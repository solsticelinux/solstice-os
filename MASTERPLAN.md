# solstice os masterplan

this is the technical stuff. the choices i made and why, the defaults, the architecture. basically everything that makes solstice, well, solstice.

## the big technical decisions

here's what i locked in:

- **libc:** glibc (because nvidia drivers, and honestly broader compatibility in general)
- **init:** systemd (it's modern, it's standard, everyone uses it)
- **display:** x11 by default (wayland's coming but not ready yet)
- **shell:** bash (it's what people know)
- **architecture:** x86-64 only for now (someone else can do arm later as an overlay)
- **package manager:** bash-based for Phase 1, rewrite in Go for Phase 2

yeah, i could write the package manager in python or rust or whatever, but honestly? bash is simpler, lighter, and i understand every line of it. Phase 1 is about getting bootstrap working. Phase 2, when it gets complex, we'll switch to Go for better structure and fewer dependencies.

## how the package manager actually works

i'm calling it `solpm`. pretty straightforward:

```bash
solpm install <package>              # get a package
solpm search <query>                 # find stuff
solpm remove <package>               # remove it
solpm upgrade                        # update everything
solpm add-overlay <url>              # add a new overlay repo
solpm list-overlays                  # see what repos you've got
```

if two overlays have the same package, you get to pick which version you want. simple as that.

**per-package options:** each recipe has its own options (menuconfig, no_modules, no_headers, etc). when you install a package, you pick which options you want OR just use the defaults. this is way simpler than gentoo's global USE flag system — no need to understand a global config, each package is self-contained.

## how many packages am i actually maintaining?

- **50 essential** — the bootstrap stuff (kernel, libc, gcc, make, bash, coreutils)
- **100 expanded** — desktop basics so you can actually use the thing (x11, systemd, utilities)
- **200+ total** — by 1.0 release
- **everything else** — lives in overlays that the community makes

i'm not trying to be gentoo with thousands of packages. that's exhausting. overlays handle the rest.

## the folder structure

```
solstice-os/
├── recipes/              # the core recipes
│   ├── gcc/
│   ├── glibc/
│   ├── firefox/
│   └── ...
├── scripts/              # automation stuff for building
├── docs/                 # documentation
├── solpm                 # the package manager itself
└── README.md
```

pretty obvious.

## the order you gotta build stuff

this is important because of dependencies:

1. kernel
2. glibc
3. binutils
4. gcc (stage 1, the bootstrap version)
5. make, bash, coreutils
6. everything else

the whole circular dependency thing with gcc is solved by using your host compiler first. linux from scratch has a whole section on this, super helpful.

## stuff that's gonna be hard and how i'm gonna handle it

- **gcc needs gcc to compile** → use the host compiler to build a bootstrap gcc first. then use that to build the real one. lfs taught me this.
- **dependency resolution** → just a topological sort of the package graph. not fancy but it works.
- **testing everything** → community helps. i can't test on every possible system, so crowdsourcing is key.
- **maintenance is a lot** → overlays distribute that. core is my job, everything else is community.

## how i know this is working

- alpha ships september 2026 (6 months from june start)
- 10+ community overlays by end of year
- 100+ people actually using it by year 2
- i'm only maintaining like 20% of total packages (rest is community)

if that happens, we're golden.

## shoutouts
- **NEOAPPS** — early collaborator, distro developer, helped with solpm architecture decisions
- **linux from scratch** — the bootstrap knowledge came straight from there, super valuable

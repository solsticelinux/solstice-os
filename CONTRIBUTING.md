# contributing to solstice os

so you want to help build solstice? cool. here's how.

## making an overlay (the main way people contribute)

the whole point of solstice is that overlays are decentralized. you make one, you share it, people use it. no gatekeeping, no approval process.

### what an overlay looks like

create a github repo. that's it. structure it like this:

```
your-overlay/
├── recipes/
│   ├── package1.sh
│   ├── package2.sh
│   └── ...
├── README.md
└── metadata.yml (optional)
```

pretty straightforward.

### test it locally

before you share it, test it:

```bash
solpm add-overlay /path/to/your-overlay
solpm install package1
```

does it work? cool, ship it.

### share it with the world

push to github and share the url:

```bash
solpm add-overlay https://github.com/yourname/your-overlay
```

people can now use your overlay. that's it. you're done.

## annual awards

every year we do this thing where the community votes on the best overlays. winners get:
- featured on solstice-os.org
- mentioned in the release notes
- community recognition

we're not gatekeeping winners or anything. just celebrating people who made cool stuff. and yeah, you still manually add them, we're not forcing anything.

## contributing to core recipes

want to improve the core distro itself? yeah, we take pull requests.

- find a bug? file an issue.
- got a fix? send a pr.
- improved documentation? we'll merge it.
- you'll get credited.

## just be cool about it

- be nice to people
- don't be a gatekeeper
- credit people who help you
- help newer people learn
- it's open source, we're all here because we like this stuff

that's it. build cool overlays, contribute when you feel like it, hang out in the community. we're all learning together.

## shoutouts
- **NEOAPPS** — early collaborator, distro developer, helping with package manager architecture
- **linux from scratch** — the inspiration for how we approach bootstrapping

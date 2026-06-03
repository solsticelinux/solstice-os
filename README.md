<img width="512" height="512" alt="2026_06_03_0rc_Kleki" src="https://github.com/user-attachments/assets/1ff60b40-d535-4ba9-80e1-9ba69eafd603" />


# solstice os

solstice is a source-based linux distro for people who actually want to understand what's running on their machine.

## why make another distro?

gentoo is cool but it's overwhelming. you've got 50+ USE flags per package that just pile up and confuse you. then you've got arch and fedora which are binary-first, meaning you don't really get the performance benefits of compiling for *your* specific hardware. but here's the thing — source-based doesn't have to be a nightmare. solstice takes the good parts (control, performance, understanding your system) and cuts out all the complexity.

## what even is solstice?

it's a source-based distro that's actually modern. we're talking systemd, x11 by default (wayland coming soon), no ancient legacy garbage. you compile from source, you optimize for your cpu, you know what's on your machine. but unlike gentoo where you pick every single knob, we're like "hey, we chose good defaults, just use those unless you want to change something."

and honestly? community is a huge part of this. we don't want overlays (extra package repos) to be some afterthought. they're first-class citizens. someone wants gaming packages? cool, there's an overlay. someone wants ml tools? there's probably an overlay. you just add it and go.

oh, and we care about performance. modern cpus, modern kernels, optimized builds. none of that old stuff weighing you down.

## who's this for?

- you trying to understand how linux actually works? perfect.
- performance nerd who wants to squeeze every bit out of their hardware? we got you.
- developer who needs full control over their system? yeah, this is your jam.
- community person who wants to create overlays and contribute? dude, you're gonna be a pioneer here.
- someone who just wants things to work without thinking about it? honestly, just use ubuntu, no shame.

## our philosophy

- we picked good defaults, but you can override them
- you compile once, it runs forever
- community handles the extras, not us
- transparency over gatekeeping

## where we're at

solstice is in development. we're starting for real in june 2026, aiming for an alpha in september. we're learning as we build this thing. if you want to jump in and learn alongside us, we're absolutely down for that.

**current status (april 2026):**
- 4.9K+ Reddit views on r/linuxfromscratch
- active Discord community with early collaborators
- technical architecture finalized
- community growing organically

## let's go

want to build solstice?

- get debian or whatever on your machine (you'll need build tools)
- check out the [ROADMAP.md](ROADMAP.md)
- ~~peek at the source on github~~ theres no source yet.
- hang out in our discord: https://discord.gg/56DYRUnzP5

## props

big thanks to:
- **NEOAPPS** — early collaborator, distro developer, architecture advisor
- **linux from scratch** — that book is insane, literally teaches you how to build a distro from nothing

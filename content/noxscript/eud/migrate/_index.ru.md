+++
title = "Миграция с EUD"
weight = 2
+++

This guide will help migrate existing [Panic's EUD](https://gitlab.com/happysoft3/eud-maps-project)
maps to [NS3]({{% relref "noxscript/ns3" %}}) and
[EUD](https://pkg.go.dev/github.com/noxworld-dev/noxscript/eud/v171) layer in OpenNox.

First, it's important to understand that "memhacks" and direct memory access is **technically not possible** in OpenNox.

Here are a few reasons why:
- Memhacks target a specific binary. This means it only works on _one_ Nox version.
  OpenNox constantly evolves, thus we cannot guarantee any specific memory layout.
- Memhacks usually inject assembly code that targets a specific CPU architecture (Intel/AMD x86).
  OpenNox can be potentially compiled for ARM (e.g. MacBooks, Android, RPi), thus script will stop working there.

We attempted to resolve these issues with EUD developer **Panic**, but we don't see any willingness for collaboration
from his side. If you really want EUD to be supported directly in OpenNox, please **reach out to Panic**.
Resolving these technical challenges is possible, but requires tight collaboration, and will to do so from him, first and foremost.

## Why?

First logical question: *why bother* with converting to OpenNox? EUD works great in original Nox.

A few reasons to migrate to OpenNox scripts:
- OpenNox is **evolving** and supports new features that are impossible in vanilla (e.g. HD, better multiplayer, modding, etc).
- EUD library in OpenNox is a **drop-in replacement**. Same functions will be supported.
- NS4 (and beyond) will have **even more features** going forward.
- You *won't* need a separate script compiler. Scripts are run **directly from source**.
- More comprehensive **type system**: proper arrays, dictionaries (`map`), structures, classes.
- A lot more **libraries** included: string manipulation, full UTF8 support, math, sorting, etc.
- Better **performance**: all libraries are compiled into OpenNox and run natively.
- Better **debugging**: if script crashes, there's a stack trace. Scripts can recover from it as well!
- Go language used in scripts is used in OpenNox itself. Maybe one day you'll decide to **contribute**?

In general, we believe that OpenNox is the future of Nox modding, thus porting your map may give it an entirely new life!

## How?

At this point, we are still working on improving the [EUD](https://pkg.go.dev/github.com/noxworld-dev/noxscript/eud/v171)
compatibility layer, so quite a few functions might still be unavailable. Please talk to us for more details.

In general the conversion process is very similar to the one for [converting NS3 source manually]({{% relref "noxscript/ns3/migrate" %}}#converting-the-source).
Same changes must be done to the source to align the syntax. We are working on a more automated process.

You need to be aware that all functions using `GetMemory` and `SetMemory` must be **rewritten** in any case.
The first thing to do is to check if functions you are using are already available in Panic's [EUD library](https://gitlab.com/happysoft3/eud-maps-project/-/tree/master/eud_project/libs).
If so, updating your EUD script to using these function will help you convert to our [EUD](https://pkg.go.dev/github.com/noxworld-dev/noxscript/eud/v171)
library later as well.

We aim to provide a good migration path for well-known EUD libraries, so if you copied code from another EUD project,
there's a high chance we support it in one of the libraries.

Still, if you cannot find anything similar, talk to us. We will help convert your code and include necessary functionality
into next OpenNox release.

## After conversion

The [NS3]({{% relref "noxscript/ns3/migrate" %}}#after-conversion) guide applies here as well, so make sure to check it out!
---
title: "NoxScript 3"
weight: 11
---

## Reference

Here you can find a full list of functions provided by [NS3](https://pkg.go.dev/github.com/noxworld-dev/noxscript/ns/v3) runtime.

## History

Vanilla Nox has its own script runtime based on compiled source files. Since original Nox editor was never released,
community recreated the script compiler from scratch.

Since there's no official version, the scripts had different dialects, one of the latest is known as [NoxScript 3](https://noxtools.github.io/noxscript/).

There's also a [Panic's EUD]({{% relref "noxscript/eud" %}}) compiler that uses memory manipulation to extend script functionality.

OpenNox supports vanilla scripts with no changes required. Additionally, it implements a more **advanced script runtime**.

## New runtime

To make the transition to the new script runtime smoother, OpenNox provides a **compatibility layer** for NoxScript 3.

The idea is that all the functions from [NoxScript 3](https://noxtools.github.io/noxscript/) should work exactly the same,
accept same arguments, etc. This way all existing functions can be copied with almost no changes (only syntax will vary).

To avoid confusion, we usually refer to vanilla scripts as "NoxScript 3", while the new compatibility layer is called **NS3**.

If you have existing scripts you want to migrate, see our [migration guide]({{% relref "noxscript/ns3/migrate" %}}).

Otherwise, it's better to start directly from the [NS4]({{% relref "noxscript/ns4" %}}), which is our current script version.
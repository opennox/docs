+++
title = "Panic's EUD"
weight = 20
+++

## History

Vanilla Nox has its own script runtime based on compiled source files. Since original Nox editor was never released,
community recreated the script compiler from scratch.

Since there's no official version, the scripts had different dialects, one of the latest is known as [NoxScript 3]({{% relref "noxscript/ns3" %}}).

However, the script runtime of Nox was very limited. Eventually the community found a way to inject custom code into the
game, which lead to a new kind of map scripts, usually referred as "memhacks".

[Panic's EUD](https://gitlab.com/happysoft3/eud-maps-project) is the most advanced project of this kind.
It uses memory manipulation to implement a lot of new functionality for the scripts.

Unfortunately, memory manipulation usually targets a single binary version (vanilla Nox), and thus cannot run on
other versions such as OpenNox. Because of this OpenNox does not support EUD scripts.

## New runtime

Even though OpenNox cannot support scripts that use memory manipulation, we still can provide similar functions
in out own script runtime. Thus, OpenNox provides a **compatibility layer** for EUD scripts.

The idea is that all the functions from [Panic's EUD](https://gitlab.com/happysoft3/eud-maps-project) which do not
expose the memory directly should work exactly the same, in OpenNox
This way all existing functions can be copied with almost no changes (only syntax will vary).

If you have existing scripts you want to migrate, see our [migration guide]({{% relref "noxscript/eud/migrate" %}}).

Otherwise, it's better to start directly from the [NS4]({{% relref "noxscript/ns4" %}}), which is our current script version.
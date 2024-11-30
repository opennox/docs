---
title: "Hosting a dedicated server"
menuTitle: "Dedicated server"
weight: 2
---

{{% notice warning %}}
There are quite a few bug reports about dedicated server freezing.

Thus, it is not recommend to run dedicated server at this stage.
{{% /notice %}}

OpenNox also ships with the `opennox-server` binary, which can be used to run a dedicated server.

Also, [Docker images](https://github.com/opennox/opennox-docker/pkgs/container/opennox) are available for the server.

When hosting a dedicated server, it is important to setup access by [remote console]({{% relref "opennox/host/ssh" %}})
and/or [HTTP API]({{% relref "opennox/host/api" %}}) to control the server remotely.
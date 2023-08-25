+++
title = "Hosting a dedicated server"
menuTitle = "Dedicated"
weight = 2
+++

OpenNox also ships with the `opennox-server` binary which can be used to run as a dedicated server.

Also, [Docker images](https://github.com/noxworld-dev/opennox-docker/pkgs/container/opennox) are available for the server.

When hosting a dedicated server, it's important to consider [remote console]({{% relref "opennox/host/ssh" %}})
and/or [HTTP API]({{% relref "opennox/host/api" %}}) to control the server remotely.

{{% notice warning %}}
We got quite a few bug reports about dedicated server freezing.

Thus, we do not recommend running dedicated server at this stage.
{{% /notice %}}
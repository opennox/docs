---
title: "Install on Windows"
menuTitle: "Windows"
weight: 2
---

## Installing

{{% notice warning %}}
OpenNox is not a standalone game. It requires a copy of **original Nox installed**!

See [GoG](https://www.gog.com/game/nox) or [Origin](https://www.origin.com/irl/en-us/store/nox/nox) for purchase options.
Original CD should work as well.
{{% /notice %}}

1. Install original Nox. Prefer locations outside of "Program Files".
2. Download latest [OpenNox installer](https://github.com/noxworld-dev/opennox/releases/latest). Use `.exe` file for Windows.
3. Install it to any directory (shouldn't be the same as Nox itself).

## Playing

### HD version

1. Go to OpenNox installation directory.
2. Make a shortcut for `opennox-hd.exe`.
3. Run it!

{{% notice info %}}
HD version will _not_ join public legacy servers!

This is done for fairness reasons, since not everyone runs OpenNox in HD. You can still host your own server for your friends to join.
{{% /notice %}}

### Legacy version

1. Go to OpenNox installation directory.
2. Make a shortcut for `opennox.exe`.
3. Run it!

{{% notice info %}}
Legacy version will _not_ join HD servers.

Make sure to run the same version as the server when playing online.
{{% /notice %}}

## Troubleshooting

### OpenNox doesn't start

First, try running OpenNox with Administrator permissions. 
If it works, then your Nox copy is likely installed in the protected folder like "Program Files" which causes issues. 
Delete OpenNox folder, reinstall Nox to some other folder and install OpenNox again.

If it doesn't help, open `opennox.yml` in OpenNox installation directory in a text editor ([Notepad++](https://notepad-plus-plus.org/) is a good option).
Find section similar to this:

```yaml
game:
  data: C:\Games\Nox
```

Change the path manually to a folder where your copy of Nox is installed. Restart OpenNox.

If it still doesn't work, please ping us on [OpenNox Discord](https://discord.gg/HgDUeXhAyW) in `#feedback` channel.
It will help if you share `opennox.log` located in `log` folder in OpenNox install directory.

### Can't connect to a server: Version mismatch

As was explained in the installation section, HD and legacy versions won't join servers of the opposite version. 

Most online servers still run legacy version, so if you want to join them, you must run legacy version of OpenNox as well. 
Make sure to try a correct version when joining a server.
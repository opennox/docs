+++
title = "Install on Steam Deck"
menuTitle = "Steam Deck"
weight = 3
+++


{{% notice note %}}
This guide is based on Linux installation guide.

Specific Steam Deck guide will be provided in the future as well.
{{% /notice %}}

## Installing

{{% notice warning %}}
OpenNox is not a standalone game. It requires a copy of **original Nox installed**!

See [GoG](https://www.gog.com/game/nox) for purchase options.
{{% /notice %}}

1. Install original Nox from [GoG](https://www.gog.com/game/nox) (via [Lutris](https://lutris.net/games/nox/) or [Heroic](https://heroicgameslauncher.com/)).
2. Install OpenNox via [Flatpak](https://flathub.org/apps/details/io.github.noxworld_dev.OpenNox).

## Playing

### HD version

Installation should create a "OpenNox HD" shortcut in the start menu. Alternatively: run `opennox-hd` binary from terminal.

{{% notice info %}}
HD version will _not_ join public legacy servers!

This is done for fairness reasons, since not everyone runs OpenNox in HD. You can still host your own server for your friends to join.
{{% /notice %}}

### Legacy version

Installation should create a "OpenNox" shortcut in the start menu. Alternatively: run `opennox` binary from terminal.

{{% notice info %}}
Legacy version will _not_ join HD servers.

Make sure to run the same version as the server when playing online.
{{% /notice %}}

## Troubleshooting

### OpenNox doesn't start

Try starting `opennox` from the terminal. Check if there are any error messages there.

If it doesn't help, open `opennox.yml` in OpenNox installation directory in a text editor. Find section similar to this:

```yaml
game:
  data: /home/user/some/path/to/Nox
```

Change the path manually to a folder where your copy of Nox is installed. Restart OpenNox.

If it still doesn't work, please ping us on [OpenNox Discord](https://discord.gg/HgDUeXhAyW) in `#feedback` channel.
It will help if you share `opennox.log` located in `log` folder in OpenNox install directory.

### Can't connect to a server: Version mismatch

As was explained in the installation section, HD and legacy versions won't join servers of the opposite version.

Most online servers still run legacy version, so if you want to join them, you must run legacy version of OpenNox as well.
Make sure to try a correct version when joining a server.
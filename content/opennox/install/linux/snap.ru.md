+++
title = "Snap release"
menuTitle = "Snap"
weight = 1
+++

## Package information

Snap is a packaging format designed to simplify user interaction with software by removing the need to install its dependencies.

Snap package is provided since v1.8.6 (19 Dec 2021).

Snap package supplies all 3 executables: non-hd client, hd client and dedicated server.

## Prerequisites

{{% notice warning %}}
OpenNox is not a full game. It requires game content files of the original Nox installation!

See [GoG](https://www.gog.com/game/nox) for purchase options.
Original CD should work as well.
{{% /notice %}}

You will need [snapd](https://snapcraft.io/docs/installing-snapd) installed.

## Installation process
 
1. Follow installation instructions on [Snapcraft](https://snapcraft.io/opennox)
2. Copy Nox content files into your `$HOME/Nox` folder. Alternatively, you can install Nox into this folder.

## Running the game

After installing you should get two launchers in your applications menu: OpenNox and OpenNox HD. Run the one you need.

### Running from terminal
To run OpenNox Non-HD (legacy), issue this command:
```shell
snap run opennox
```

To run OpenNox HD, issue this command:
```shell
snap run opennox.hd
```

To run OpenNox dedicated server, issue this command:
```shell
snap run opennox.server
```

## Troubleshooting

### OpenNox doesn't start
- Try starting OpenNox from the terminal. Check if there are any error messages there.
- Make sure you have Nox game files in `$HOME/Nox` or in the place specified in `$HOME/opennox.yml`:
```yaml
game:
  data: /home/user/some/path/to/Nox
```

Change this path manually to a folder where your copy of Nox is installed, if necessary. Restart OpenNox.

If nothing helps, please contact us on [OpenNox Discord](https://discord.gg/HgDUeXhAyW) in `#feedback` channel and share the `opennox.log` located in the `$HOME/snap/opennox/common/logs` folder.

### Can't connect to a server: Version mismatch

HD and legacy versions won't join servers of the opposite version.

Most online servers still run legacy version, so if you want to join them, you must run legacy version of OpenNox as well.

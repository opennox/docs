+++
title = "Flatpak release"
menuTitle = "Flatpak"
weight = 1
+++

## Package information

Flatpak is a packaging format designed to simplify user interaction with software by removing the need to install its dependencies.

Flatpak package is provided since v1.8.12-dev (0a8352c) (13 Jan 2023).

Flatpak package supplies only 2 executables: non-hd client and hd client.

## Prerequisites

{{% notice warning %}}
OpenNox is not a full game. It requires game content files of the original Nox installation!

See [GoG](https://www.gog.com/game/nox) for purchase options.
Original CD should work as well.
{{% /notice %}}

You will need [Flatpak](https://flathub.org/setup) installed.

## Installation process
 
1. Follow installation instructions on [Flathub](https://flathub.org/apps/details/io.github.noxworld_dev.OpenNox)
2. Copy Nox content files into your `$HOME/Nox` folder. Alternatively, you can install Nox into this folder.

## Running the game

After installing you should get two launchers in your applications menu: OpenNox and OpenNox HD. Run the one you need.

### Running from terminal
To run OpenNox Non-HD (legacy) issue this command:
```shell
flatpak run io.github.noxworld_dev.OpenNox
```

To run OpenNox HD issue this command:
```shell
flatpak run --command=opennox-hd io.github.noxworld_dev.OpenNox
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

If nothing helps, please contact us on [OpenNox Discord](https://discord.gg/HgDUeXhAyW) in `#feedback` channel and share the `opennox.log` located in the `logs` folder, which is located either in your home folder or in OpenNox working directory.

### Can't connect to a server: Version mismatch

HD and legacy versions won't join servers of the opposite version.

Most online servers still run legacy version, so if you want to join them, you must run legacy version of OpenNox as well.

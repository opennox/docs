+++
title = "Binary archive release"
menuTitle = "Binary archive"
weight = 1
+++

## Release information

This release is just OpenNox binaries packed into tar.gz archive.

## Prerequisites

{{% notice warning %}}
OpenNox is not a full game. It requires game content files of the original Nox installation!

See [GoG](https://www.gog.com/game/nox) for purchase options.
Original CD should work as well.
{{% /notice %}}

To run OpenNox you will need to install this dependencies:
- libc6:i386
- libopenal1:i386
- libsdl2-2.0-0:i386

Make sure you have 32 bit version of your graphics drivers installed to provide libgl1:i386.

## Installation process (portable)

1. Download the tag.gz file from the [Opennox releases](https://github.com/noxworld-dev/opennox/releases) page.
2. Unpack tar.gz archive contents into Nox installation folder.
3. Mark files `opennox`, `opennox-hd` and `opennox-server` as executable.

## Installation process (non-portable)

1. Download the tag.gz file from the [Opennox releases](https://github.com/noxworld-dev/opennox/releases) page.
2. Unpack tar.gz archive contents into folder of your choice.
3. Mark files `opennox`, `opennox-hd` and `opennox-server` as executable.
4. Copy Nox content files into your `$HOME/Nox` folder. Alternatively, you can install Nox into this folder.

## Running the game

You need to create launchers yourself for executables you want to run.

Please note, that working directory must be set to the Nox installation folder.

### Running from terminal

{{% notice info %}}
Navigate to the Nox installation folder, before running any of these commands.
{{% /notice %}}
To run OpenNox Non-HD (legacy), issue this command:
```shell
opennox
```

To run OpenNox HD, issue this command:
```shell
opennox-hd
```

To run OpenNox dedicated server, issue this command:
```shell
opennox-server
```
{{% notice info %}}
If you placed binaries not Nox installation folder, you have to provide a full or relative path to the binary.
{{% /notice %}}

## Troubleshooting

### OpenNox doesn't start
- Try starting OpenNox from the terminal. Check if there are any error messages there.
- Make sure you have put binaries into your Nox installation folder or have game files in the `$HOME/Nox` directory or in the place specified in `opennox.yml` (which can be either in `$HOME/.config/opennox` or in the working directory used to call binaries from):
```yaml
game:
  data: /home/user/some/path/to/Nox
```

Change this path manually to a folder where your copy of Nox is installed, if necessary. Restart OpenNox.

If nothing helps, please contact us on [OpenNox Discord](https://discord.gg/HgDUeXhAyW) in `#feedback` channel and share the `opennox.log` located in the `$HOME/snap/opennox/common/logs` folder.

### Can't connect to a server: Version mismatch

HD and legacy versions won't join servers of the opposite version.

Most online servers still run legacy version, so if you want to join them, you must run legacy version of OpenNox as well.

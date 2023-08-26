+++
title = "Appimage release"
menuTitle = "Appimage"
weight = 1
+++

## Package information

{{% notice warning %}}
Appimage does not work on Ubuntu distribution since version 22, since it no longer ships *libfuse2*.
{{% /notice %}}

Appimage is a portable packaging format designed to simplify user interaction with software by removing the need to install it as a package or install its dependencies.

32 bit Appimage packages are provided since v1.8.12-alpha9 (25 Aug 2023).

## Difference list between Appimage release and binary release
- The Appimage contains all 3 executables: non-hd client, hd client and dedicated server.
- The Appimage release is **not portable by default** -- it overrides config location and data location to use user's home folder conforming to Freedesktop standard *"XDG Base Directory Specification v0.8"*. This is done specifically to allow making packages out of this AppImage and to allow direct system installation (in `/usr/local/bin` for example).

### Paths used by the Appimage release
Please note, that $HOME is either user's home or a portable home, depending on how you install OpenNox.
- **Game files** are expected to be in this directory: `$HOME/.local/share/opennox`
- **Game configuration** files are expected to be in this directory: `$HOME/.config/opennox`
- **Game logs** will be put into this directory: `$HOME/.local/state/opennox`

## Prerequisites

{{% notice warning %}}
OpenNox is not a full game. It requires game content files of the original Nox installation!

See [GoG](https://www.gog.com/game/nox) for purchase options.
Original CD should work as well.
{{% /notice %}}

Most probably, your Linux distribution has all required packages installed already.
In case if Appimage does not run, please ensure you have these packages installed:
- libc:i386
- libfuse2:i386
- zlib1g:i386

## Installation process (standard usage)
 
1. Download the Appimage file from the [Opennox releases](https://github.com/noxworld-dev/opennox/releases) page. Put it anywhere you think is appropriate and *mark it as executable*.
2. Put Nox content into `$HOME/.local/share/opennox` folder.
3. *Optional* If you are migrating from binary release, please put opennox.yml into `$HOME/.config/opennox` folder.

## Installation process (portable)

1. Download the Appimage file from the [Opennox releases](https://github.com/noxworld-dev/opennox/releases) page. Put it anywhere you think is appropriate and *mark it as executable*.
2. Create portable home folder for the Appimage by running it with parameter **--appimage-portable-home** or by creating a folder with the same name as the Appimage and ".home" appended to the end. If Appimage file is "opennox-bundle-i386.AppImage", then portable home folder must be named "opennox-bundle-i386.AppImage.home".
3. Put Nox content into `/.local/share/opennox` folder *inside the portable home folder* you had created in step 2.
4. *Optional* If you are migrating from binary release, please put opennox.yml into `/.config/opennox` folder *inside the portable home folder* you had created in step 2.


## Running the Appimage

Appimage release always checks the first parameter to decide which executable to run.
- To run OpenNox (legacy version), simply run the Appimage file.
- To run OpenNox HD, run the Appimage file with **"hd"** parameter as the first parameter.
- To run OpenNox dedicated server, run the Appimage file with **"server"** parameter as the first parameter.
- To get help about this Appimage release, run the Appimage file with **"help"** parameter as the first parameter. The help explains how to use Appimage and where files should be placed.

## Troubleshooting

### OpenNox doesn't start

Please ping us on [OpenNox Discord](https://discord.gg/HgDUeXhAyW) in `#feedback` channel and share the `opennox.log` located in `.local/state/opennox` folder in OpenNox install directory.

### Can't connect to a server: Version mismatch

HD and legacy versions won't join servers of the opposite version.

Most online servers still run legacy version, so if you want to join them, you must run legacy version of OpenNox as well.
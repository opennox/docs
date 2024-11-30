---
title: "Features"
weight: 2
---

## Vanilla features

All vanilla features are supported. You should be able to complete the campaign and play online with OpenNox.

If something doesn't work, please [file an issue](https://github.com/opennox/opennox/issues/new/choose).

## Compatibility

OpenNox will work out-of-the-box on any recent [Windows]({{% relref "opennox/install/windows" %}}) version. This includes proper graphics and online multiplayer.

OpenNox also works natively on [Linux]({{% relref "opennox/install/linux" %}}), including [Steam Deck]({{% relref "opennox/install/deck" %}}).

OpenNox doesn't provide Nox assets. You must own a copy of the original game and have it installed in order to run it.
OpenNox will attempt to find Nox installation automatically.

OpenNox is able to connect to vanilla Nox servers, as well as vanilla Nox clients are able to connect to OpenNox servers.
This is only true for regular version of OpenNox. OpenNox HD will refuse to connect with non-HD (legacy) players.

## Graphics

OpenNox can load vanilla Nox content and should work on any recent Windows and Linux versions with no graphical issues.

Additionally, OpenNox provides an HD version, which allows using display resolutions up to 4K.
OpenNox HD will refuse connections from non-HD/legacy version and from vanilla Nox, because fairness considerations.

OpenNox supports custom TTF and OTF fonts to replace vanilla raster fonts.

## Multiplayer

Vanilla Nox distinguishes between online and LAN multiplayer. It uses XWIS server and requires login/password for it.

OpenNox combines both online and LAN games into a single list. It doesn't require XWIS password, while still able to join XWIS servers.

OpenNox also attempts to automatically forward ports, when hosting a game online.
This requires UPnP to be enabled on your router (which is enabled by default in most cases).

There is an initial work done for supporting playing [solo campaign in multiplayer]({{% relref "opennox/dev/console" %}}#load).

## Server

OpenNox provides a headless dedicated server both for Linux and Windows.

OpenNox servers expose a simple [HTTP API]({{% relref "opennox/host/api" %}}) for getting server information,
which allows easy integration with websites, Discord bots, etc. The same API provides a simple Web control panel for the server.

## Game

OpenNox improves a few aspects of the game to make it more convenient to players, or to provide more options.

Apart from a simpler [online games list](#multiplayer), automatic port-forwarding and more [graphical options](#graphics),
OpenNox additionally provides:

- More control over [Nox Quest]({{% relref "opennox/play/quest" %}}).
- [Manual spell casting]({{% relref "opennox/play/manual-cast" %}}) similar to [Magicka](https://en.wikipedia.org/wiki/Magicka).

## Modding

OpenNox aims to greatly improve modding support. It is still a work-in-progress, but there are a few improvements already implemented:

- New [console commands]({{% relref "opennox/dev/console" %}}).
- Support for safe [NoxScript]({{% relref "opennox/mod/scripts/ns" %}}) runtime.
- Easier way to change [game balance]({{% relref "opennox/mod/balance" %}}) values.
- Support for [changing or replacing spells]({{% relref "opennox/mod/spells" %}}).
- Initial support for [loading custom sprites]({{% relref "opennox/mod/sprites" %}}).
- Support for [custom translations]({{% relref "opennox/mod/translation" %}}).

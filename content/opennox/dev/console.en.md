---
title: "OpenNox console"
menuTitle: "Console"
weight: 10
---

## Enabling all commands

Just like in vanilla Nox, OpenNox starts with most console commands disabled. This is done to prevent cheating in the solo campaign.
Most commands will not work in multiplayer, unless you are a server admin/host.

To enable all commands, open the console (`F1` by default) and type:

```
racoiaws
```

## Remote server administration

OpenNox does not support original RCON protocol based on telnet.

Instead, it implements remote console via built-in SSH server.

## List commands

To get a list of all available commands, use `help`.

Here's the list of the most interesting ones.

### image

Take a screenshot and save it as a PNG image.

```
image
```

### show

This command displays various information, including debug information.

Available sub-commands:
- `show bindings` - lists all console bindings (macros).
- `show extents` - toggle displaying of names and sizes for all objects on the screen.
- `show ai` - toggle displaying of AI paths and prints all AI decisions to console.
- `show gui` - toggle graphical user interface.

### list

This command lists various in-game spells, items, monsters, maps and players.

These commands prints item IDs that can be the used with [spawn](#cheat-spawn) command.

Available sub-commands:
- `list staffs` - lists all staves and wands.
- `list armor` - lists all armor.
- `list weapons` - lists all weapons.
- `list food` - lists all consumables.
- `list monsters` - lists all monsters and NPCs.
- `list spells` - lists all spells.
- `list maps` - lists all maps.
- `list users` - lists all players.

### load

This command switches current game map to the one specified:

```
load wiz01a
```

In vanilla Nox, not every map can be loaded like that. For example, it's impossible to load campaign maps in multiplayer.
OpenNox allows bypassing those restrictions by using [`set maps allow.all`](#set-maps) command.

### set god

A vanilla cheat for invulnerability, all spells and infinite mana.

```
set god
```

To disable:

```
unset god
```

Note that using this cheat will cause the character to learn all spells up to the maximal level.
This cannot be reversed, even if the cheat is disabled.
See [cheat god](#cheat-god) if you only need invulnerability and infinite mana.

### set quest

These command allow more controls for Nox Quest game mode. See [this page]({{% relref "opennox/play/quest" %}}) for details.

### set maps

These commands allow more control for game map loading.

- `set maps allow.all` - disable game mode checks when loading the map; allows loading campaign in multiplayer, etc

### cheat god

A cheat for invulnerability and infinite mana.

```
cheat god
```

To disable:

```
cheat god 0
```

For additionally getting all spells see [cheat sage](#cheat-sage), or [set god](#set-god).

### cheat sage

A cheat for getting all class spells, scrolls and/or abilities.

```
cheat sage
```

To disable:

```
cheat sage 0
```

### cheat spells

A cheat for getting all spells.

For getting class spells:

```
cheat spells
```

For getting class spells with a specific spell level:

```
cheat spells 3
```

To get all spells, even hidden ones:

```
cheat spells all
```

### cheat scrolls

A cheat for getting all beast scrolls.

```
cheat scrolls
```

To disable:

```
cheat scrolls 0
```

### cheat goto

Teleport to given coordinates or a waypoint.

For teleporting to coordinates (X, Y):

```
cheat goto 1000 2000
```

For teleporting to a waypoint:

```
cheat goto MyWaypoint
```

### cheat spawn

Spawn a given item or monster at the player's position.

Command accepts IDs returned by the [list](#list) command.

```
cheat spawn OblivionOrb
cheat spawn Mimic
```

It is also possible to specify a number of items to spawn:

```
cheat spawn RedApple 5
```

### cheat gold

Adds specified amount of gold to all players.

```
cheat gold 10000
```

### cheat health

Sets or restores health for the character.

Without arguments, command will restore health to maximum:

```
cheat health
```

You can also specify the desired health value:

```
cheat health 999
```

### cheat mana

Sets or restores mana for the character.

Without arguments, command will restore mana to maximum:

```
cheat mana
```

You can also specify desired mana value:

```
cheat mana 999
```

### cheat equip.all

Removes equipment requirements from all items. In other words, any class can equip and use any armor/weapons.

```
cheat equip.all
```

To disable it:

```
cheat equip.all 0
```

### cheat charm.all

Allows charming any hostile creatures and NPCs (including scripted ones, humanoids, etc).

```
cheat charm.all
```

To disable it:

```
cheat charm.all 0
```

### cheat summon.nolimit

{{% notice warning %}}
The game may become unstable and crash, when using this command!
{{% /notice %}}

Remove the limit for the number of summoned creatures.

```
cheat summon.nolimit
```

To disable it:

```
cheat summon.nolimit 0
```

### lua

This commands executes given Lua code.

For example, to replicate `cheat spawn RedApple` with Lua:

```lua
apple = Nox.ObjectType("RedApple")
p = Nox.Players.host
apple:Create(p)
```

In the console, each line must start with `lua` command:

```lua
lua apple = Nox.ObjectType("RedApple")
lua p = Nox.Players.host
lua apple:Create(p)
```

Notice that variables defined in one `lua` commands can be used in other ones.

It's also possible to write a multi-line command in a single line:

```lua
apple = Nox.ObjectType("RedApple"); p = Nox.Players.host; apple:Create(p)
```

or

```lua
Nox.ObjectType("RedApple"):Create(Nox.Players.host)
```

For more information about Lua scripting, see [this page]({{% relref "opennox/mod/scripts/lua" %}}).


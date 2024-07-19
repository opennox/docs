---
title: "Multiplayer campaign"
weight: 6
---

{{% notice warning %}}
This mode is highly experimental! You will encounter bugs.

You must **restart the game** after playing in this mode. Otherwise, game session and the menu will likely be broken.  
{{% /notice %}}

### Starting campaign in multiplayer

1. Host regular Quest game.
2. Wait for all players to join.
3. Open game console with F1 and type `racoiaws` (enables [console commands]({{% relref "opennox/dev/console" %}})).
4. Disable map restrictions: `set maps allow.all`.
5. Load desired campaign: `load wiz01a` (for Wizard), `load con01a` (for Conjurer), `load war01a` (for Warrior).
6. Enjoy!

### Known issues

- Game saves won't work. All your progress for this session will be lost. Use `load` to jump to other chapters.
- Players likely won't be able to reconnect. Full game restart is required (for both client and server!).
- Other players can run around during cutscenes. If you break them - you'll have to restart the map.
- Death of any player will trigger the death screen and stop the campaign.  

### Useful commands

- Teleport P2 to P1: `tp` (or `tp 0`).
- Teleport P1 to P2: `tpto` (or `tpto 0`).
- Unfreeze P1 after broken cutscene: `unstuck`.
   
Use [SSH remote console]({{% relref "opennox/host/ssh" %}}) to copy-paste commands.
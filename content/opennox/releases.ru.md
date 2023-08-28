+++
disableToc = false
title = "Что нового"
weight = 1
+++

This page shows what's new in the latest OpenNox release.

{{% badge style="warning" icon="bug" title=" " %}}Bug{{% /badge %}} A well-known issue affecting specific version.

{{% badge style="warning" title=" " %}}Breaking{{% /badge %}} A change that requires action by you after upgrading.

{{% badge style="note" title=" " %}}Change{{% /badge %}} A change in default behavior that may requires action by you if you want to revert it.

{{% badge style="note" icon="wrench" title=" " %}}Experiment{{% /badge %}} An experimental change that may be removed or changed completely in the future.

{{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Marks new behavior you might find interesting or comes configurable.

{{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} A fix of a bug or regression.

<!--GH-ACTION-RELEASE-MILESTONE-->

---

## 1.8.11 (2022-06-29)

**Known issues**

- {{% badge style="warning" icon="bug" title=" " %}}Bug{{% /badge %}} Game may crash or break save file in solo when encountering invisible NPCs.
- {{% badge style="warning" icon="bug" title=" " %}}Bug{{% /badge %}} Multiplayer is unstable. Client may fail to connect to servers.

**New**

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Preparations to make more spells moddable.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Hidden Death spell now correctly draws spinning skull on monsters.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow using two more effects from scripts: `ENERGY_BOLT` and `PLASMA`.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Lots of internal changes related to color handling.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow force-switching maps in more cases.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Stretch image option is now persisted.

**Fixes**

- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Potential crash when loading certain maps.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Downloading maps via Nox protocol.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Incorrect rendering of the observer effect.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Rendering of abilities panel when player dies.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Obliteration spell effect.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Minimap rendering.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Parsing of network filters from the config.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Transparent color not rendering correctly in some GUI elements.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Correctly override background color in GUI.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Crash when reading gamma on the server.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Server requiring audio/video libs.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Text message when switching maps.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} `GREEN_BOLT` effect when called from a script.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Build now doesn't require Git.

---

## 1.8.10 (2022-05-30)

- {{% badge style="note" title=" " %}}Change{{% /badge %}} First release as an open source project!
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Significant cleanup of the codebase.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Fix long-standing bug for rendering lights in high-res.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Long-awaited support for movie playback.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Reworked most of the rendering code.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow console commands in Quest.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Use shaders for gamma control. Should work more reliably.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Send server resolution and player list to the lobby.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow overriding and initial modding support for spells.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow getting all spells, including hidden ones via `cheat spells all`.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow removing summon limit via `cheat summon.nolimit`.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Support XDG paths on Linux.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Correctly handle `goto` console command.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Minor physics deviation compared to vanilla.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Teams creation in Quest.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Reading gamma settings from config.
- {{% badge style="note" icon="wrench" title=" " %}}Experiment{{% /badge %}} Support for loading campaign in multiplayer.

---

## 1.8.9 (2022-03-04)

- {{% badge style="note" title=" " %}}Change{{% /badge %}} OpenNox will now use the new lobby server and fallback to XWIS if no servers were found.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Ping will now be shown in servers list for servers that support it.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Server discovery was optimized and is now faster.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Implemented a tiny builtin SSH remote console. Telnet support removed.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Game load/save was optimized and works faster now.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Not being able to connect to non-OpenNox servers.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Spawned creatures being stuck when damaged.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Magic missiles targeting dead entities.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Energy bolt not working properly in traps.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} UI no longer freezes when discovering game servers.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Player names not being shown in scores table.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Sorting in the character list.

---

## 1.8.8 (2022-01-31)

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Notify if OpenNox update is available.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Server: add metrics for monitoring.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Jumping no longer prevents from taking damage from lava.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Do not announce Solo Quest games online.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Team colors (regression from v1.8.7).
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Correctly set config dir for Snap.

---

## 1.8.7 (2022-01-21)

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Support loading of TrueType and OpenType fonts.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Automatically fix Russian translation and font files.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} A ton of internal changes and cleanup.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Creatures and NPCs with ranging attack trying to fight melee only.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Server API being stuck than there are no players on the server.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Crash when falling into a pit.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} AI debug logging.

---

## 1.8.6 (2021-12-18)

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Release OpenNox for Linux on [Snapcraft](https://snapcraft.io/opennox).
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Reading game files is now safer and more extendable.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Preparations for saving and replaying Nox matches.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Preparations for rendering TTF fonts in game engine.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} E2E mode now allows recording player input directly (to reproduce bugs).
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Safer and faster sprite rendering.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Initial work on rendering map previews.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} A lot of internal refactorings and improvements.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow configuring manual spell cast timeout.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow binding any keys with `bind` command.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} `cheat spawn` command to spawn items and monsters.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Safer GUI code, preventing a major memory corruption.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Races in the audio playback.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Potential fix for native map downloads.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Crashes when playing on broken maps.

---

## 1.8.5 (2021-10-31)

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Add more resolution options for both regular and HD version.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Move screen resolution to `opennox.yml` config.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Instant victory if player commits a suicide in Arena.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Properly propagate closed and private game flags to XWIS.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} It was possible to join closed games.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Map filtering by game type.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} `cheat health` and `cheat mana` now work properly without arguments.

---

## 1.8.4 (2021-10-31)

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Better performance for particle effects.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow using emotes in campaign.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} `cheat sage` command that gives all spells and scrolls, but doesn't make you invincible.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} `cheat spells` command that only gives all spells for your class.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} `cheat scrolls` command that only gives all best scrolls.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} `cheat god` (as opposed to `set god`) that only makes you invincible, but won't give any spells.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Set time limit for new key bindings to prevent the same action from executing to fast.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Lightning spells were not hitting multiple targets as they should.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Controlled creatures disappearing on map switch.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Effects from Protection spells were played incorrectly.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Random "you cannot wear this" messages when switching equipment.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Allow really large amount of gold in `cheat gold`.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Announcing Solo games to online lobby.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Using relative paths in config.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Better protection from potential memory leaks.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Crash when reading maps that use the new Panic's script compiler.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Multiple other crashes.

---

## 1.8.3 (2021-10-06)

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Integrated the new (simple) server control panel.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Saving complex input bindings to the config.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Wrong interpretation of XWIS option in the new config.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Possible crashes for maps using new memhacks compiler.

---

## 1.8.2 (2021-10-02)

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Write `opennox.yml` config with all extended options.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow changing game data dir via the `opennox.yml` config.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Player names being stuck as online in dedicated server.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Mouse movement on low sensitivity settings.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Assigning keyboard keys instead of mouse for movement.

---

## 1.8.1 (2021-10-01)

- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Back walls rendering in high-resolution mode.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Center in-game menu in high-resolution mode.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Possible crash after running for some time.

---

## 1.8.0 (2021-09-29)

**New**

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} High-resolution support (up to 4K)! You'll need to run `opennox-hd.exe` for it.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} A lot faster OpenGL-based rendering (partially offloaded to GPU).
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Add `cheat charm.all` to charm any creature (including humanoids).
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Automated end-to-end testing mode, see [opennox-e2e](https://github.com/noxworld-dev/opennox-e2e) for details.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Simple HTTP-based Server API for controlling game servers.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow disabling image smoothing in the video options.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow enabling image stretching in the video options.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Other minor optimizations.

**Fixes**

- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Bug with creatures being "deaf" (not reacting to footsteps, etc).
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Properly show the last character in long server names.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Error when manually saving player in online games.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Banish of captured creatures (like vampire bats) leading to scripts being stuck.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Properly forward ports when server port is changed via a flag.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Disabling soft shadows via `-soft` flag.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} LUA scripts when reloading the same map from the console.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Nox Reloaded failing to join OpenNox Quest games.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} OpenNox changing `user.rul` file permissions.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Potential crash on hosting Quest games.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Potential crash when leaving the game.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Crash when opening advanced server setting without admin rights.

---

## 1.7.1 (2021-07-19)

- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Hide OS mouse cursor in windowed mode as well.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Rename “Back” button in input config menu to “Accept”.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Prevent crash on audio errors.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Avoid collision of new health and mana cheats with old ones.

---

## 1.7.0 (2021-07-16)

- {{% badge style="note" title=" " %}}Change{{% /badge %}} Completely reworked input and present pipelines.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Manual spell casting. Bind keys to individual spell gestures and become a real wizard/conjurer!
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Gamma and mouse sensitivity sliders were added to the options menu.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Wide-screen 16:9 resolutions are now available. Older 4:3 resolutions are still supported via config.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Added key bindings for:
    - Switching to a specific spell slot.
    - Switching to a specific trap slot.
    - Dropping a trap from your inventory.
    - Controlling spawned creature behavior.
    - Accepting item buy/sell/drop.
- {{% badge style="warning" title=" " %}}Breaking{{% /badge %}} `set allow.all` was renamed to `cheat equip.all`
- {{% badge style="warning" title=" " %}}Breaking{{% /badge %}} `set mana` was renamed to `cheat mana`
- {{% badge style="warning" title=" " %}}Breaking{{% /badge %}} `set health` was renamed to `cheat health`
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Input sensitivity should now work correctly in fullscreen mode.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Gamma setting in the config is now respected.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Stretched video setting in the config is now respected.

---

## 1.6.1 (2021-06-21)

- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Prevent freeze when closing the game on Windows.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Prevent crash in `set mana`.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Prevent crash when switching shield and bow with `set allow.all` enabled.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Ignore item strength requirement when using `allow.all`.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Remove restrictions from `cheat gold`, so it's accepted in Quest games.

---

## 1.6.0 (2021-06-21)

- {{% badge style="note" title=" " %}}Change{{% /badge %}} Rename project to OpenNox to avoid confusion.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Automatically set Nox data folder. Supports Origin, GoG and Nox Reloaded.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Keep 4:3 aspect ratio when resizing game window.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Toggle fullscreen mode with Alt+Enter.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Add `set health` and `set mana` cheats.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Add `set allow.all` cheat to remove item class restrictions.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Allow customizing `gamedata.bin` values without encoding it. See `gamedata-sample.yml`.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} LUA now supports trigger events as well as player join/leave events.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Detonate traps spell will no longer freeze the game.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Fullscreen mode will now be saved correctly.
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Warriors should now be able to scroll weapons with mouse wheel in multiplayer as well.

---

## 1.5.0 (2021-06-06)

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Automatically open/forward ports when hosting a game (no need to configure firewall).
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Blazing-fast map downloads. Both client and the server should use this version.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Maps will now be transferred with other related files when possible (`.txt`, `.rul`, `.lua`, `.png`).
- {{% badge style="tip" icon="bug-slash" title=" " %}}Fix{{% /badge %}} Fixed the bug that prevented warriors from scrolling weapons with mouse wheel.
- {{% badge style="note" icon="wrench" title=" " %}}Experiment{{% /badge %}} Experimental support for LUA map scripts.

---

## 1.4.0 (2021-05-19)

- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} First public release!
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Compatible with Nox Reloaded.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Native SDL and OpenAL support (no workarounds required for Win10, streaming, etc).
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Builtin XWIS integration. No need for account in order to host or join games.
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} More Nox Quest options (skip levels, keep portal forever, etc).
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Native Linux build (no Wine).
- {{% badge style="info" icon="plus-circle" title=" " %}}New{{% /badge %}} Dedicated "headless" server.
- {{% badge style="note" icon="wrench" title=" " %}}Experiment{{% /badge %}} Gamepad support.

---

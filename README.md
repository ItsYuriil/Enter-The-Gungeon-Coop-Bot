# Enter the Gungeon – Co-op Bot

A BepInEx mod that adds an AI-controlled second player to *Enter the Gungeon*. The bot follows you, fights, dodges, and does what you order with hotkeys. It uses the game's own co-op systems (second player, ghost/revive, co-op camera and UI).

## Features

- **Summon / dismiss** a bot in any run; choose which character it plays (Cultist, Pilot, Convict, Marine, Hunter, Robot, Bullet, Paradox, Gunslinger, ...).
- **Combat:** targets and shoots enemies with lead, slight human-like aim error, reloads smartly, handles charge weapons, drops empty weapons, can use blanks and active items.
- **Dodging:** predicts incoming projectiles and weaves or rolls (with varied reaction times); avoids pits, harmful goop/fire and telegraphed danger zones (e.g. sky rockets).
- **Cover:** flips tables and uses cover, with a configurable preference.
- **Orders (H):** open chests, interact with objects, pick up guns, smash breakables, regroup, or kill the enemy under the cursor.
- **Co-op rules:** works with doors and elevators, becomes a ghost when killed (blocks bullets until revived), camera follows the bot if you are down.
- **Shared loadout:** the bot's items/guns are stored when dismissed and restored when summoned again.
- If you die outside a boss room, the run ends as in single player.
- **Pause-menu "Coop Bot Menu"** to rebind keys and set cover preference.

## Requirements

- *Enter the Gungeon* (Steam, Windows, 64-bit)
- [BepInEx 5.x](https://github.com/BepInEx/BepInEx/releases) (x86/x64 matching the game) installed in the game folder
- The **Mod the Gungeon** API / loader for BepInEx
- To build from source: .NET SDK (any recent version; targets `net35` via reference assemblies)

## Install

1. Install BepInEx and Mod the Gungeon into the game folder and run the game once.
2. Copy `CoopBot.dll` to `<game>\BepInEx\plugins\CoopBot\`.
3. Start a run and press **H**.

## Build from source

```
dotnet build -c Release -p:GamePath="C:\path\to\Enter the Gungeon"
```

The csproj references the game's `Assembly-CSharp.dll`, Unity and BepInEx/Harmony DLLs from `GamePath` (default `G:\SteamLibrary\steamapps\common\Enter the Gungeon`) and copies the result to `BepInEx\plugins\CoopBot\` automatically. Close the game before building (the DLL is locked while it runs).

## Default controls (rebindable in the pause menu or the BepInEx config)

| Key | Action |
|-----|--------|
| H | Summon the bot; afterwards order it (interact / pick up / smash / attack the enemy under the cursor / regroup) |
| Shift+H | Dismiss the bot (saves its loadout) |
| J | Cycle bot character (only while the bot is not active) |
| N | Bot drops its equipped weapon |
| U | Bot uses its active item |
| B | Bot drops its active item |

Config file: `BepInEx\config\` (Controls, Character, CoverPreference, ShowHints).

## Notes

- Not affiliated with Dodge Roll or Devolver Digital. No game files are included in this repository.
- Behaviour is tuned by playtesting; expect rough edges. Bug reports with `BepInEx\LogOutput.log` are welcome.

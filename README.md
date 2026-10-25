# Menyoo (Traditional Chinese Translation for GTA V iOS / macOS Port)

This is a Traditional Chinese (繁體中文) translation and bugfix release for Menyoo v1.0.5 on the GTA V iOS / macOS native port.

Translated and maintained by **@Oyooyee**.

---

## What This Does

Menyoo is one of the most popular trainers for Grand Theft Auto V. While the iOS / macOS port by @cermite_01 made it playable on Apple Silicon and iOS devices, Chinese players previously ran into two major issues:

1. **Theme font bug (□□□ boxes)**: In the GTA V port, only Font 0 (the standard game font) contains CJK Chinese characters. Fonts 1, 2, 4, and 7 lack Chinese glyphs entirely. In original Menyoo, switching menu themes or colors automatically swaps the title and option fonts to Impact or Pricedown, immediately turning all text into square boxes (`□`). This release includes a binary patch on `Menyoo-iOS.asi` that permanently locks the rendering pipeline to Font 0 regardless of what theme or color you select.
2. **Startup freeze / Watchdog timeout**: The port's ScriptHookV compatibility layer enforces a strict 3-second watchdog timer on script initialization. When loading overly large language dictionaries (>150 KB), unbuffered character parsing in the C++ stream timed out, causing the game to silently terminate Menyoo on boot (`a script ran too long without waiting`). This release uses an optimized dictionary (~32 KB, 701 core terms) that covers all essential gameplay settings while booting in under 0.3 seconds.

---

## Included Translations

- **Vehicle Options**: Full vehicle class catalog (Super, Sports, Muscle, Off-Road, etc.), detailed tuning (engine, transmission, turbo, brakes, suspension, armor, xenon, respray, neons, and digital speedometer with km/h units).
- **Player & Weapons**: God mode, never wanted, super jump/run, fast swim, clean ped, infinite ammo, explosive/fire rounds, gravity gun, magnet gun, and damage multipliers.
- **Teleportation**: All safehouses, Ammu-Nation stores, Los Santos Customs, Benny's Original Motor Works, barber shops, and points of interest.
- **Spooner & World**: Core Object Spooner menus, entity spawner, time freeze/sync, and full weather controls.
- **Themes & Settings**: FreeCam controls, keybind descriptions, and all custom color/gradient presets.

---

## Installation

### Prerequisites
- GTA V Port (v1.4.1+ for macOS / iOS)
- Working `Documents/Mods/` directory

### Steps
1. Download `Menyoo_1.0.5_Trans_By_Oyooyee.zip` from this repo (or grab the `Menyoo_1.0.5_TC` folder directly).
2. Copy the `Menyoo_1.0.5_TC` folder into your game's `Documents/Mods/` folder.
   
   Your path should look like this:
   ```text
   Documents/Mods/Menyoo_1.0.5_TC/
   ├── Menyoo-iOS.asi
   ├── Menyoo-iOS.json
   └── menyooStuff/
       ├── Language/
       │   └── Chinese.json
       ├── menyooConfig.ini
       └── ...
   ```
3. Boot into Story Mode.
4. Press **F8** on keyboard (or three-finger tap on touchscreens) to toggle the menu.

---

## Credits

- **MAFINS** - Original MenyooSP developer ([MAFINS/MenyooSP](https://github.com/MAFINS/MenyooSP))
- **@cermite_01** - iOS / macOS ARM64 port
- **@Oyooyee** - Traditional Chinese translation, dictionary optimization, and Font 0 binary patch

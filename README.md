# Menyoo (Traditional Chinese Translation for GTA V Port)

Traditional Chinese (繁體中文) translation and font patch release for Menyoo on the GTA V iOS / macOS native port.

Translated and maintained by **@Oyooyee**.

---

## Releases & Compatibility

| Release | Recommended For | Port Version | Features |
| :--- | :--- | :--- | :--- |
| **Menyoo 2.4.4 (Latest)** | **GTA V Port v1.5+** | **v1.5 (iOS / macOS)** | Desktop Menyoo 2.4.4 engine, full 2,936-entry translation, DLC cars/weapons, async boot, gamepad cold-boot wake fix |
| **Menyoo 1.0.5 (Legacy)** | Older ports | v1.4.1 – v1.4.7 | Lightweight 32 KB dictionary tailored for the strict 3.0s watchdog timer |

---

## Key Fixes & Features

### 1. Gamepad Cold-Boot Wakeup Fix (Direct Controller Access)
In original Menyoo, the menu toggle logic checked either the controller or the keyboard based on the game's current input detection flag (`bit_controller ? gamepad : keyboard`). Because GTA V Port on macOS / iOS initializes with keyboard/touchpad input active, the controller opening combination (`RB + D-Pad Left`) was completely ignored until the menu was opened at least once with the keyboard (`F8`), often triggering the `~r~Error:~s~ Menu not opened yet.` error message.
- **Concurrent Dual-Input Listening**: Patched `Menu::isBinds()` binary logic to listen for both controller combinations and keyboard hotkeys simultaneously every frame. You can now wake Menyoo straight from your controller immediately after game boot without ever touching the keyboard.
- **Cold-Boot Guard Removal**: Neutralized the uninitialized `g_menuNotOpenedYet` barrier that triggered the "Menu not opened yet" error.

### 2. Font 0 Hard-Lock (Eliminates `□□□` Square Boxes)
In GTA V, standard Chinese CJK glyphs are embedded exclusively in **Font 0** (Chalet London 1960). Fonts 1, 2, 4, and 7 do not contain Chinese glyphs.
Original Menyoo uses artistic fonts (Pricedown 7, Impact 4, Italic 1) for its title, selections, and breaks, which caused Chinese characters to display as broken square boxes (`□`). 
- `Menyoo.asi` is binary-patched at all five `SET_TEXT_FONT` call sites to enforce Font 0 directly at the native level.
- `Theme::SetActive` font override routines have been neutralized. You can switch between any theme (Dark, Rainbow, Blue, Green, Red, etc.) without losing your Chinese characters.

### 3. Full Traditional Chinese Localization (2,936 Terms)
With GTA V Port v1.5 providing official MSVC C++ runtime support and an asynchronous 10-second script initialization window, the translation is no longer constrained by the old 3-second watchdog kill:
- **Core Menus**: Player Options, Vehicle Options, Weapon Options, Teleportation, Weather, Time, Spooner, and Settings.
- **GTA Online DLC Vehicles**: Tuners, The Contract, Drug Wars, The Chop Shop, and Bottom Dollar Bounties (e.g. Annis Remus, Euros, Buffalo STX, Gauntlet Hellfire, Krieger, Cavalcade XL, Virtue).
- **DLC Weapons**: Railgun, Tactical SMG, Heavy Rifle, EMP Launcher, Precision Rifle, Service Carbine, Battle Rifle, and Mk II weapon variants.
- **Teleports & Interiors**: Acid Lab, Celebrity Solutions Agency, Chop Shop Salvage Yard, Auto Shop, LS Car Meet & Test Track, Kosatka Submarine, Cayo Perico Island, Dr. Dre's Studio, and Aircraft Carrier.
- **Spooner & Utilities**: Complete object placement, entity attachments, and vehicle tuning with metric (km/h) units.

---

## Installation (GTA V Port v1.5)

1. Download **`Menyoo_2.4.4_Trans_By_Oyooyee.zip`** from this repository (or grab the local copy in your Downloads folder).
2. Extract the archive. You will get a `Menyoo_2.4.4_TC` folder containing `Menyoo.asi`, `Menyoo.json`, and `menyooStuff/`.
3. Copy the `Menyoo_2.4.4_TC` folder directly into your game's `Documents/Mods/` directory.

Your folder structure should look like this:
```text
Documents/Mods/Menyoo_2.4.4_TC/
├── Menyoo.asi
├── Menyoo.json
├── License.txt
├── Readme.txt
└── menyooStuff/
    ├── Language/
    │   ├── Chinese.json
    │   └── French.json
    ├── menyooConfig.ini
    ├── Graphics/
    └── ...
```

4. Launch GTA V Port v1.5 and load into Story Mode.
5. Press **RB + D-Pad Left** on your controller (or **F8** on keyboard) to open the menu.

> **Note for Port v1.4.x users**: If you are still running GTA V Port v1.4.7 or earlier, please use `Menyoo_1.0.5_Trans_By_Oyooyee.zip` (`Menyoo_1.0.5_TC`) instead, as v1.4.x lacks the MSVC runtime required for Menyoo 2.4.4.

---

## Credits

- **MAFINS & ItsJustCurtis** - Original MenyooSP developers ([MAFINS/MenyooSP](https://github.com/MAFINS/MenyooSP))
- **@cermite_01** - iOS / macOS port contributor
- **@Oyooyee** - Traditional Chinese translation, DLC terminology localization, Font 0 / Theme-switch binary patches, and Gamepad cold-boot wakeup fix

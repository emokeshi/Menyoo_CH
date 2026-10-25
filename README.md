# Menyoo (Traditional Chinese Translation for GTA V Port)

Traditional Chinese (繁體中文) translation and font patch release for Menyoo on the GTA V iOS / macOS native port.

Translated and maintained by **@Oyooyee**.

---

## Releases & Compatibility

| Release | Recommended For | Port Version | Features |
| :--- | :--- | :--- | :--- |
| **Menyoo 2.4.4 (Latest)** | **GTA V Port v1.5+** | **v1.5 (iOS / macOS)** | Desktop Menyoo 2.4.4 engine, full 2,936-entry translation, DLC cars/weapons, async boot |
| **Menyoo 1.0.5 (Legacy)** | Older ports | v1.4.1 – v1.4.7 | Lightweight 32 KB dictionary tailored for the strict 3.0s watchdog timer |

---

## Key Fixes & Features

### 1. Font 0 Hard-Lock (Eliminates `□□□` Square Boxes)
In GTA V, standard Chinese CJK glyphs are embedded exclusively in **Font 0** (Chalet London 1960). Fonts 1, 2, 4, and 7 do not contain Chinese glyphs.
Original Menyoo uses artistic fonts (Pricedown 7, Impact 4, Italic 1) for its title, selections, and breaks, which caused Chinese characters to display as broken square boxes (`□`). 

In this release:
- `Menyoo.asi` is binary-patched at all five `SET_TEXT_FONT` call sites to enforce Font 0 directly at the native level.
- `Theme::SetActive` font override routines have been neutralized. You can switch between any theme (Dark, Rainbow, Blue, Green, Red, etc.) without losing your Chinese characters.

### 2. Full Traditional Chinese Localization (2,936 Terms)
With GTA V Port v1.5 providing official MSVC C++ runtime support and an asynchronous 10-second script initialization window, the translation is no longer constrained by the old 3-second watchdog kill:
- **Core Menus**: Player Options, Vehicle Options, Weapon Options, Teleportation, Weather, Time, Spooner, and Settings.
- **GTA Online DLC Vehicles**: Tuners, The Contract, Drug Wars, The Chop Shop, and Bottom Dollar Bounties (e.g. Annis Remus, Euros, Buffalo STX, Gauntlet Hellfire, Krieger, Cavalcade XL, Virtue).
- **DLC Weapons**: Railgun, Tactical SMG, Heavy Rifle, EMP Launcher, Precision Rifle, Service Carbine, Battle Rifle, and Mk II weapon variants.
- **Teleports & Interiors**: Acid Lab, Celebrity Solutions Agency, Chop Shop Salvage Yard, Auto Shop, LS Car Meet & Test Track, Kosatka Submarine, Cayo Perico Island, Dr. Dre's Studio, and Aircraft Carrier.
- **Spooner & Utilities**: Complete object placement, entity attachments, and vehicle tuning with metric (km/h) units.

---

## Installation (GTA V Port v1.5)

1. Download **`Menyoo_2.4.4_Trans_By_Oyooyee.zip`** from this repository.
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
5. Press **F8** on keyboard (or **RB + D-Pad Left** on controller) to open the menu.

> **Note for Port v1.4.x users**: If you are still running GTA V Port v1.4.7 or earlier, please use `Menyoo_1.0.5_Trans_By_Oyooyee.zip` (`Menyoo_1.0.5_TC`) instead, as v1.4.x lacks the MSVC runtime required for Menyoo 2.4.4.

---

## Credits

- **MAFINS & ItsJustCurtis** - Original MenyooSP developers ([MAFINS/MenyooSP](https://github.com/MAFINS/MenyooSP))
- **@cermite_01** - iOS / macOS port contributor
- **@Oyooyee** - Traditional Chinese translation, DLC terminology localization, and Font 0 / Theme-switch binary patches

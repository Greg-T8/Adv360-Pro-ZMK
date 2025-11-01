# Custom Kinesis Advantage 360 Pro Configuration

This is my heavily customized ZMK configuration for the Kinesis Advantage 360 Pro keyboard, focusing on efficiency, ergonomics, and advanced typing features.

## Overview

This configuration implements:

- **9 layers**: DEFAULT, GAME, BF (Battlefield), WT (War Thunder), NUM, NAV, FN, NAV2, MOD
- **70+ combos** for symbols, navigation, and text editing
- **Home row mods** with optimized timing for comfortable typing
- **Tap dance behaviors** for advanced key sequences
- **Custom macros** for window management and special characters
- **Balanced hold-tap behaviors** to minimize accidental activations

## Keymap Visualization

You can view an interactive visualization of the keymap at:

**[View Interactive Keymap →](https://keymap-drawer.streamlit.app/?zmk_url=https%3A%2F%2Fgithub.com%2FGreg-T8%2FKinesis-Adv360Pro-ZMK%2Fblob%2Fmain%2Fconfig%2Fadv360.keymap)**

The visualization shows:

- Default layer with home row mods
- All combo positions and their outputs
- Layer-specific keybindings
- Hold vs. tap behaviors

## Key Features

### Home Row Mods

The default layer uses home row mods on the left hand:

- `A` → GUI when held
- `S` → ALT when held
- `D` → CTRL when held
- `F` → SHIFT when held

Right hand home row mods:

- `J` → SHIFT when held
- `K` → CTRL when held
- `L` → ALT when held
- `;` → GUI when held

**Timing Configuration:**

- Tapping term: 280ms (left), 280ms (right)
- Prior idle requirement: 170ms (left), 250ms (right)
- Quick tap: 150ms
- Hold-trigger-on-release enabled for smooth modifier combinations

### Layer System

1. **DEFAULT (0)**: Standard QWERTY with home row mods and extensive combos
2. **GAME (1)**: Traditional gaming layout with no home row mods
3. **BF (2)**: Battlefield-optimized layout
4. **WT (3)**: War Thunder-specific bindings
5. **NUM (4)**: Number pad layer accessed via right thumb
6. **NAV (5)**: Navigation layer with arrow keys and number pad on left hand
7. **FN (6)**: Function keys (F1-F12) accessed via left thumb
8. **NAV2 (7)**: Extended navigation for alt-tab macro
9. **MOD (8)**: System settings, Bluetooth, RGB controls

### Combos

This configuration includes 70+ combos organized into categories:

#### Left Hand Horizontal Combos

- **17+18**: Tab (12ms timeout for fast activation)
- **16+17**: Reverse Tab (Shift+Tab)
- **30+31**: ESC (hold for ALT+CTRL)
- **31+32**: CTRL+SHIFT
- **32+33**: Undo (CTRL+Z)
- **48+49**: Delete (hold for CTRL+DEL)
- **49+50**: Backspace (hold for CTRL+BSPC)
- **65+66**: Sticky Shift

#### Left Hand Vertical Combos

Special characters:

- **15+29**: `!` (Exclamation)
- **16+30**: `%` (Percent)
- **17+31**: `@` (At)
- **18+32**: `$` (Dollar)
- **19+33**: `#` (Hash)

Text editing:

- **29+47**: Select All (CTRL+A)
- **30+48**: Cut (CTRL+X)
- **31+49**: Copy (CTRL+C)
- **32+50**: Paste (tap dance: CTRL+V / CTRL+SHIFT+V)
- **33+51**: Bold (CTRL+B)

#### Right Hand Horizontal Combos

Brackets and quotes:

- **22+23**: `_` (Underscore)
- **23+24**: `[` (Left bracket, 25ms timeout)
- **24+25**: `]` (Right bracket)
- **40+41**: `"` (Double quotes)
- **41+42**: `(` (Left paren, hold for CTRL+SHIFT)
- **42+43**: `)` (Right paren, hold for ALT+CTRL)
- **54+55**: `'` (Single quote)
- **55+56**: `{` (Left brace)
- **56+57**: `}` (Right brace)

#### Right Hand Vertical Combos

Math and symbols:

- **22+40**: `*` (Star)
- **23+41**: `+` (Plus)
- **24+42**: `=` (Equal)
- **25+43**: `&` (Ampersand)
- **26+44**: `^` (Caret)
- **40+54**: `` ` `` (Grave)
- **41+55**: `-` (Minus)
- **42+56**: `/` (Slash)
- **43+57**: `|` (Pipe)
- **44+58**: `\` (Backslash)

### Macros

Custom macros for enhanced workflow:

- **alttab**: Hold ALT, tap TAB, activates NAV2 layer for navigation, releases ALT on layer exit
- **close**: ALT+DEL for closing windows
- **arrow**: Types `=>` (JavaScript arrow function)
- **endash**: Inserts en-dash character (–)

### Tap Dance

- **td_paste**: Single tap = CTRL+V (paste), double tap = CTRL+SHIFT+V (paste special)

### Mod Morphs

Prevents unintended behavior when shift is held:

- Numbers (0-9), brackets, parentheses, quotes, comma, dot, colon, minus, underscore, backslash
- HOME/END masked with CTRL to prevent document-level jumps

### Timing Constants

```c
#define TAPPING_TERM 220        // Standard hold-tap timing
#define PRIOR_IDLE   170        // Prevents accidental mod activation when typing fast
#define QUICK_TAP    150        // Repeat key timing
#define COMBO_TERM_FAST 15      // Fast combo timeout for frequently used combos
#define COMBO_TERM_SLOW 200     // Standard combo timeout
#define COMBO_IDLE_FAST 120     // Fast combo idle time
#define COMBO_IDLE_SLOW 250     // Larger idle time reduces accidental combos
```

### Navigation Layer Features

The NAV layer (activated via left thumb space hold) provides:

- **Arrow keys** on right hand (J/K/L/;)
- **Number pad** on left hand (home row: 4/5/6/0, upper row: 7/8/9, lower row: 1/2/3)
- **Home/End navigation** with smart CTRL masking
- **Page Up/Down** for scrolling

### Number Layer Features

The NUM layer (activated via right thumb space hold) provides:

- **Number pad layout** on left hand matching NAV layer
- Optimized for numeric data entry
- Quick access to numbers without leaving home position

### Function Layer Features

The FN layer (accessed via left thumb shift hold) provides:

- **F1-F12** function keys
- Organized in standard number pad layout (F7/F8/F9, F4/F5/F6, F1/F2/F3, F10/F11/F12)

## Building and Flashing

### Build with GitHub Actions

1. Fork this repository
2. Enable GitHub Actions
3. Push changes to trigger build
4. Download firmware artifacts from Actions tab

### Flash Firmware

1. Connect left keyboard via USB
2. Press Mod+macro1 for bootloader mode
3. Copy `left.uf2` to USB drive
4. Repeat for right side with Mod+macro3
5. Use `right.uf2` for right side

For detailed flashing instructions, see the [Quick Start Guide](https://kinesis-ergo.com/wp-content/uploads/Advantage360-Professional-QSG-v8-25-22.pdf).

## Building the Firmware in a local container

### Setup

#### Software

- Either Podman or Docker is required, Podman is chosen if both are installed.
- Make is also required

#### Windows specific

- If compiling on Windows use WSL2 and Docker [Docker Setup Guide](https://docs.docker.com/desktop/windows/wsl/).
- Install make using `sudo apt-get install make` inside the WSL2 instance.
- The repository can be cloned directly into the WSL2 instance or accessed through the C: mount point WSL provides by default (`/mnt/c/path-to-repo`).

#### macOS specific

On macOS [brew](https://brew.sh) can be used to install the required components.

- docker
- [colima](https://github.com/abiosoft/colima) can be used as the docker engine

```shell
brew install docker colima
colima start
```

> Note: On Apple Silicon (ARM based) systems you need to make sure to start colima with the correct architecture for the container being used.
>
> ```shell
> colima start --arch x86_64
> ```

#### Ubuntu/Debian specific

```shell
sudo apt-get install docker make
```

### Building the firmware

1. Execute `make` to build firmware for both halves or `make left` to only build firmware for the left hand side.
2. Check the `firmware` directory for the latest firmware build. The first part of the filename is the timestamp when the firmware was built.

### Cleanup

The built docker container and compiled firmware files can be deleted with `make clean`. This might be necessary if you updated your fork from V2.0 to V3.0 and are encountering build failures.

Creating the docker container takes some time. Therefore `make clean_firmware` can be used to only clean firmware without removing the docker container. Similarly `make clean_image` can be used to remove the docker container without removing compiled firmware files.

## Flashing firmware

Follow the programming instruction on page 8 of the [Quick Start Guide](https://kinesis-ergo.com/wp-content/uploads/Advantage360-Professional-QSG-v8-25-22.pdf) to flash the firmware.

### Overview

1. Extract the firmwares from the archive downloaded from the GitHub build job (If using the cloud builder) or the firmware folder (If building locally).
1. Connect the left side keyboard to USB.
1. Press Mod+macro1 to put the left side into bootloader mode; it should attach to your computer as a USB drive.
1. Copy `left.uf2` to the USB drive and it will disconnect.
1. Power off both keyboards (by unplugging them and making sure the switches are off).
1. Turn on the left side keyboard with the switch.
1. Connect the right side keyboard to USB to power it on.
1. Press Mod+macro3 to put the right side into bootloader mode to attach it as a USB drive.
1. Copy `right.uf2` to the mounted drive.
1. Unplug the right side keyboard and turn it back on.
1. Enjoy!

> Note: There are also physical reset buttons on both keyboards which can be used to enter and exit the bootloader mode. Their location is described in section 2.7 on page 9 in the [User Manual](https://kinesis-ergo.com/wp-content/uploads/Advantage360-ZMK-KB360-PRO-Users-Manual-v3-10-23.pdf) and use is described in section 5.9 on page 14.

> Note: Some operating systems wont always treat the drive as ejected after the settings-reset file is flashed or may throw a spurious error, this doesn't mean that the flashing process has failed.

### Upgrading from V2 to V3

If you encounter a git conflict when updating your repository to V3.0 please follow the instructions on how to resolve it [here](UPGRADE.md).

Updating from V2.0 based firmwares to V3.0 based firmwares can be a rather complex process. There are reset files for every major firmware revision as well as documentation on the update process available [here](https://kinesis-ergo.com/support/kb360pro/#firmware-updates).

## Versioning

Starting on 11/15/2023 the Advantage 360 Pro will now automatically record the compilation date, branch and Git commit hash in a macro that can be accessed with Mod+V. This will type out the following string: YYYYMMDD-XXXX-YYYYYY, where XXXX is the first 4 characters of the Git branch and YYYYYY is the Git commit hash. In addition to this the builds compiled by GitHub actions are now timestamped and also record the commit hash in the filename.

## N-Key Rollover

By default this keyboard has NKRO enabled, however for compatibility reasons the higher ranges are not enabled. If you want to use F13-F24 or the INTL1-9 keys with NKRO enabled you can change `CONFIG_ZMK_HID_KEYBOARD_EXTENDED_REPORT=n` to `CONFIG_ZMK_HID_KEYBOARD_EXTENDED_REPORT=y` in [adv360_left_defconfig](/config/boards/arm/adv360/adv360_left_defconfig#L65)

## Battery reporting

By default reporting the battery level over BLE is disabled as this can cause some computers to spontaneously wake up repeatedly. If you'd like to enable this functionality change `CONFIG_BT_BAS=n` to  `CONFIG_BT_BAS=y` in [adv360_left_defconfig](/config/boards/arm/adv360/adv360_left_defconfig#L58).

## Modifier indicator color

The color of the CAPS/NUM/SCROLL LOCK indicator LEDs may be configured by specifying a hexadecimal RGB color code. For example, `CONFIG_ZMK_RGB_UNDERGLOW_MOD_COLOR=0xFF0000` would give red indicator colors. In order to set the indicator color on both modules, ensure that both [adv360_left_defconfig](/config/boards/arm/adv360/adv360_left_defconfig) and [adv360_right_defconfig](/config/boards/arm/adv360/adv360_right_defconfig) have been updated.

## Layer colors

A total of 32 layers are supported by ZMK, with the highest currently active layer displayed using the layer LEDs on each of the left and right modules. All possible colors are listed below; for the first 8 layers the same color is displayed on both modules. After that, only the right module color will cycle through until "rolling over", which will cause the left module color to change as well (and this then repeats). To avoid confusion, the black/off LED color is only used for layer 0.

| Layer # | L/R | Layer # | L/R | Layer # | L/R | Layer # | L/R |
| ---: | :---: | ---: | :---: | ---: | :---: | ---: | :---: |
| 0 | <img valign='middle' src='assets/swatches/000000.svg'/> <img valign='middle' src='assets/swatches/000000.svg'/> | 8 | <img valign='middle' src='assets/swatches/FFFFFF.svg'/> <img valign='middle' src='assets/swatches/0000FF.svg'/> | 16 | <img valign='middle' src='assets/swatches/0000FF.svg'/> <img valign='middle' src='assets/swatches/FF0000.svg'/> | 24 | <img valign='middle' src='assets/swatches/00FF00.svg'/> <img valign='middle' src='assets/swatches/00FFFF.svg'/> |
| 1 | <img valign='middle' src='assets/swatches/FFFFFF.svg'/> <img valign='middle' src='assets/swatches/FFFFFF.svg'/> | 9 | <img valign='middle' src='assets/swatches/FFFFFF.svg'/> <img valign='middle' src='assets/swatches/00FF00.svg'/> | 17 | <img valign='middle' src='assets/swatches/0000FF.svg'/> <img valign='middle' src='assets/swatches/FF00FF.svg'/> | 25 | <img valign='middle' src='assets/swatches/00FF00.svg'/> <img valign='middle' src='assets/swatches/FFFF00.svg'/> |
| 2 | <img valign='middle' src='assets/swatches/0000FF.svg'/> <img valign='middle' src='assets/swatches/0000FF.svg'/> | 10 | <img valign='middle' src='assets/swatches/FFFFFF.svg'/> <img valign='middle' src='assets/swatches/FF0000.svg'/> | 18 | <img valign='middle' src='assets/swatches/0000FF.svg'/> <img valign='middle' src='assets/swatches/00FFFF.svg'/> | 26 | <img valign='middle' src='assets/swatches/FF0000.svg'/> <img valign='middle' src='assets/swatches/FFFFFF.svg'/> |
| 3 | <img valign='middle' src='assets/swatches/00FF00.svg'/> <img valign='middle' src='assets/swatches/00FF00.svg'/> | 11 | <img valign='middle' src='assets/swatches/FFFFFF.svg'/> <img valign='middle' src='assets/swatches/FF00FF.svg'/> | 19 | <img valign='middle' src='assets/swatches/0000FF.svg'/> <img valign='middle' src='assets/swatches/FFFF00.svg'/> | 27 | <img valign='middle' src='assets/swatches/FF0000.svg'/> <img valign='middle' src='assets/swatches/0000FF.svg'/> |
| 4 | <img valign='middle' src='assets/swatches/FF0000.svg'/> <img valign='middle' src='assets/swatches/FF0000.svg'/> | 12 | <img valign='middle' src='assets/swatches/FFFFFF.svg'/> <img valign='middle' src='assets/swatches/00FFFF.svg'/> | 20 | <img valign='middle' src='assets/swatches/00FF00.svg'/> <img valign='middle' src='assets/swatches/FFFFFF.svg'/> | 28 | <img valign='middle' src='assets/swatches/FF0000.svg'/> <img valign='middle' src='assets/swatches/00FF00.svg'/> |
| 5 | <img valign='middle' src='assets/swatches/FF00FF.svg'/> <img valign='middle' src='assets/swatches/FF00FF.svg'/> | 13 | <img valign='middle' src='assets/swatches/FFFFFF.svg'/> <img valign='middle' src='assets/swatches/FFFF00.svg'/> | 21 | <img valign='middle' src='assets/swatches/00FF00.svg'/> <img valign='middle' src='assets/swatches/0000FF.svg'/> | 29 | <img valign='middle' src='assets/swatches/FF0000.svg'/> <img valign='middle' src='assets/swatches/FF00FF.svg'/> |
| 6 | <img valign='middle' src='assets/swatches/00FFFF.svg'/> <img valign='middle' src='assets/swatches/00FFFF.svg'/> | 14 | <img valign='middle' src='assets/swatches/0000FF.svg'/> <img valign='middle' src='assets/swatches/FFFFFF.svg'/> | 22 | <img valign='middle' src='assets/swatches/00FF00.svg'/> <img valign='middle' src='assets/swatches/FF0000.svg'/> | 30 | <img valign='middle' src='assets/swatches/FF0000.svg'/> <img valign='middle' src='assets/swatches/00FFFF.svg'/> |
| 7 | <img valign='middle' src='assets/swatches/FFFF00.svg'/> <img valign='middle' src='assets/swatches/FFFF00.svg'/> | 15 | <img valign='middle' src='assets/swatches/0000FF.svg'/> <img valign='middle' src='assets/swatches/00FF00.svg'/> | 23 | <img valign='middle' src='assets/swatches/00FF00.svg'/> <img valign='middle' src='assets/swatches/FF00FF.svg'/> | 31 | <img valign='middle' src='assets/swatches/FF0000.svg'/> <img valign='middle' src='assets/swatches/FFFF00.svg'/> |

## Changelog

The changelog for both the config repo and the underlying ZMK fork that the config repo builds against can be found [here](CHANGELOG.md).

## Beta testing

The Advantage 360 Pro is always getting updates and refinements. If you are willing to beta test you can follow [this guide from ZMK](https://zmk.dev/docs/features/beta-testing#testing-features) on how to change where your config repo points to. The `west.yml` file that is mentioned is located in config/. [This link](config/west.yml) can take you to the file. Typically you will only need to change the `revision:` to match the beta branch. There is currently no beta branch available for testing.

Feedback on beta branches should be submitted as a GitHub issue on the base ZMK repository as opposed to this config repository.

In the event of a major update the beta branch may not be compatible with the current mainline version of the config repository. If this is the case it will be detailed here along with instructions on how to update.

## Note

By default this config repository references [a customised version of ZMK](https://github.com/ReFil/zmk/tree/adv360-z3.5) with Advantage 360 Pro specific functionality and changes over [base ZMK](https://github.com/zmkfirmware/zmk). The Kinesis fork is regularly updated to bring the latest updates and changes from base ZMK however will not always be completely up to date, some features such as new keycodes will not be immediately available on the 360 Pro after they are implemented in base ZMK.

Whilst the Advantage 360 Pro is compatible with base ZMK (The pull request to merge it can be seen [here](https://github.com/zmkfirmware/zmk/pull/1454) if you want to see how to implement it) some of the more advanced features (the indicator RGB leds) will not work, and Kinesis cannot provide customer service for usage of base ZMK. Likewise the ZMK community cannot provide support for either the Kinesis keymap editor, nor any usage of the Kinesis custom fork.

## Other support

Further support resources can be found on Kinesis.com:

- [Firmware Updates](https://kinesis-ergo.com/support/kb360pro/#firmware-updates)
- [User Manuals](https://kinesis-ergo.com/support/kb360pro/#manuals)

In the event of a hardware issue it may be necessary to open a support ticket directly with Kinesis as opposed to a GitHub issue in this repository.

- [Support Ticket System](https://kinesis-ergo.com/support/kb360pro/#ticket)

## Resources

- [ZMK Documentation](https://zmk.dev/docs) - For understanding ZMK behaviors and features
- [Key Positions Reference](assets/key-positions.md) - Visual guide for combo key positions
- [Kinesis 360 Pro Manual](https://kinesis-ergo.com/wp-content/uploads/Advantage360-ZMK-KB360-PRO-Users-Manual-v3-10-23.pdf) - Official hardware documentation

# Super Mario 64 Mobile
- also known as sm64mobile

A high-performance mobile port of the Super Mario 64 decompilation, optimized for Android and iOS (M1/A-series) devices. This port leverages **SDL2** for input handling and provides the **complete game experience**, from entering Peach's Castle all the way to the final credits.

## Features
- **Native ARM64 Support:** Optimized for modern mobile processors, including the Apple M1.
- **Controller Support:** Full integration for joysticks, triggers, and face buttons via SDL2.
- **On-Screen Controls:** Touch-screen overlay for mobile-only play.
- **High Performance:** Capable of running at native refresh rates on modern mobile hardware.

## Prerequisites
To build this project, you will need the following dependencies:

### iOS / macOS
- **Xcode & Command Line Tools**
- **Homebrew**
- **MIPS Binutils:** `brew tap n64tools/n64tools && brew install mips64-elf-binutils`
- **SDL2:** `brew install sdl2 pkg-config`

### Android / Linux
- **Build Essentials:** `sudo apt install build-essential pkg-config`
- **Android NDK:** Latest version configured in your environment (ensure `$ANDROID_NDK_LATEST_HOME` is set).
- **MIPS Binutils:** `sudo apt install binutils-mips-linux-gnu`
- **SDL2:** `sudo apt install libsdl2-dev`

## Building
A valid Super Mario 64 ROM (US version) is required to extract assets. Place your ROM in the root directory and rename it to `baserom.us.z64`.

### Build for Android
1. **Prepare the environment:** Ensure you have the Android NDK and MIPS binutils installed.
2. **Asset Extraction:** The Makefile will automatically use the MIPS tools to extract game assets from your ROM.
3. **Compile:** Run the following command:
```bash
make TARGET_ANDROID=1 ARCH=arm64 CROSS_COMPILE=mips-linux-gnu- HAVE_SDL2=1 -j$(nproc)

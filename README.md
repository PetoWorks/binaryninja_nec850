# Renesas NEC850 Architecture Plugin

This Binary Ninja plugin provides a native implementation for the Renesas RH850/V850 architecture. The main reason for writing this from scratch instead of using existing plugin is that any Architecture plugin written in Python is not usable for large binaries as the analysis takes ages. Therefore, this is a complete coverage of this architecture written purely in C/C++.

## Install

The `binaryninjaapi` submodule must match the Binary Ninja build you are targeting. This repo is pinned to the API revision that matches Binary Ninja `5.3.9072-dev`.

1. Clone this repo: `git clone https://github.com/Accenture/NEC850_Architecture && cd NEC850_Architecture`
2. Fetch submodules: `git submodule update --init --recursive`
3. Configure the build:
   - macOS app bundle: `cmake -S . -B build -DBN_INSTALL_DIR="/Applications/Binary Ninja.app" -DHEADLESS=1`
   - Linux example: `cmake -S . -B build -DBN_INSTALL_DIR=/opt/binaryninja -DHEADLESS=1`
4. Build the plugin: `cmake --build build -j4`
5. Install it to your user plugin directory: `cmake --install build`

On macOS the built plugin artifact is `build/libnec850_arch.dylib`.

## Windows (MSVC) Build

1. `cmake -S . -B build -G "Visual Studio 18 2026" -DBN_INSTALL_DIR="C:/Users/<you>/AppData/Local/Programs/Vector35/BinaryNinja"`
2. `cmake --build build --config Release --parallel`
3. Output: `build/Release/nec850_arch.dll` → copy to `%APPDATA%/Binary Ninja/plugins`

### Note on binaryninjaapi version
- Match the `binaryninjaapi` submodule to your installed Binary Ninja API revision (see `api_REVISION.txt` under the Binary Ninja install, then `git -C binaryninjaapi checkout <revision>`). This avoids BNGet* linker errors.

# Renesas NEC850 Architecture Plugin

This Binary Ninja plugin provides a native implementation for the Renesas RH850/V850 architecture. The main reason for writing this from scratch instead of using existing plugin is that any Architecture plugin written in Python is not usable for large binaries as the analysis takes ages. Therefore, this is a complete coverage of this architecture written purely in C/C++.

## Install

1. Clone this repo: `git clone https://github.com/Accenture/NEC850_Architecture && cd NEC850_Architecture`
2. Fetch submodules: `git submodule update --init --recursive`
3. CMake things: `mkdir build && cd build && cmake .. -DBN_INSTALL_DIR=/opt/binaryninja` (Replace the `/opt/binaryninja` string at the end with an actual install path of your instance)
4. Make things and install plugin: `make -j4 && cp libnec850_arch.so ~/.binaryninja/plugins/` (Replace the last part of the command with valid path to the plugins directory for your platform)

## Windows (MSVC) Build

1. `cmake -S . -B build -G "Visual Studio 18 2026" -DBN_INSTALL_DIR="C:/Users/<you>/AppData/Local/Programs/Vector35/BinaryNinja"`
2. `cmake --build build --config Release --parallel`
3. Output: `build/Release/nec850_arch.dll` → copy to `%APPDATA%/Binary Ninja/plugins`

### Note on binaryninjaapi version
- Match the `binaryninjaapi` submodule to your installed Binary Ninja API revision (see `api_REVISION.txt` under the Binary Ninja install, then `git -C binaryninjaapi checkout <revision>`). This avoids BNGet* linker errors.

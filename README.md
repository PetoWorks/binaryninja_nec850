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

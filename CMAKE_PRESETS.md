# CMake Presets Usage

## Overview

This project uses CMake Presets (CMakePresets.json) to simplify the build configuration process. CMake Presets provide a standard way to configure common build scenarios with predefined settings.

## Prerequisites

- CMake >= 3.19 (CMake Presets support was introduced in version 3.19)
- All dependencies listed in the INSTALL file

## Available Presets

### Configure Presets

List all available presets:
```bash
cmake --list-presets
```

#### General Presets (Platform-independent)

- **debug** - Debug build with symbols
- **release** - Optimized release build
- **relwithdebinfo** - Release build with debug information
- **minsizerel** - Release build optimized for size

#### Linux-specific Presets

- **linux-debug** - Debug build for Linux
- **linux-release** - Release build for Linux

#### Windows-specific Presets

- **windows-debug** - Debug build for Windows
- **windows-release** - Release build for Windows

### Build Presets

- **debug** - Build using debug configuration
- **release** - Build using release configuration
- **relwithdebinfo** - Build using RelWithDebInfo configuration
- **minsizerel** - Build using MinSizeRel configuration
- **linux-debug** - Build Linux debug configuration
- **linux-release** - Build Linux release configuration
- **windows-debug** - Build Windows debug configuration
- **windows-release** - Build Windows release configuration

## Quick Start

### Using Presets

1. **Configure** the project:
   ```bash
   cmake --preset debug
   ```
   or
   ```bash
   cmake --preset release
   ```

2. **Build** the project:
   ```bash
   cmake --build --preset debug
   ```
   or
   ```bash
   cmake --build --preset release
   ```

3. **Install** (optional):
   ```bash
   cmake --build build/debug --target install
   ```

### Traditional Build (still supported)

The traditional CMake workflow is still fully supported:
```bash
cmake -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build
sudo cmake --build build --target install
```

## User-Specific Presets

You can create your own user-specific presets by copying the example file:

```bash
cp CMakeUserPresets.json.example CMakeUserPresets.json
```

Then edit `CMakeUserPresets.json` to add your own custom configurations. This file is git-ignored and won't be committed to the repository.

### Example User Preset

The example file includes presets for:
- Custom Qt6 paths
- Custom install prefixes
- User-specific debug/release configurations

## Build Directory Structure

When using presets, build directories are organized as:
```
build/
  debug/           # Debug build files
  release/         # Release build files
  relwithdebinfo/  # RelWithDebInfo build files
  linux-debug/     # Linux debug build files
  linux-release/   # Linux release build files
```

## Benefits of Using Presets

1. **Consistency** - Standardized build configurations across developers
2. **Convenience** - Simple one-command configuration
3. **Discoverability** - Easy to see available build options
4. **Separation** - Different build types in separate directories
5. **IDE Integration** - Better support in modern IDEs (VS Code, CLion, etc.)

## IDE Support

Modern IDEs with CMake support will automatically detect and use these presets:
- Visual Studio Code (with CMake Tools extension)
- CLion
- Visual Studio 2019+
- Qt Creator 8+

## Troubleshooting

### "CMake 3.19 or higher is required"

Upgrade your CMake installation:
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install cmake

# Or download from https://cmake.org/download/
```

### "Preset not found"

Make sure you're in the project root directory where CMakePresets.json is located.

## Additional Resources

- [CMake Presets Documentation](https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html)
- [DSView Build Instructions](INSTALL)

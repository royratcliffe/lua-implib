# lua-implib

`lua-implib` generates a Windows import library (`lua.lib`) from the Lua
exports listed in [`lua.def`](lua.def). The library lets MSVC projects link
against a compatible Lua DLL.

This project does not build or include Lua, its DLL, or Lua headers. The DLL
used at runtime must provide the exports in `lua.def` and be ABI-compatible
with the application.

## Requirements

- Windows and the Microsoft Visual C++ toolchain
- CMake 3.22 or later

## Build

The included presets use the Visual Studio 2026 x64 generator:

```powershell
cmake --preset windows-vs2026
cmake --build --preset windows-vs2026-release
```

The generated import library is `lua.lib` in the build directory.

## Install

To install `lua.lib` under the configured CMake install prefix, use the
corresponding build directory:

```powershell
cmake --install <build-directory> --config Release
```

To use the Eagle Dynamics preset, which sets the install prefix to
`%ProgramData%\Eagle Dynamics`:

```powershell
cmake --build --preset windows-vs2026-eagle-dynamics-release-install
```

The install rule places the library in the prefix's `lib` directory.

## Custom configuration

For another MSVC generator or install prefix, configure CMake with the desired
generator and set `CMAKE_INSTALL_PREFIX` as needed. The `LuaLib` target creates
`lua.lib`; the `install` target installs it under `lib`.

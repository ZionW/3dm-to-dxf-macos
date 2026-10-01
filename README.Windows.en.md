# 3DM → DXF: Windows

[繁體中文](README.Windows.zh-TW.md) · [GitHub](https://github.com/ZionW/3dm-to-dxf-macos)

For Windows 10 / 11 on Intel or AMD 64-bit PCs. Download `3DM-to-DXF-Windows-x64-v0.10.0.zip` and extract the whole folder. Drag one or more `.3dm` files onto `3DM to DXF.exe`, or create a desktop shortcut to the executable and drop files on that shortcut.

There is no main window. The app does not launch Rhino and needs no Python, Rhino or ODA installation. DXF files are written beside their sources; existing names get `_1`, `_2`, etc. Windows notifications report completion or failure. Do Not Disturb or notification settings may hide the notification; batch results are also saved in `%LOCALAPPDATA%\3DM-to-DXF\logs`. Run as a normal user: elevated apps may reject Explorer drag and drop.

This build has no purchased Windows code-signing certificate. SmartScreen may show an unknown-publisher prompt. Check that the download comes from this project's GitHub Release and verify its SHA-256.

Supported objects include common points, lines, circles, arcs, polylines, NURBS curves, meshes, hatches, text, representable block references, linear dimensions and planar reference pictures. Layer names, colors, visibility, locking and units are retained. The DXF is read back to check source object IDs, types and hatch boundary counts. An audit requiring repair prevents publication of that output.

General Brep solids, specialized objects and unsupported transforms may fail. A `.conversion-error.txt` file explains the failure; other files in the batch continue. Success produces a `.dxf.verification.json` report. Fonts depend on the receiving CAD application. Pictures are external references: move the adjacent `<source-name>_embedded_files` folder along with the DXF. Hidden source layers remain hidden.

The packaged EXE is tested on a GitHub Windows runner using synthetic fixtures for Unicode paths with spaces, hatch holes, block placement, dimensions, NURBS, meshes, layers, DXF readback, existing-name protection and mixed success/failure batches. Explorer drag gestures and the visible notification still require testing on an interactive Windows desktop.

Conversion is local; models are never uploaded.

## Build from source

Install Python 3.14 x64, Git, CMake and Visual Studio 2022 Build Tools with Desktop development with C++. From the extracted source directory, run PowerShell:

```powershell
./build.ps1
```

The script downloads a pinned official openNURBS commit and the PyPI versions in `requirements.txt`. Outputs go to `release` after the tests pass. Source is supplied for inspection and rebuilding. Third-party license texts are included in the download.

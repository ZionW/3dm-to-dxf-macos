# 3DM → DXF for macOS and Windows

Drag one or more `.3dm` files onto the app to create `.dxf` files without opening Rhino.
將一個或多個 `.3dm` 檔案拖到程式圖示，即可產生 `.dxf`，不需要開啟 Rhino。

## Download / 下載

| Platform / 平台 | Release / 版本 | Guides / 說明 |
| --- | --- | --- |
| Windows 10/11 x64 | [Windows v0.10.0](https://github.com/ZionW/3dm-to-dxf-macos/releases/tag/v0.10.0-windows) | [繁體中文](README.Windows.zh-TW.md) · [English](README.Windows.en.md) |
| macOS Apple Silicon | [macOS v0.9](https://github.com/ZionW/3dm-to-dxf-macos/releases/tag/v0.9) | [繁體中文](README.zh-TW.md) · [English](README.en.md) |

Unzip the download, then drag files onto `3DM to DXF.exe` (Windows) or `3DM to DXF.app` (macOS). DXF files are saved beside the originals; existing files are protected with `_1`, `_2` suffixes.
下載後解壓縮，把檔案拖到 Windows 的 `3DM to DXF.exe` 或 macOS 的 `3DM to DXF.app`。DXF 輸出在原資料夾，同名檔自動加 `_1`、`_2`。

## Source and build / 原始碼與建置

Windows source is included in `windows-source-v0.10.0.zip`. Build with `build.ps1`; see the Windows guides for prerequisites and supported geometry. GitHub Actions tests the packaged EXE before publishing.
Windows 原始碼位於 `windows-source-v0.10.0.zip`，使用 `build.ps1` 建置；環境需求與支援物件請見 Windows 說明。GitHub Actions 會測試打包的 EXE，通過才發布。

General Brep solids/surfaces are not supported. Unsupported objects fail with a report instead of silently disappearing. Windows builds are unsigned; Explorer drag-and-drop and notification appearance still need an interactive desktop check.
一般 Brep 實體／曲面尚未支援；遇到不支援物件會失敗並留下報告。Windows 版尚未簽署憑證，桌面拖曳及通知顯示仍需實機確認。

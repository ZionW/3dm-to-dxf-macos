# 3DM → DXF: macOS Guide

[繁體中文](README.zh-TW.md) · [Home](README.md)

## Install and use

1. Download `3DM-to-DXF-macOS-arm64-v0.9.zip` from [Releases](../../releases/latest) and unzip it to get `3DM to DXF.app`.
2. Drag one or more `.3dm` files onto the app icon.
3. The app writes a matching `.dxf` beside each source file. If that name exists, it uses `_1.dxf`, `_2.dxf`, and so on. A macOS notification reports completion or failure.

The app has no main window and does not launch Rhino. It writes DXF directly without a DWG converter or ODA.

## Requirements

- Apple Silicon Mac. The app declares macOS 13 as its minimum version; this build was tested on macOS 27.2 only.
- The app is locally signed but not Apple notarized. If macOS blocks the first launch, Control-click the app in Finder, choose **Open**, and follow the system prompt.

## Conversion scope and limits

The app supports common points, lines, circles, arcs, polylines, NURBS curves, some meshes, hatches, text, representable block references and dimensions, and planar reference pictures. It preserves layer names, colors, visibility, and drawing units. It reads the DXF back after writing and checks source objects and hatch counts. An unsupported object causes that file to fail with a `.conversion-error.txt` report beside the source.

This is not a full Rhino exporter. General Brep solids, specialized materials, and other unsupported objects may fail. Text appearance depends on fonts installed in the receiving CAD app. Layers hidden in the source remain hidden; enable them in the CAD layer manager when needed.

Pictures are external references. When moving a DXF, also move the adjacent `<source-name>_embedded_files` folder. Successful conversions also produce a `.dxf.verification.json` report beside the DXF.

## Privacy

Conversion runs locally; the app does not upload 3DM or DXF files. The GitHub release contains the app only, with no user models.

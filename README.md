# Australis Hex Viewer prototype

## Current status

The executable is packaged under `/System`, but its current source only prints `Hello, World!`. It does not open or display file bytes.

`HexViewer.hyproj` builds `system/hexviewer.exec`. The Australis OS aggregate includes
this project and installs the executable at `/System/hexviewer.exec` in the read-only
HyFS 2 boot image. Run it by its bare name `/System/` through the current
recovery shell's `PATH`, or use `run /System/hexviewer.exec`.

## Planned direction

Implement bounded byte reads, offsets, and hexadecimal output through the checked file API. Do not treat installation as feature completion.

Build this checkout with:

```bash
mkdir -p build
hy build HexViewer.hyproj -o build/hexviewer.exec
```

AUEX `.exec` files currently run in the checked interpreter. Native ring-3
processes and a normal userland shell are later milestones. The boot root is
read-only; writable application data belongs on the separate `/data` volume.
The OS-level build, supported APIs, and packaging rules are described in the
Australis OS `applications/README.md`. This README describes this project's
actual source rather than treating its filename as proof of a finished feature.

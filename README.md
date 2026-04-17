# Orthus

An ergonomic split keyboard PCB designed for Kailh Choc low-profile switches. (Formerly named "OrthusChoc" — renamed now that this is the canonical Orthus variant.)

## Status

**Functionally complete** — just a few finishing touches remaining before release.

## Folder structure

```
Orthus/
├── KiCad/              KiCad project files (Orthus.kicad_pro is the main project)
│   ├── font/           Custom silkscreen font SVGs (0-9)
│   └── backups/        Dated KiCad auto-backups (trimmed to 4 snapshots)
├── Renders/            Project renders and WIP photos
├── 3D/                 .step / .stl / .bin / .gltf — case, keycaps, trackpad models
├── Fabrication/        Trackpad grill cutouts (.dxf / .svg)
├── JLCPCB/             (empty — see "What's missing" below)
└── Components/
    ├── OrthusTrackpad/  Capacitive trackpad PCB (has its own gerbers in JLCPCB/)
    └── OrthusSharp/     Sharp Memory Display breakout (renamed from sharp_memory_display)
```

## Components

- **OrthusTrackpad** — Custom mutual-capacitance trackpad PCB. Self-contained KiCad project with its own JLCPCB gerber folder. Status: complete.
- **OrthusSharp** — A Sharp Memory Display breakout PCB built on top of an open-source sharp_memory_display design but significantly modified. All files renamed from `sharp_memory_display.*` → `OrthusSharp.*`. Original KiCad 5 files preserved under `Legacy/`. Status: complete.
- **OrthusMouseWheel** *(not included here — unfinished)* — Still lives under `Custom/Ergomania/OrthusMouseWheel/`.

## What's missing / potentially missing

- **No gerbers / JLCPCB order files** for the main Orthus PCB. Will need to generate these before fabrication. `JLCPCB/` subfolder is an empty placeholder.
- **No BOM / pick-and-place files** generated for the main PCB yet.
- **No README-level assembly documentation** — schematics are split across Left/Right/LeftMatrix/OLED/led sub-sheets.
- **3D model paths in `Orthus.kicad_pcb`** reference absolute paths to `E:/EverythingKB/Custom/Ergomania/OrthusChoc/OrthusKeycap.step` (the untouched original location). These were intentionally left alone so the 3D view keeps working. When preparing for open-source release, update these paths to reference models inside `Orthus/3D/`.
- **3D model path in `OrthusSharp.kicad_pro`** references `../../Custom/Ergomania/test/OrthusSharp.step` (relative path inherited from the old location) — this may need updating in KiCad.
- **OrthusSharp `fp-lib-table`** has hardcoded macOS paths from the original upstream fork (e.g. `/Users/karnadi/...`). These won't resolve on Windows; regenerate or point to your local KiCad library paths when opening.

## Attribution

`Components/OrthusSharp/` is derived from an open-source Sharp Memory Display breakout (see `Components/OrthusSharp/LICENSE`). It has been heavily modified for integration with Orthus.

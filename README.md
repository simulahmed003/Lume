# Lume

A desktop G-code viewer and editor for PCB milling, built with Python and Qt (PySide6). It is the software side of my work on reviving a CirQoid-style PCB milling machine.

> **Status: early, working foundation.** Import, 3D viewing and editing work today. Simulation, height mapping and live Z adjustment are specified in `docs/features/` but not built yet.

## What works today

- Import one or more `.nc` G-code files into a project (FlatCAM-style headers and footers are preserved).
- Toolpath viewer: OpenGL 3D view (pyqtgraph) with an XY grid and coloured axes (X red, Y green, Z blue).
- G-code text editor. Selecting lines in the editor highlights the matching toolpath segment in the viewer.
- XYZ offset dialog for shifting a job.
- Parser and model layer (`core/`) with a list of supported and unsupported G-codes, and sample drill and mill files in `data/samples/`.

## Planned

Each item has a written spec in [`docs/features/`](docs/features): live simulation, streaming engine, on-the-fly Z adjustment, height mapping, affine alignment, reference-point detection and G-code remapping. [`docs/10_current-implementation.md`](docs/10_current-implementation.md) records exactly what is implemented.

## Run it

```bash
pip install PySide6 pyqtgraph numpy
python main.py
```

Open the sample files in `data/samples/` to try it.

## Layout

| Path | Purpose |
|---|---|
| `app/` | Qt UI: main window, project tree, viewer, editor, offset dialog |
| `core/` | Project model, G-code parser, geometry builder, import pipeline |
| `simulator/` | Early CNC machine simulator |
| `docs/` | Requirements overview, current-state snapshot, per-feature specs |

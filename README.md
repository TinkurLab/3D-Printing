# Tinkurlab's Anycubic Kossel Linear 3D Printer

## Overview

This repo contains code and docs for Tinkurlab's [Anycubic Kossel Linear Plus 3D Printer](https://github.com/TinkurLab/3D-Printing).

## Toolchain

- [Simplify 3D](https://www.simplify3d.com/) 3D slicing and printing
- [Thingiverse 3D](https://www.thingiverse.com/) 3D model sharing
- [TinkerCad 3D](https://www.tinkercad.com/) 3D model creation and editing

## Calibration

Use Simplify 3D's manual Job Controls to lower the print head towards the bed. Lower until first tension occurs when moving a sticky note between the bed and print head. Set as Global G-Code Offset: X-Axis.

## Drivers and Firmware

See https://github.com/TinkurLab/3D-Printing or backups in /drivers in this repo.

## Settings

Important settings in Simplify 3D:

### For 1.75mm diameter PLA

- Extruder Temp: 200F
- Bed Temp 60F
- Extrustion Width: 0.25 or 0.30mm
- First Layer Speed: 30%
- Infill: 15 - 30% depending on project
- Supports: as needed
- Brim: mostly always
- Raft: as needed
- Global G-Code Offset: X-Axis -26.60mm

Also see backups in /settings in this repo.

## Resources

- [GCode Reference](http://reprap.org/wiki/G-code)

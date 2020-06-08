# Tinkurlab's Anycubic Kossel Linear 3D Printer

## Overview

This repo contains code and docs for Tinkurlab's [Anycubic Kossel Linear Plus 3D Printer](https://github.com/TinkurLab/3D-Printing).

## Toolchain

- [Marlin Firmware](https://marlinfw.org/)
- [Simplify 3D](https://www.simplify3d.com/) 3D slicing and printing
- [Thingiverse 3D](https://www.thingiverse.com/) 3D model sharing
- [TinkerCad 3D](https://www.tinkercad.com/) 3D model creation and editing

## Calibration

As of April 2020, all calibration is done in firmware to facilitate a completely "from code" programming and adjustment.

### Updating Firmware

1. Using the https://github.com/TinkurLab/Kossel-Anycubic-Marlin-Firmware repo, update `Configuration.h` and `Configuration_adv.h` as needed. Refer to [Marlin Firmware Configuration](https://marlinfw.org/docs/configuration/configuration.html) as needed.
1. [Upload firmware](https://marlinfw.org/docs/basics/install_arduino.html) changes to printer.
1. After uploading, run a `M502` to reset EEPROM to factory settings, `M500` to save to EEPROM, and `M503` to show current settings in SRAM.
1. Run a test print.

### Height and Geometry Calibration

- Use `G33` to measure Delta geometry and update in firmware as needed.
- Use `M303` to tune PID settings for extruder and `M303 E-1` to tune bed and update in firmware as needed.
- Ensure that @ Z = 0, there is slight tension when sliding a piece of paper between the printer bed and nozzle.

### Thermal Protection Calibration

- Update in firmware as needed. See [Marlin Thermal Protection in Depth](https://jgaurorawiki.com/thermal-runaway).

## Settings

Important settings in Simplify 3D:

### For 1.75mm diameter PLA

- Extruder Temp: 200F
- Bed Temp 60F
- Layer Height: 0.1 to 0.2mm
- First Layer Speed: 30%
- First Layer Height: 150%
- First Layer Width 150%
- Solid Infill Underspeed: 50%
- Infill: 15 - 30% depending on project
- Supports: as needed
- Brim: mostly always, 3x 5mm offset
- Raft: as needed

Also see backups in /settings in this repo.

## Quirks and Known Issues

- Extruder set to 200C will drop to 190C when fan starts. May further drop to 185C or < if doing 100% infill at full speed.

## Resources

- [Anycubic Kossel Product Page](https://www.anycubic.com/products/anycubic-kossel-3d-printer)
- [Anycubic Kossel Wiki](http://www.lpomykal.cz/3d-printers/kossel/)
- [Marlin G-code Reference](https://marlinfw.org/meta/gcode/)
- [Marlin Firmware Configuration](https://marlinfw.org/docs/configuration/configuration.html)
- [Marlin Thermal Protection in Depth](https://jgaurorawiki.com/thermal-runaway)
- [Reprap G-code Reference](http://reprap.org/wiki/G-code)
- [G29 (bed leveling) vs G33 (Delta calibration)](https://hennerley.wordpress.com/2018/01/29/g29-vs-g33/)
- [Delta Calibration 3D model](https://www.thingiverse.com/thing:2256557)

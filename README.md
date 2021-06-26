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

1. Using the https://github.com/TinkurLab/Kossel-Anycubic-Marlin-Firmware repo, update `Configuration.h` and `Configuration_adv.h` as needed. Refer to [Marlin Firmware Configuration](https://marlinfw.org/docs/configuration/configuration.html) as needed. Note: most changes are suffixed with `//Adam` to indicate a change.
1. Compile the code to [upload firmware](https://marlinfw.org/docs/configuration/configuration.html#hardware-info) changes to printer via the Arduino IDE. Settings:

   - Tools > Board > Arduino / Genduino Mega or Mega 2560
   - Port > `dev/cu.SLAB_USBtoUART` or similar
   - Baud Rate > `250000`

1. After uploading, run a `M502` to reset EEPROM to factory settings, `M500` to save to EEPROM, and `M503` to show current settings in SRAM.
1. Run a test print.

### Height and Geometry Calibration

- Attach the leveling proble to the printer and use `G33 V2` to measure Delta geometry. Use the serial connection from the Arduino IDE or Simplify 3D to execute commands. After running `G33 V2`, this will output the new calibration settings via the serial connection. Copy these values and update in firmware as needed (normally `Configuration.h` values for `DELTA_RADIUS`, `DELTA_RADIUS`, `DELTA_HEIGHT`, `DELTA_ENDSTOP_ADJ`, and `DELTA_TOWER_ANGLE_TRIM`).
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

Also see backup settings files in `/settings` in this repo.

## Quirks and Known Issues

- Extruder set to 200C will drop to 190C when fan starts. May further drop to 185C or < if doing 100% infill at full speed. Perhaps a [better thermistor and heating element](https://www.lpomykal.cz/anycubic-kossel-replacement-parts/) would help. Could also further experiment with tweaking print settings.
- Bed is somewhat unevan. I cheat by printing things with the smallest footprint when possible to minimize the bed variation encountered. Could further experiment with getting a better bed surface, better leveling the bed, getting a bed that can be leveled, or using a virtual level grid (via Marlin).

## Resources

- [Anycubic Kossel Product Page](https://www.anycubic.com/products/anycubic-kossel-3d-printer)
- [Anycubic Kossel Wiki](http://www.lpomykal.cz/3d-printers/kossel/)
- [Marlin G-code Reference](https://marlinfw.org/meta/gcode/)
- [Marlin Firmware Configuration](https://marlinfw.org/docs/configuration/configuration.html)
- [Marlin Thermal Protection in Depth](https://jgaurorawiki.com/thermal-runaway)
- [Reprap G-code Reference](http://reprap.org/wiki/G-code)
- [G29 (bed leveling) vs G33 (Delta calibration)](https://hennerley.wordpress.com/2018/01/29/g29-vs-g33/)
- [Delta Calibration 3D model](https://www.thingiverse.com/thing:2256557)

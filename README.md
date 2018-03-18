# Tinkurlab's Anycubic Kossel Linear 3D Printer

## Overview
This repo contains code and docs for Tinkurlab's Anycubic Kossel Linear Plus 3D Printer.

This repo also contains 3D models and printing info that aren't associated with another TinkurLab repo.

## Collaboration

Check out this project's Waffle.io Board!

[![Waffle.io - Columns and their card count](https://badge.waffle.io/TinkurLab/tinkurlab-anycubic-3d-printer.svg?columns=all)](https://waffle.io/TinkurLab/tinkurlab-anycubic-3d-printer)

## Toolchain

### Software
* [Tinkercad](https://www.tinkercad.com/) for 3D modeling
* [Simplify 3D](https://www.simplify3d.com/) for 3D model slicing, supports, and printing
* GitHub for source code and docs
* [Thingiverse](https://www.thingiverse.com/) to find 3D models and host TinkurLab 3D models
* Repetier Host, Mesh Mixer, and other tools for specific needs

### Hardware
*  Anycubic Kossel Linear Plus 3D Printer
*  Hatchbox filament
*  Tweezers, pliers for model removal
*  Micro cutters, sand paper, files for model cleanup post printing
*  Painters tape for bed coverage

## Calibration / Leveling

This procedure should be performaned when any major changes are made to the printer - assembling / disassembling, moving bed, or when the printer is out of level based on print results.

**Prerequisites**
* [Arduino IDE](https://www.arduino.cc/)
* [Repetier Host](https://www.repetier.com/)
* Understanding of using [Repetier Host - Print Panel](https://www.repetier.com/documentation/repetier-host-mac/manual-control/) for manual control

**Steps**
1. Measure center Z for ideal print height
    * Prepare print bed for printing (ex. add tape, glass plate, etc)
    * Home All
    * Move print head to Z10 `G1 Z10`
    * Place a single post it note between the print bed and print head.
    * Decrease print head height as approperiate in -10, -1, or -0.1 increments until unable to move post it note with reasonable effort.
    * Record Z position (ex. -26.29)
1. Measure ideal print height at each of the 3x vertical support posts
    * Home All
    * Move to Z10 `G1 Z10` for safe clearance
    * Move to approperiate post
      * `G0 Y80`
      * `G0 X-70 Y-41`
      * `G0 X70 Y-41`
    * Decrease print head height as approperiate in -10, -1, or -0.1 increments until unable to move post it note with reasonable effort.
    * Record Z position (ex. -26.29)
    * If Z post > Z center (ex. post Z height is -26.49 vs. center -26.29), turn set screw in carriage on post counter clockwise.  1/4 turn = about +0.1mm in Z height.
    * If Z post > Z center (ex. post Z height is -26.09 vs. center -26.29), turn set screw in carriage on post clockwise.  1/4 turn = about -0.1mm in Z height.
    * Repeat this process for a given post until Z post = Z center.  Repeat for all posts.

See https://www.youtube.com/watch?v=5nD6LLx32U0 which is basis for these steps.

## GCode Cheatsheet

Home
`G28`    

Move to X,Y,Z Position
`G0 Y80` move to Y80 slowly
`G0 Y20 X-20` move to Y20 X-20 slowly
`G1 Z10` move to Z10 quickly

Software Endstops Off
`M211 S0`

Fan On 
`M106 S127`

## Resources

* [Repetier Host Mac Docs](https://www.repetier.com/documentation/repetier-host-mac/manual-control/)
* [Slic3r Docs](http://manual.slic3r.org/intro/overview)
* [GCode Reference](http://reprap.org/wiki/G-code)
* Simplify 3D
    - [Video Tutorials](https://www.simplify3d.com/support/videos/)
    - [Written Tutorials](https://www.simplify3d.com/support/articles/)
    - [Print Quality Guide](https://www.simplify3d.com/support/print-quality-troubleshooting/)
    - [Print Material Guide](https://www.simplify3d.com/support/materials-guide/)




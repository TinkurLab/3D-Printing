# Tinkurlab's Anycubic Kossel Linear 3D Printer

## Overview
This repo contains code and docs for Tinkurlab's Anycubic Kossel Linear 3D Printer.

## Collaboration

Check out this project's Waffle.io Board!

[![Waffle.io - Columns and their card count](https://badge.waffle.io/TinkurLab/tinkurlab-anycubic-3d-printer.svg?columns=all)](https://waffle.io/TinkurLab/tinkurlab-anycubic-3d-printer)

## Calibration / Leveling

### Overview

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

## Updating Printer Firmware an Configs

**This is a work in progress and isn't currently complete / working**

* Download desired Marlin firmware version
* In Adrudino IDE
    * Open Marlin.ino
    * Power on printer and configure
        * Board: Arduino Mega
        * Processor: ATmega2560
        * Port: SLAB_USBtoUART
    * Open Serial panel and configure 
        * Speed: 115200 baud
        * Send: NL (new line) and CR (carriage return)
    * Replace configuration.h and configuration_adv.h files in /marlin directory w/ Delta Kossel Pro files from /example directory.
* In Configuration.h
    * `DELTA_HEIGHT=330`
    * `DELTA_RADIUS=100`

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




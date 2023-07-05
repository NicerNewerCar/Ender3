# Ender3

OG Ender 3 running SKR Mini E3 V3 and a Raspberry Pi 3 B+ with Mainsail OS.

## SKR Mini E3 V3 Notes

### Fan pins:

* Fan0 - Part Cooler
* Fan2 - Hot End Fan
* Fan1 - Mainboard

## Firmware Generation

* `cd ~/klipper`
* `make menuconfig`
    * Switch to `STM32G0B1` processor 
    * Set `8KiB bootloader`
    * Ensure USB communication
    * Save it with `q`
* `make`
* On host: `scp pi@ender3:~/klipper/out/klipper.bin /local/on/host/firmware.bin`

## Trouble Shooting + Tips & Tricks

### E-Steps Calib

* Preheat to 210 for PLA
* Messure 100 mm of filament
* Issue `M83` - puts the extruder in relative mode
* Issue `G1 E100 F100` - Slowly extrudes 100mm of filament over 1 min (change `E100` for dif lengths)
* Messure/calculate what was accutally extruded.
* Calculate the new `rotation_distance` with the following formula:
    * `rotation_distance = <prev rotation_distance> * <acutal length extruded> / <requested length>`
* Update the `rotation_distance` parameter under the `[extruder]` section
* Repeat until the extruder is extruding exactly 100mm

### `mcu` unable to connect

* `ls /dev/serial/by-id/*`
* Copy the returned result
* Edit the `[mcu]` section of the `printer.cfg` file.   

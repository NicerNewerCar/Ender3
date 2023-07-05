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

## Trouble Shooting


### `mcu` unable to connect

* `ls /dev/serial/by-id/*`
* Copy the returned result
* Edit the `[mcu]` section of the `printer.cfg` file.   

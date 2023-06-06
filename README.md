# Ender3

## Firmware Generation

* `cd ~/klipper`
* `make menuconfig`
    * Switch to `STM32F103` processor 
    * Enable extra low-level configuration options
    * Set `28KiB bootloader`
    * Configue `GPIO pins to set at micro-controller startup` to `!PA14`
    * Save it
* `make`
* On host: `scp pi@ender3:~/klipper/out/klipper.bin /local/on/host/firmware.bin` 
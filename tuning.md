# Tuning & Stuff

## E-Steps Calib

* Preheat to 210 for PLA
* Messure 100 mm of filament
* Issue `M83` - puts the extruder in relative mode
* Issue `G1 E100 F100` - Slowly extrudes 100mm of filament over 1 min (change `E100` for dif lengths)
* Messure/calculate what was accutally extruded.
* Calculate the new `rotation_distance` with the following formula:
    * `rotation_distance = <prev rotation_distance> * <acutal length extruded> / <requested length>`
* Update the `rotation_distance` parameter under the `[extruder]` section
* Repeat until the extruder is extruding exactly 100mm

## PID Tuning

* `PID_CALIBRATE HEATER=extruder TARGET=210`
* `SAVE_CONFIG`
* `PID_CALIBRATE HEATER=heater_bed TARGET=60` - Usally takes a while since there are no fans for bed
* `SAVE_CONFIG`

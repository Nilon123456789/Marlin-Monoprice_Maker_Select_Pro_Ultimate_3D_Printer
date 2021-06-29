# Cura Settings
First import the cura print settings [file](/Cura/Monoprice_Maker_Select_Pro_Ultimate_3D_Printer.curaprofile) (.curaprofile)

After go to the printer tab and creat a new custom printer
## Printer Settings
  * X(Width) : `200` mm
  * Y(Depth) : `200` mm
  * Z(Height) : `175` mm
  * Build plate shape : `Rectangular`
  * Origin at center : :x:
  * Heated bed : :heavy_check_mark:
  * Heated build volume : :x:
  * G-code flavor : `Marlin`

## Start G-code
```
G21 ;metric values
G90 ;absolute positioning
M82 ;set extruder to absolute mode
M107 ;start with the fan off
G28 X0 Y0 ;move X/Y to min endstops
G28 Z0 ;move Z to min endstops

;prime line
M117 Purgin... ;Put prugin on the LCD
G92 E0 ;zero the extruded length
G1 Z2.0 F3000; move Z up
G1 Y-3.0 Z0.28 F500 ; move out of print volume
G1 X60.0 Z0.28 E9 F500.0 ; start purge line
G1 X100.0 Z0.28 E12.5 F500.0 ; end purge line
G92 E0 ;zero the extruded length again
G1 Z2.0 F3000; move Z up
	
G1 F{speed_travel} 

;Put printing message on LCD screen
M117 Printing...
```

## Printhead Settings
  * X min : `-20` mm
  * Y min : `-10` mm
  * X max : `10` mm
  * Y max : `10` mm
  * Gantry Height : `55.0` mm
  * Number of Extruders : `1`
  * Apply Extruder offsets to GCode : :heavy_check_mark:

## End G-code
```
M104 S0 ;extruder heater off 
G91 ;relative positioning
G1 E-1 F300  ;retract the filament a bit before lifting the nozzle, to release some of the pressure
G1 Z+0.5 E-5 X-20 Y-20 F{speed_travel} ;move Z up a bit and retract filament even more
G28 X0 Y0 ;move X/Y to min endstops, so the head is out of the way
M84 ;steppers off
G90 ;absolute positioning
 ```
## Extruder 1
  * Nozzle size : `0.4` mm
  * Compatible material diameter : `1.75` mm
  * Nozzle offset X : `0` mm
  * Nozzle offset Y : `0` mm
  * Cooling Fan Number : `0`

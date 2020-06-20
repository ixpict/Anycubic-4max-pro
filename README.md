# start g-code

```
G21 ; metric values
G90 ; absolute positioning
M82 ; set extruder to absolute mode
M107 ; start with the fan off
G28 X0 Y0 ; move X/Y to min endstops
G28 Z0 ;move Z to min endstops
G1 Y44 F2000 ; wipe nozzle
G28 X0 Y0 ;  move X/Y to min endstops
G1 Z15.0 F{speed_travel} ; move the platform down 15mm
G92 E0 ; zero the extruded length
G1 F200 E3 ; extrude 3mm of feed stock
G92 E0 ; zero the extruded length again
G1 F{speed_travel}
M117 Printing...
G5
```

# end g-code

```
M104 S0 ; turn off extruder
M140 S0 ; turn off bed
M84 ; disable motors
M107
G91 ; relative positioning
G1 E-1 F300 ; retract the filament a bit before lifting the nozzle, to release some of the pressure
G1 Z+0.5 E-5 ; X-20 Y-20 F{speed_travel} ;move Z up a bit and retract filament even more
G28 X0 ;Y0 ; move X/Y to min endstops, so the head is out of the way
G90 ; absolute positioning
G1 Z200 F2000 ; lower print bed
M84 ; steppers off
M300 P300 S4000
```

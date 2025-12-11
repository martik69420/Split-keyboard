# Split Keyboard – Caldera Remix

Custom split keyboard inspired by Christian Selig’s **Caldera**.  
Two halves, column-staggered layout, **nice!nano + ZMK** firmware.

All images are in `/images`.

---

## Finished Keyboard

Short look at the final build.

![assembled keyboard](/images/assembled.jpg)
![both halves](/images/both_halves.jpg)

---

## CAD / Case

The case is a low-profile shell that holds the PCB, plate, and standoffs.  
I designed it from the Ergogen outlines and exported it to CAD for 3D printing.

![case render](/images/cad_case.png)

---

## PCB

The PCB is generated from the Ergogen config and then cleaned up in KiCad.  
It includes the key matrix, diodes, **nice!nano** footprint, battery connector,  
power switch and reset switch.

![pcb top](/images/pcb_top.png)  
![pcb 3d view](/images/pcb_3d.png)

---

## Schematic

The schematic is split into a matrix section and a power / controller section.  
Each key goes: **switch → diode → row**, with columns going to the MCU pins.  
Power section connects the LiPo, JST jack, power switch, and the nice!nano.

![schematic overview](/images/schematic.png)

---

## Parts List

Main parts used in this build.

![parts layout](/images/parts.jpg)

- **2× nice!nano (or nice!nano v2)**
- **Choc switches** – one per key
- **Keycaps** for Choc switches
- **Diodes** – one per switch (through-hole or SMD)
- **1× LiPo battery** (for each side, if wireless)
- **JST battery connector**
- **Power switch** and **reset switches**
- Screws, standoffs, and 3D-printed case parts

---

## Quick Build Guide

Very short summary of how this project is put together.

1. **Generate layout and PCB**
   - Use Ergogen config in this repo to generate outlines and KiCad files.
   - Import into KiCad, route the board, and export Gerbers.

2. **Order PCBs and parts**
   - Upload Gerbers to a PCB fab.
   - Order the parts from the parts list above.

3. **Solder the PCB**
   - Solder diodes, sockets/switches, JST, power switch, reset, and nice!nano.
   - Check for shorts and continuity on rows and columns.

4. **Flash firmware (ZMK)**
   - This repo includes `zmk-config-caldera` with **caldera_left** and **caldera_right** shields.
   - Example build commands:
     ```sh
     west build -s zmk/app -d build_left -b nice_nano -- \
       -DSHIELD=caldera_left \
       -DZMK_CONFIG=$PWD/zmk-config-caldera/config

     west build -s zmk/app -d build_right -b nice_nano -- \
       -DSHIELD=caldera_right \
       -DZMK_CONFIG=$PWD/zmk-config-caldera/config
     ```
   - Flash `build_left/zephyr/zmk.uf2` and `build_right/zephyr/zmk.uf2` to each half.

5. **Assemble the case**
   - Screw the PCB into the printed case.
   - Plug in the battery and close everything up.

6. **Test and tweak**
   - Pair both halves, test every key.
   - Adjust the keymap in the ZMK config if needed.

---

## Notes

- Images: all stored in `/images`, referenced directly in this README.
- Layout and firmware are based on the original Caldera project but customized for this build.

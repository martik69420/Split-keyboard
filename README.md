# Split Keyboard – Caldera Remix

Custom split keyboard inspired by Christian Selig’s **Caldera**.  
Two halves, column-staggered layout, **nice!nano + ZMK** firmware.

All images are in `/images`.

---

## Credits (Original Inspiration)

This project is heavily inspired by Christian Selig’s Caldera build.  
Original video: [https://www.youtube.com/watch?v=7UXsD7nSfDY]([url](https://www.youtube.com/watch?v=7UXsD7nSfDY))

---

## Ergogen

Here is a look at the key placement and layout generated with Ergogen.

![key placement](/images/ERGOGEN_SWITCHES.png)  
![layout](/images/ERGOGEN_LAYOUT.png)

### Ergogen config
The Ergogen config used for this project is included in this repo.

![Ergogen files](/ergogen) 

---

## PCB (KiCad)

The PCB is generated from the Ergogen config and then cleaned up in KiCad.  
It includes the key matrix, diodes, **nice!nano** footprint, battery connector,  
power switch, and reset switch.

![Unfinished left side PCB](/images/LEFT_PCB_UNFINISHED.png)  
![Finished left side PCB](/images/LEFT_PCB_FINISHED.png)

![Unfinished right side PCB](/images/RIGHT_PCB_UNFINISHED.png)  
![Finished right side PCB](/images/RIGHT_PCB_FINISHED.png)

---

## Schematic

Complete schematic showing matrix wiring, controller connections, and power section.

![schematic](/images/SCHEMATIC.png)

---

## CAD / Case

The case is a low-profile shell that holds the PCB, plate, and standoffs.  
Designed from the Ergogen outlines and exported to CAD for 3D printing.

![case](/images/case.png)

---

## Parts List

Main parts used in this build.

![parts layout 1](/images/materials1.png)  
![parts layout 2](/images/materials2.png)  
![parts layout 3](/images/materials3.png)  
![battery](/images/lithium_battery.png)

- **2× nice!nano (or nice!nano v2)**
- **Choc switches** – one per key
- **Keycaps** for Choc switches
- **Diodes** – one per switch (through-hole or SMD)
- **LiPo battery** (per side if wireless)
- **JST battery connector**
- **Power switch** and **reset switches**

All materials from
   [https://typeractive.xyz/]([url](https://typeractive.xyz/))
except the lithium ion battery
   [https://nl.aliexpress.com/item/1005005213892382.html?spm=a2g0o.cart.0.0.23e061d7xbi5uM&mp=1&pdp_npi=5%40dis%21EUR%21EUR%2014.09%21EUR%204.68%21%21EUR%204.68%21%21%21%40211b655217656172436378542e3ce8%2112000033329836828%21ct%21BE%21-1%21%211%210&gatewayAdapt=glo2nld](https://nl.aliexpress.com/item/1005005213892382.html?spm=a2g0o.cart.0.0.23e061d7xbi5uM&mp=1&pdp_npi=5%40dis%21EUR%21EUR%2014.09%21EUR%204.68%21%21EUR%204.68%21%21%21%40211b655217656172436378542e3ce8%2112000033329836828%21ct%21BE%21-1%21%211%210&gatewayAdapt=glo2nld)
---

## Full Build Walkthrough

### 1. Ergogen → Layout and Outlines
1. Open the Ergogen config file in this repo.
2. Adjust key spacing, stagger, and outline.
3. Generate switch positions and board outline.
4. Export DXF files for PCB and CAD usage.

---

### 2. Ergogen → KiCad Setup
1. Create a KiCad PCB project.
2. Import the Ergogen DXF outline into **Edge.Cuts**.
3. Place footprints for:
   - Choc switches / hotswap sockets
   - Diodes
   - nice!nano
   - Battery connector
   - Power and reset switches

---

### 3. KiCad Routing
1. Define row and column nets.
2. Route switch → diode → row.
3. Route column lines to the controller.
4. Add mounting holes and silkscreen.
5. Run DRC until no errors remain.

---

### 4. Gerbers and PCB Order
1. Export Gerber files from KiCad.
2. Upload to a PCB manufacturer.
3. Order the required number of boards.

---

### 5. Assembly and Soldering
Recommended solder order:
1. Diodes  
2. Hotswap sockets or switches  
3. JST battery connector  
4. Power and reset switches  
5. nice!nano headers or sockets  

Verify continuity and check for shorts.

---

### 6. Firmware (ZMK)

ZMK configuration is included in `zmk-config-caldera`.

Shields:
- **caldera_left**
- **caldera_right**

Build commands:

```sh
west build -s zmk/app -d build_left -b nice_nano -- \
  -DSHIELD=caldera_left \
  -DZMK_CONFIG=$PWD/zmk-config-caldera/config

west build -s zmk/app -d build_right -b nice_nano -- \
  -DSHIELD=caldera_right \
  -DZMK_CONFIG=$PWD/zmk-config-caldera/config

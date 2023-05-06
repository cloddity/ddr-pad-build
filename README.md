# DDR Pad Build
*Last Updated: 09-14-22*

**Progress: Complete**

--

Video Preview:
* https://drive.google.com/file/d/1P_XRcj81ezTKjtoF2oQaf90bWCNSWTdR/view?usp=share_link
![enter image description here](https://i.imgur.com/nr7AmzJ.png)

## Introduction

Last summer, my friends and I set out to build our own DDR (Dance Dance Revolution) pad. We were motivated by our mutual love for rhythm games and wanted to create an inexpensive yet sturdy pad that could endure long hours of gameplay. During the initial planning, we iterated through various ideas until we settled on a design that was fairly easy to assemble and maintain.

While our goal was to emulate the arcade experience at home, we primarily wanted to challenge ourselves by tackling a project that brought our skills together to create something fun. We hope that it will encourage more people to get into rhythm games, or at the least, inspire people to try their hand at a craft.

![](https://i.imgur.com/zRv2hFl.jpg)  
![Initial planning documents](https://i.imgur.com/Y11E0Yj.jpg)
## Materials

- FSR mod kit [FSRs, microcontroller, jumper wires, resistors, breadboard, case, micro USB cable] $60 ($55 + $5 shipping) [https://ddrpad.com/collections/diy-pad-parts/products/fsr-mod-kit] 
- Polycarbonate panels $65 ($13/panel [11x11", 1/4" thickness] + $10 shipping) [https://www.tapplastics.com/product/plastics/cut_to_size_plastic/polycarbonate_sheets/516]
- Velcro tape $12 (26ft x 2in) [https://www.amazon.com/dp/B08KP577YY]
- Gorilla wood glue $5 (8 oz) [https://www.amazon.com/Gorilla-Wood-Glue-ounce-Bottle/dp/B001E4E3KY/]
-  Duct tape 
- Scrap plywood/MDF
	- 36" by 36" x 3/4" for the base
	- 36" by 24" x 3/4" for structural support
- Hardboard
	- 24" by 48" x 1/4" for panel covering


## Tools
- Clamps
- Power jig/miter saw
- Soldering iron
- Tape measure
- Pencil

# Building the Pad
## Base

1. Cut the MDF into four 11"x11" squares and one 10"x10" square. These will be used to add support for the corner panels.
2. Add grooves to the edges of the center panel. These will house the wiring components and hide the FSR contact points.
3. Cut one of the corner panels into two triangles. This will allow the wires to be routed from the center panel to a microcontroller, located at the top-left corner of the pad.
4. Apply wood glue to the corner panels, spacing them 1.5" from the corners of the plywood base (11" apart from each other). Then, apply wood glue to the center panel. Add clamps where necessary to ensure a tight bond.
5. Cut the hardboard into five 11"x11" squares. Set these aside until wiring is complete.

![enter image description here](https://i.imgur.com/LPpu2RX.jpg)

## Sensors
1. Place the force-sensitive resistors (FSRs) towards the center of each panel (location may vary based on desired minimum sensitivity, thresholds may be adjusted later on during programming). If using more than one FSR per panel, wire them in series.
2. Secure the sensors in place with tape, then cut eight 22-gauge jumper wires to connect the microcontroller to both ends of each sensor. Excess wire may be wrapped around the middle panel or tucked inside the case.
3. Cut 20 square pieces of velcro, then place four pieces equidistant from each other in the space between the panels. These will hold the polycarbonate panels in place while allowing some freedom of movement.
4. Attach the remaining four velcro pieces on the polycarbonate panels, ensuring that each piece lines up with the location of each FSR when the panels are placed down. Make sure to keep the plastic film on one side of the velcro so that it doesn't stick to the FSRs.

![enter image description here](https://i.imgur.com/SCcwuS6.jpg)
## Wiring
1. Use a soldering iron to solder tabs to the microcontroller, then slot the microcontroller into the breadboard.
2. Connect VCC to (+) and GND to (-) on their respective power rails. 
3. Bridge four 330 ohm resistors from A0, A1, A2, A3 to GND.
4. Guide the FSR jumper wires through the case, then connect the right pins to GND and the left pins to A0, A1, A2, A3 via the terminal strips. Ensure that the pins are correctly matched or it will result in negative resistance values when a force is applied to the sensor.
5. (optional) If using the case buttons, wire one pin to GND and the other to any available slot in the microcontroller. 
6. Push firmware to the microcontroller after installing the prerequisites outlined in [teejusb's FSR guide](https://github.com/teejusb/fsr/blob/master/README.md "README.md"). Modify the SensorState array to include the case buttons if utilized.


![enter image description here](https://i.imgur.com/yqpmTn9.jpg)
## Panels
1. Make sure that the sensors are registering values to confirm that there are no wiring issues before installing the panels.
2. Stick the polycarbonate panels adjacent to the center panel, ensuring that the velcro lines up with the FSRs.
3. Apply wood glue on the hardboard panels, then clamp them down on top of the MDF panels. Take extra care to align them properly. These will hide the wires, and provide enough height to be level with the polycarbonate panels.
4. Allow some time for the glue to dry before testing out the pad.

## Software
1. Using the React web app, adjust the FSR thresholds. The ideal threshold would be high enough such that the FSRs are not being activated when the panels are not stepped on, yet sensitive enough to register light taps.
2. Download Stepmania, then go to `Settings > Config Key/Joy Mappings`. Apply these settings to map the pad buttons to their respective keys.
![enter image description here](https://i.imgur.com/C6eNRz7.png)
3. Then, go to `Settings > Input Options > Calibrate Audio Sync` to minimize input latency.

# Special Thanks
This project could not have been possible without [teejusb](https://github.com/teejusb/fsr/blob/master/README.md), who developed most of the code involved in interfacing the microcontroller, in addition to [azirixx's easy travel pad build](https://github.com/azirixx/easy-travel-pad-build), which inspired the foundation for our project.

Many thanks to the Stamina Nation community members for their knowledge and support!

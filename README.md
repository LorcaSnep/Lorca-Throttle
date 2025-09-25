## Overview:
To begin, this repository serves as an archive of my work relating to this project for the purposes of my university studies.  All items in this repository are work in progress and are NOT finalized.

The DCC-EX project represents a remarkable achievement for model railroading.  For approximately 50 USD, it is possible to build a fully functioning, JMRI compatible DCC command station.  However, one key element is not ideal; throttles.  Some excellent options do exist such as the TCS UWT series throttles and the LoDi-Con throttle.  To be clear, these are excellent devices that are thoughtfully built by extremely talented people.  However, these, and most off the-shelf throttles, are quite expensive.  This is where this project comes into play.  I began this project with two simple goals.  Design a wireless Throttle for 100 USD or less, and to design it as compact and ergonomic as possible.

This device is based on the ESP32-WROOM-32E microprocessor on a custom designed pair of boards running the WiTcontroller code (https://github.com/flash62au/WiTcontroller) written by Peter Akers.  Having used a throttle based on this code for approximately 1 year, it has proven to be quite reliable and has a wide feature set that I appreciate including integration with JMRI rosters, function lists, and accessory decoder lists.

As of 9/21/25, the electronics are nearly finalized.  Each aspect of them is functioning and I am waiting on the delivery of version 3.2 of the PCBs and the 3D printed case components.  This should conclude the prototype phase for the PCBs.  The one aspect of the PCBs that will not be populated and will be left for a future version is the hardware for a charging dock based on pogo pins.

## Images
Prototype V3.1 running on battery power connected to my personal JMRI Withrottle server:

![Error](https://github.com/LorcaSnep/Lorca-Throttle/blob/main/Images/Lorca%20Throttle%20V3.1.jpg)

Current 3D design of the entire device:

![Error](https://github.com/LorcaSnep/Lorca-Throttle/blob/main/Images/Lorca%20Throttle%20V3.2%20Front.PNG)

![Error](https://github.com/LorcaSnep/Lorca-Throttle/blob/main/Images/Lorca%20Throttle%20V3.2%20Back.PNG)

![Error](https://github.com/LorcaSnep/Lorca-Throttle/blob/main/Images/Lorca%20Throttle%20V3.2%20Bottom.PNG)

## Build Instructions:
Once all of the parts have arrived, assemble the boards according to the component designators as listed in the Bill of Materials file.  I recommend ordering stencils with the boards and using hot plate soldering with solder paste to assemble them. Once the boards are assembled, it is a good time to upload the code to them.  For the most part, follow the steps as laid out in the original WiTcontroller instructions.  However the following changes need to be made in the config_buttons.h file:<br>
-Swap the keypad column pins to {4, 26, 2} (Ensure the code is set for the 4x3 keypad and not the 4x4 one)<br>
Ensure that the rotary encoder sections refering to Small ESP32 are defined and make the following changes:<br>
-Rotary Encoder A Pin 14<br>
-Rotary Encoder B Pin 27<br>
-Rotary Encoder Button Pin 23<br>
Once the code is uploaded to the boards and is functioning, proceed with the build.  Place the 13 keys, and the charge LED insert in the top case piece and place the board assembly in the top case. Next, place the display module in its slot at the top of the device. Place the battery on the back of the display and place the retainer bracket above these pieces.  fasten the entire assembly together with 3 m2x6 screws in the retainer bracket.  Next plug in the battery and the display capbles to the PCB board assembly.  Place the sliding power switch in its appropriate slot, and place the back cover on the device.  Fasten the back cover in place with 6 m2x8 screws and this concludes the build of the throttle!

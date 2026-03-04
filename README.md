# Lorca Throttle
## Overview:
To begin, this repository serves as an archive of my work relating to this project for the purposes of my university studies.  All items in this repository are work in progress and are NOT finalized.

The DCC-EX project represents a remarkable achievement for model railroading.  For approximately 50 USD, it is possible to build a fully functioning, JMRI compatible DCC command station.  However, one key element is not ideal; throttles.  Some excellent options do exist such as the TCS UWT series throttles and the LoDi-Con throttle.  To be clear, these are excellent devices that are thoughtfully built by extremely talented people.  However, these, and most off the-shelf throttles, are quite expensive.  This is where this project comes into play.  I began this project with two simple goals.  Design a wireless Throttle for 100 USD or less, and to design it as compact and ergonomic as possible.

This device is based on the ESP32-WROOM-32E microprocessor on a custom designed pair of boards running the WiTcontroller code (https://github.com/flash62au/WiTcontroller) written by Peter Akers.  Having used a throttle based on this code for approximately 1 year, it has proven to be quite reliable and has a wide feature set that I appreciate including integration with JMRI rosters, function lists, and accessory decoder lists.

## Current Status:
As of 3/1/26, I am awaiting delivery of parts for V4.2 of the PCBs.  This is a very small iteration on V4.1 with no significant design changes.  The placement of some components has been altered and the decoupling on several components has been tweaked to be more resiliant.  Changes in the case have allowed for a significant increase in battery capacity to 1100mAh.  This has not been tested yet but I have calculated that this should result in an approximately 10 hour battery life.  There have been major changes to the case hardware.  I have switched from resin printed components via JLC to extrusion printed ones from a Bambu Lab H2C.  These components are nearly finalized but the settings and configuration of the printer need to be further tweaked.  Switching to extrusion printing has also allowed for multifilament printing to inset white symbols on the keys as opposed to the recessed symbols of the resin keys.  The light diffuser above the charge LED indicator is also printed in this fashion.  Utilizing plastic has also allowed me to use heat set inserts for the screws.  This allows me to use machine thread screws as opposed to self tapping screws which will be considerably more durable.  The next step is to switch from PLA to ABS filament.  This will result in stronger prints.  I am also developing a modification to the keys which would have them printed with a TPU "gasket" that connects all 13 keys together and has anchor points to the case.  This should significantly reduce the amount of key rattle that the design currently has.  Another major development has occured in the software aspect of this project.  A friend in a computer science major at my university has assisted me in coding a firmware flashing application specifically for this project.  It allows the user to configure the device language, WiFi credentials, IP configuration, and roster settings before flashing the firmware with these settings to the device.  This eliminates the need to modify the code from the source project which makes the process much more smooth.  This application is coded so it can be run on Windows, Mac and Linux.  Aside from the firmware flashing application, I have gotten to the point where all of the design changes are very minor.  As such, V4.2 should be the final prototype version of this device.  Once a version 4.2 throttle has been built with the ABS parts and tested, this will represent the first iteration of this project that I am ready to call a production design.

## Images:
Prototype V4.1 running on battery power connected to my personal JMRI Withrottle server (Note: The colors and the materials of the device are not finalized): 

<p align="center">

![Error](https://github.com/LorcaSnep/Lorca-Throttle/blob/main/Images/Lorca%20Throttle%20V4.2.jpg)

Current 3D design of the entire device:

![Error](https://github.com/LorcaSnep/Lorca-Throttle/blob/main/Images/Lorca%20Throttle%20V4.2%20Front.PNG)

![Error](https://github.com/LorcaSnep/Lorca-Throttle/blob/main/Images/Lorca%20Throttle%20V4.2%20Back.PNG)

![Error](https://github.com/LorcaSnep/Lorca-Throttle/blob/main/Images/Lorca%20Throttle%20V4.2%20Bottom.PNG)

</p>

## Build Instructions:
Once all of the parts have arrived, assemble the boards according to the component designators as listed in the Bill of Materials file.  I recommend ordering stencils with the boards and using hot plate soldering with solder paste to assemble them. Once the boards are assembled, it is a good time to upload the code to them.  For the most part, follow the steps as laid out in the original WiTcontroller instructions.  However the following changes need to be made in the config_buttons.h file:<br>
-Swap the keypad column pins to {4, 26, 2} (Ensure the code is set for the 4x3 keypad and not the 4x4 one)<br>
-Set Encoder Rotation to "Clockwise is increase speed"<br>
-Set Rotary Encoder debounce time to 200.<br>
-Define speed step as 1.<br>
To ensure that the throttle displays the JMRI function definitions instead of the throttle defined ones, the following changes need to be made:<br>
-Ensure the lines defining the names of funcitons 0 - 9 are defined as Function_0 through Function_9.<br>
-Set "#define HASH_SHOWS_FUNCTIONS_INSTEAD_OF_KEY_DEFS" as true.<br>
Ensure that the rotary encoder sections refering to Small ESP32 are defined and make the following changes:<br>
-Rotary Encoder A Pin 14<br>
-Rotary Encoder B Pin 27<br>
-Rotary Encoder Button Pin 23<br>
The following changes need to be made for battery percentages:<br>
#define USE_BATTERY_TEST true<br>
#define BATTERY_TEST_PIN 34<br>
#define BATTERY_CONVERSION_FACTOR 2<br>
#define USE_BATTERY_PERCENT_AS_WELL_AS_ICON true<br>
#define USE_BATTERY_SLEEP_AT_PERCENT 0<br>
These changes also need to be made in the "Pangodream_18650_CL.h" file.<br>

Once the code is uploaded to the boards and is functioning, proceed with the build.  Place the 13 keys, the throttle shaft, and the charge LED insert in the top case piece and place the board assembly in the top case. Next, place the display module in its slot at the top of the device. Place the battery on the back of the display and place the retainer bracket above these pieces.  fasten the entire assembly together with 3 m2x6 screws in the retainer bracket.  Next plug in the battery and the display capbles to the PCB board assembly.  Place the sliding power switch in its appropriate slot, and place the back cover on the device.  Fasten the back cover in place with 6 m2x8 screws and place the throttle knob on the shaft.  This concludes the build of the throttle!

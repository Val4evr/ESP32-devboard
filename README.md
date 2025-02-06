# ESP32-devboard

I made this ESP-32 Development board to learn KiCad. It is heavilly based on the [ESP32-DevKit C](https://www.espressif.com/en/products/devkits/esp32-devkitc/resources) reference implementation, but with the redundant micro USB port replaced with USB-C. Here's a ray-traced KiCad render:

![Ray-traced render of the assembled Devboard](https://github.com/Val4evr/ESP32-devboard/blob/main/images/Screenshot%202025-02-06%20at%2021.50.01.png)

# Usage
This repo comes with the footprints, 3D models and everything needed to reproduce the renders. Also, this KiCad project uses the [KiKit](https://github.com/yaqwsx/KiKit) extension to create the below panelization in a format compatible with the [JLCPCB PCBA service](https://jlcpcb.com/smt-assembly). 

![Ray-traced render of the assembled Devboards, panelized](https://github.com/Val4evr/ESP32-devboard/blob/main/images/Screenshot%202025-02-06%20at%2021.54.52.png)

The resultant production files are [here](https://github.com/Val4evr/ESP32-devboard/blob/main/ESP32_panelized_outputgerbers.zip). If you want to edit the design you will have to re-create the panel and gerbers for production:
1. [Setup KiKit](https://yaqwsx.github.io/KiKit/latest/installation/intro/)
2. Open an empty KiCad pcbnew instance
3. Click on the KiKit icon to open the GUI.
4. Select the updated pcb design and output directory (I used `/panelized`) 
5. Import my KiKit [JSON config](https://github.com/Val4evr/ESP32-devboard/blob/main/panelized/kikit_config.json)
6. Panelize!

If you then decide it's good enough for production, run the following snippet to get the gerbers, specifying the path to the panel. 
```
kikit fab jlcpcb --nametemplate "ESP32_panelized_output{}" --no-drc --assembly --schematic <path to schematic file> <path to PCB file> <path to output directory>
```

This will produce gerber, drill and position files for JLC PCB. 


# Previous revisions:
The PCB did not work on first try because of two misconfigured 0ohm DNP resistors on the USB serial traces. As a result I had to solder two strands of solder wick directly to the serial converter chip and ESP32, and hold them in place with copious quantities of tape. 

![All Photos - 1 of 1](https://github.com/user-attachments/assets/7416f65e-95c5-46c8-ad93-dc7a47cd84b9)


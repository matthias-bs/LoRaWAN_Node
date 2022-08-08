# LoRaWAN_Node

Please refer to my [BresserWeatherSensorTTN](https://github.com/matthias-bs/BresserWeatherSensorTTN) project for an example application. The hardware has some options for a variety of other uses, however.

## TTN Node Board

### Schematic
Please refer to Fritzing or PDF file for most current version!

![ttn_node-20220614-2_sch](https://user-images.githubusercontent.com/83612361/183265248-27ff49f0-91a8-427f-959b-108c1d9e68b8.png)

### PCB
Please refer to Fritzing or PDF file for most current version!

**Note:**

Actually an antenna should not be placed next to circuitry or metal parts, but the decision was made to place the antenna inside the case to avoid leakage or corrosion problems. The concept works perfectly for me. 

![ttn_node_v3_pcb](https://user-images.githubusercontent.com/83612361/183265170-01bee6f2-5752-422e-a078-0f699fb1699f.png)

![LoRaWAN_Node-1](https://user-images.githubusercontent.com/83612361/183265799-35a17795-5f3f-4d37-867a-c85cc667befa.jpg)

![LoRaWAN_Node-2](https://user-images.githubusercontent.com/83612361/183265817-2f7a1a1e-1e9d-4e9b-a29a-9f60a6a3cc44.jpg)

### Connectors/Wiring
![ttn_node_wiring](https://user-images.githubusercontent.com/83612361/183265340-02fee7d6-5dc1-46e7-92a9-3ebd7063b362.png)

![LoRaWAN_Node-3](https://user-images.githubusercontent.com/83612361/183265830-def8cbac-5eb0-4b49-8697-ba42429444d9.jpg)

![LoRaWAN_Node-4](https://user-images.githubusercontent.com/83612361/183265832-7b003ffb-fc45-4e7e-966a-1e0f9eb263e6.jpg)

### Issues and Workarounds
1. The mounting holes are too small for the selected screws (special form; SHR Z B4,5x7,8)<br>(Fritzing limitation)<br>Workaround: Drilling with 4.5mm or a little filing.
2. The cutouts at the lower corners of the PCB have to be done manually<br>(apparently Fritzing does not support PCB cutouts)
3. The footprint for the fuse F1 is too narror.<br>As a workaround, F1 can be placed instead of connector J6 and a pin header at the actual F1 pads can be used to connect the fuse in series to the battery B+ wire. (see photo)
4. Connection from battery B+ to analog input voltage divider is missing.<br>Workaround: Add a wire from B+ to J5.7 (A3) (see photo - white wire)

## Main Components
### MCU Board
[DFRobot FireBeetle ESP32 IoT Microcontroller](https://www.dfrobot.com/product-1590.html)

**Note 1:** Assemble R10 and R11 with 0 Ohms resistors (or solder joints...) if you want to monitor VB.

**Note 2:** The USB-serial-converter seems to be quite picky - use a short USB cable and lower bitrate when flashing!

### LoRa Radio Transceiver
[Adafruit RFM95W LoRa Radio Transceiver Breakout](https://www.adafruit.com/product/3072) - **868 MHz Version!**

** Note:** Don't use the transceiver without antenna!

### Antenna
[Delock LoRa 868 MHz Antenna SMA plug 3 dBi omnidirectional](https://www.delock.de/produkt/89769/merkmale.html)

## Solar Battery Charger
[Adafruit Universal USB / DC / Solar Lithium Ion/Polymer charger - bq24074](https://www.adafruit.com/product/4755)

## Solar Panel
[Solar Panel (6V 5W)](https://www.waveshare.com/solar-panel-6v-5w.htm)


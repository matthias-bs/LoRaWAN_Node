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

#### Internal Wiring
```
                           (1)    Fuse
                      + o--------< F1 >-----< +
              BATT1                             U2 (Charger), "Batt"
                      - o-------------------< -
                                 (2)


                      + >-------------------< +
U2 (Charger), "Load"                            U1 (ESP32_Firebeetle)
                      - >-------------------< -
```
Wires (1) and (2) are only needed if the battery holder does not have PCB pins.

#### Connector Wiring
```
                                
                     Power  2 >------------------< +
     Solar Power In                                   2.1mm DC Jack (U2, Charger)
                       GND  1 >------------------< -


                       GND  1 >----------------< 1  GND
     OneWire Socket    VDD  2 >----------------< 2  3V3   LoRaWAN_Node, J2
                       DQ   3 >----------------< 3  DQ
```

![ttn_node_wiring](https://user-images.githubusercontent.com/83612361/183265340-02fee7d6-5dc1-46e7-92a9-3ebd7063b362.png)

![LoRaWAN_Node-3](https://user-images.githubusercontent.com/83612361/183265830-def8cbac-5eb0-4b49-8697-ba42429444d9.jpg)

![LoRaWAN_Node-4](https://user-images.githubusercontent.com/83612361/183265832-7b003ffb-fc45-4e7e-966a-1e0f9eb263e6.jpg)


### Assembly Options
1. Do not assemble R42, R43, R44 and R55.
2. Assemble C40, R40 and R41 for battery voltage measurement.
3. Assemble R1 if a one-wire sensor is to be used (and this sensor does not have an internal pull-up).
4. Assemble R2 and R3 for connection of I<sup>2</sup>C devices.
5. No pin header has to be assembled for the charger module. The apparently missing connections on the PCB drawing to the module can be ignored.

### Issues and Workarounds
1. The mounting holes are too small for the selected screws (special form; SHR Z B4,5x7,8)<sup>(1)</sup><br>(Fritzing limitation)<br>Workaround: Drilling with 4.5mm or a little filing.
2. The cutouts at the lower corners of the PCB have to be done manually.<br>(apparently Fritzing does not support PCB cutouts)
3. The footprint for the fuse F1 is too narror.<br>As a workaround, F1 can be placed instead of connector J6 and a pin header at the actual F1 pads can be used to connect the fuse in series to the battery B+ wire. (see photo)
4. Connection from battery B+ to analog input voltage divider is missing.<br>Workaround: Add a wire from B+ to J5.7 (A3) (see photo - white wire)
5. Optionally: Drill a hole to strap the battery in the holder. (see photo)

(1) The screws on the photo are different ones.

## Main Components
### MCU Board
[DFRobot FireBeetle ESP32 IoT Microcontroller](https://www.dfrobot.com/product-1590.html)

**Note 1:** Assemble R10 and R11 with 0 Ohms resistors (or solder joints...) if you want to monitor VB.

**Note 2:** The USB-serial-converter seems to be quite picky - use a short USB cable and lower bitrate when flashing!

### LoRa Radio Transceiver
[Adafruit RFM95W LoRa Radio Transceiver Breakout](https://www.adafruit.com/product/3072) - **868 MHz Version!**

**Note:** Don't use the transceiver without antenna!

### Antenna
[Delock LoRa 868 MHz Antenna SMA plug 3 dBi omnidirectional](https://www.delock.de/produkt/89769/merkmale.html)

## Solar Battery Charger
[Adafruit Universal USB / DC / Solar Lithium Ion/Polymer charger - bq24074](https://www.adafruit.com/product/4755)

**Note:** "Load Out" voltage can be different from battery voltage in certain conditions - see [Adafruit Universal USB / DC / Solar Lithium Ion/Polymer charger - bq24074 -- Overview](https://learn.adafruit.com/adafruit-bq24074-universal-usb-dc-solar-charger-breakout/overview).

## Solar Panel
[Solar Panel (6V 5W)](https://www.waveshare.com/solar-panel-6v-5w.htm)


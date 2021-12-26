# wled-controller
A small ESP8266 controller with step-down for use with [WLED](https://github.com/Aircoookie/WLED) firmware made with KICAD 6

![wled-controller](https://github.com/3komma3volt/wled-controller/blob/main/images/wledController.png)

# Intro
This board was designed for a christmas lightshow and 17 of them were used. They were supplied from a central 24V power supply and the supply was chained from prop to prop. This made wireing very easy. 
The included 5V regulator supplies up to 5A which is pretty enough for some light props.
The [KICAD](https://www.kicad.org) files include LCSC component numbers for direct ordering at [JLCPCB](https://jlcpcb.com)

![wled-desc](https://github.com/3komma3volt/wled-controller/blob/main/images/description.png)

# Usage
First decide if you want to use the voltage regulator. In some cases, you need more power and then you can remove/not populate the U4 regulator and solder the 5V_Bridge1 on the board. Then the VIN supply must not more than 12V!
With the brige, the voltage on the screw terminals is the same than VIN. So you could use 12V pixels whith this board or a powerful 5V supply. The ESP is supplied from an other voltage regulator.
Without brige, the voltage regulator has to be mounted. Use following fusing for F1:
- 24V input: 1.3A
- 5V or 12V input (with bridge and no U4 mounted): 5A or greater, accordingly to your used power supply / or pixels
An OLED can be mounted but have to be defined in the firmware
A MOSFET can be populated and switch some small loads (connected to J3) and have to be defined in firmware


## Programming
For programming an USB to UART converter is needed. Use following steps:
- EITHER supply from VIN or supply 3.3V to J2 (e.g. from an USB/UART converter)
- Connect GND, RX, TX from the USB/UART to J2
- Press and hold PG, press and release RS, release RS. The EPS should now be in programming mode
- Program accordingly WLED manual and press RS after programming. Now the board should open an AP

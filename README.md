\# STM32F4 Mixed-Signal Interface Board



A 4-layer STM32F4-based mixed-signal interface PCB designed in Altium Designer as a proof-of-concept embedded hardware project. The board integrates USB input power, 3.3 V regulation, SWD programming/debug access, an MPU-6050 IMU interface, external expansion I/O, ESD/TVS protection, decoupling, and fabrication-ready design outputs.



This project was created to practice the end-to-end PCB design workflow: schematic capture, component selection, footprint integration, PCB layout, design rule checking, fabrication output generation, and technical documentation.



\## Project Goals



The goal of this board was to design a compact embedded electronics platform that exercises several common hardware design areas:



\* MCU-based schematic and PCB design

\* USB input power and 3.3 V regulation

\* External connector ESD protection

\* Sensor/IMU interface design

\* SWD programming/debug access

\* Local decoupling and power distribution

\* 4-layer PCB layout workflow

\* DRC cleanup and fabrication file generation

\* Documentation for review and future bring-up



\## Features



\* \*\*Microcontroller:\*\* STM32F411CEU6

\* \*\*IMU:\*\* MPU-6050 inertial measurement unit over I2C

\* \*\*Power Input:\*\* USB VBUS input

\* \*\*Regulation:\*\* AMS1117-3.3 LDO regulator for 3.3 V rail generation

\* \*\*USB Protection:\*\* TVS diode from VBUS to GND near the USB connector

\* \*\*Expansion Connector Protection:\*\* D1213A-04S-7 4-channel ESD array on PA4–PA7

\* \*\*Debug Interface:\*\* TC2030-IDC-NL Tag-Connect SWD programming/debug connector

\* \*\*Clocking:\*\* 24 MHz external crystal

\* \*\*User Indicator:\*\* Power/status LED

\* \*\*PCB:\*\* 4-layer board layout in Altium Designer

\* \*\*Outputs:\*\* Schematic PDF, fabrication outputs, BOM, and DRC report



\## Hardware Overview



\### USB Power Input and Regulation



The board receives power through the USB connector. VBUS is protected using a TVS diode placed near the connector, filtered through a ferrite bead, and regulated down to 3.3 V using an AMS1117-3.3 LDO regulator. Input and output capacitors are included for filtering and regulator stability.



\### STM32F4 Microcontroller



The STM32F411CEU6 serves as the main controller. The design includes local decoupling capacitors, boot/reset circuitry, SWD programming/debug access, USB data connections, and exposed expansion signals.



\### External Expansion Connector



The SM06B-GHS-TB connector exposes 3.3 V, GND, and four MCU signals:



| Connector Pin | Net     |

| ------------: | ------- |

|             1 | +3V3    |

|             2 | MCU\_PA4 |

|             3 | MCU\_PA5 |

|             4 | MCU\_PA6 |

|             5 | MCU\_PA7 |

|             6 | GND     |



The PA4–PA7 lines are protected using a D1213A-04S-7 4-channel ESD diode array placed near the connector.



\### IMU Interface



The MPU-6050 is connected over I2C with pull-up resistors on the SDA and SCL lines. Local support capacitors are placed near the device supply, REGOUT, and CPOUT pins.



\### SWD Debug Interface



A TC2030-IDC-NL Tag-Connect footprint is included for SWD programming and debug access. The connector exposes SWDIO, SWCLK, NRST, SWO, 3.3 V, and GND.



\## PCB Layout Notes



This board was laid out as a 4-layer PCB. During layout, attention was given to:



\* Keeping ESD/TVS protection close to external connectors

\* Placing decoupling capacitors close to MCU and IMU supply pins

\* Routing USB D+ and D− cleanly from the USB connector to the MCU

\* Managing power and ground polygons across layers

\* Creating local design-rule exceptions for fine-pitch footprint clearances

\* Resolving routing, via, keepout, polygon, and DRC issues during layout



\## Design Rule Check Status



At the time of export:



\* Electrical clearance violations: resolved

\* Short-circuit violations: resolved

\* Unrouted nets: resolved

\* Width violations: resolved

\* Hole-size violations: resolved

\* Remaining DRC warnings: solder-mask sliver warnings around fine-pitch footprints



The remaining solder-mask sliver warnings are documented as fabrication/assembly considerations rather than unresolved electrical design issues.



\## Repository Structure



```text

.

├── Docs/

│   ├── design\_notes.md

│   ├── bringup\_plan.md

│   └── known\_issues.md

├── Fabrication/

│   ├── Gerbers.zip

│   ├── NC\_Drill.zip

│   ├── BOM.csv

│   ├── Pick\_and\_Place.csv

│   └── DRC\_Report.pdf

├── Images/

│   ├── schematic\_overview.png

│   ├── pcb\_top.png

│   ├── pcb\_bottom.png

│   ├── 3d\_top.png

│   └── 3d\_bottom.png

├── Source/

│   ├── Altium\_Project\_Files/

│   └── Schematics\_PDF/

└── README.md

```



File names may vary depending on the exported Altium output files.



\## Project Status



This board is currently a proof-of-concept PCB design project. It has not yet been fabricated or electrically validated.



Planned bring-up steps include:



1\. Inspect PCB and assembly under magnification.

2\. Check for shorts between +3V3 and GND.

3\. Verify USB VBUS input.

4\. Verify 3.3 V regulator output.

5\. Connect SWD programmer and detect the STM32F411.

6\. Flash basic GPIO test firmware.

7\. Verify USB connectivity.

8\. Verify I2C communication with the MPU-6050.

9\. Read the MPU-6050 `WHO\_AM\_I` register.

10\. Test expansion connector GPIO/SPI-style signals.



\## Known Limitations



\* The board has not yet been fabricated.

\* The board has not yet been electrically tested.

\* Firmware bring-up has not yet been completed.

\* Some component footprints were sourced from third-party libraries and should be verified against manufacturer datasheets before fabrication.

\* Remaining DRC warnings are solder-mask sliver warnings around fine-pitch footprints.



\## Skills Demonstrated



\* Altium Designer schematic capture and PCB layout

\* MCU-based embedded board design

\* USB power input and 3.3 V regulation

\* ESD/TVS protection for external-facing connectors

\* I2C peripheral integration

\* SWD debug/programming interface design

\* Decoupling and power distribution

\* 4-layer PCB layout workflow

\* DRC troubleshooting and rule management

\* Fabrication output generation

\* Hardware design documentation



\## License



This project is provided for portfolio and educational purposes.




# Functionland DevKit

We're updating the documentation with first version dropping in a few days! This page will update...

As the first step, install a Raspberry Pi CM4 on your board. Track shops that have them in stock here:

https://rpilocator.com/

## overview
The DevKit board is a general purpose evaluation board for rapid-prototyping base on the Raspberry Pi Compute Module 4 (RPi CM4) and Raspberry Pi Zero 2 W (RPi Zero). High performance Compute module, Variety of USBs ports provides a flexible prototyping platform.


## Board Component Location
Figure below shows the Devkit board component locations. Each numbered component is shown in the table.

![Devkit_components_location](https://user-images.githubusercontent.com/3342690/211040885-91474fdf-057b-454a-a358-90412d65ff50.jpg)



| No.| Feature/Component       | Notes                                            |
| -- | ------------------------|--------------------------------------------------|
| 1  | RPi CM4 module          |                                                  |
| 2  | RPi Zero module         |                                                  |
| 3  | PCIe USB3 Controller IC | VL805 (Under CM4)                                |
| 4  | 4 Port USB HUB IC       | USB7252 Smart HUB                                |
| 5  | USB PD sink IC          | STUSB4500                                        |
| 6  | SPI flash memory IC     | SST26VF016B for HUB setting                      |
| 7  | SPI flash memory IC     | AT25SF321B for PCIe to USB (Under CM4 )          |
| 8  | 2.54 mm pin header      | For programming smart HUB spi flash memory       |
| 9  | 2.54 mm pin header      | For programming VL805 spi flash memory           |
| 10 | USB type-C connector    | Power input 9-20 V PD v2.0 compatible            |
| 11 | 2.54 mm pin header      | For programming PD power In IC                   |
| 12 | HDMI connector          | Connected to CM4 HDMI0                           |
| 13 | USB3 Type A connector   | Connected to VL805 PCIe USB3 Controller          |
| 14 | USB3 Type A connector   | Connected to VL805 PCIe USB3 Controller          |
| 15 | USB3 Type A connector   | Connected to VL805 PCIe USB3 Controller          |
| 16 | USB3 Type-C connector   | Connected to USB7252 SMART HUB                   |
| 17 | USB2 Type A connector   | Connected to USB7252 SMART HUB                   |
| 18 | USB3 Type-C connector   | Connected to USB7252 SMART HUB                   |
| 19 | USB3 Type A connector   | Connected to USB7252 SMART HUB                   |
| 20 | Power in jack           | For Power input                                  | 
| 21 | 2.54 mm pin header      | For Power input                                  |
| 22 | Push button             | Connected to RPi Zero                            |
| 23 | FAN connector           | Fan Controller IC is EMC2301                     | 
| 24 | Push button             | Connected to RPi CM4                             |
| 25 | Micro SD Connector      | Connected to RPi CM4                             |
| 26 | USB type-C connector    | USB2 Device for programming CM4 eMMC IC          |
| 27 | 2.54 mm pin header      | Connected to RPi CM4 UART TTL (GPIO14, 15)       | 
| 28 | 2.54 mm jumpers         | For enabling or disabling CM4 Features           |
| 29 | Slide Switch            | For CM4 Powering ON and OFF                      |
| 30 | LED3                    | For CM4 Status                                   |
| 27 | 2.54 mm pin header      | Connected to RPi Zero UART TTL (GPIO14, 15)      |
| 32 | 2.54 mm pin header      | For enabling smart HUB manually or with RPI Zero |

# Next steps
**Devkit Architecture**

for more information about block diagram and architecture see ["Devkit Architecture"](https://link-url-here.org)

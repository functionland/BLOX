# Functionland DevKit

We're updating the documentation with the first version dropping in a few days! This page will update...

As the first step, install a Raspberry Pi CM4 on your board. Track shops that have them in stock here:

https://rpilocator.com/

## overview
The DevKit board is a general-purpose evaluation board for rapid prototyping based on the Raspberry Pi Compute Module 4 (RPi CM4) and Raspberry Pi Zero 2 W (RPi Zero). A High-performance Compute module and a Variety of USBs ports provide a flexible prototyping platform.


## Board Component Location
The figure below shows the Devkit board component locations. Each numbered component is shown in the table.

![Devkit_components_location](https://github.com/functionland/BLOX/raw/main/Electrical/DevKit/documents/images/Devkit_components_location.jpg)



| No.| Feature/Component       | Notes                                            |
| -- | ------------------------|--------------------------------------------------|
| 1  | RPi CM4 module          |                                                  |
| 2  | RPi Zero module         |                                                  |
| 3  | PCIe USB3 Controller IC | VL805 (Under CM4)                                |
| 4  | 4 Port USB HUB IC       | USB7252C Smart HUB                               |
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
| 16 | USB3 Type-C connector   | Connected to USB7252C SMART HUB                  |
| 17 | USB2 Type A connector   | Connected to USB7252C SMART HUB                  |
| 18 | USB3 Type-C connector   | Connected to USB7252C SMART HUB                  |
| 19 | USB3 Type A connector   | Connected to USB7252C SMART HUB                  |
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
| 30 | LEDs                    | For CM4 Status                                   |
| 31 | 2.54 mm pin header      | Connected to RPi Zero UART TTL (GPIO14, 15)      |
| 32 | 2.54 mm pin header      | For enabling smart HUB manually or with RPI Zero |
| 33 | Push button             | For Reset Smart HUB IC                           |
| 34 | 2.54 mm pin header      | For selecting Smart HUB Boot Mode                |

# Quick Start Guide
## Power Adapter
For minimum function, you need a USB PD Adapter with 20V 10W at least. we suggest using USB Adapter with 30W power for proper functionality.
These are some USB Adapters that we suggested.

- [Anker 711 Charger (Nano II 30W)](https://www.anker.com/products/a2665)
- [Belkin 30W USB-C GaN Wall Charger](https://www.belkin.com/30w-usb-c-gan-wall-charger-usb-c-cable/P-WCH001dq1MWH-B6.html)
- [Ugreen Nexode Mini 45W Dual USB C Charger](https://eu.ugreen.com/collections/gan-chargers/products/ugreen-nexode-mini-45w-dual-usb-c-charger)


>**Note:** For power input USB PD sink IC STUSB4500 is used. the default configuration of this IC sets for 20V, but we can change the USB PD IC parameter and change it for other Voltage for example 9V or 12V. For more information, about the STUSB4500 setting see [Devkit USB PD STUSB4500](https://github.com/functionland/BLOX/blob/main/Electrical/DevKit/documents/documents_md/USB_PD_STUSB4500.md)

## RPi CM4 models
CM4 module is the heart of DevKit.The [Raspberry Compute Module 4](https://www.raspberrypi.com/products/compute-module-4) by the Raspberry Pi Foundation is a single-board computer (SBC) that is meant to be used in embedded devices. It has many new capabilities that have not been seen on other Pis before such as a built-in eMMC module (optional) and PCI express capabilities. we used most of these capabilities in the DevKit board. For selecting and buying see this [link](https://www.raspberrypi.com/products/compute-module-4/?variant=raspberry-pi-cm4104032).

![Devkit_components_location](https://github.com/functionland/BLOX/raw/main/Electrical/DevKit/documents/images/CM4_models.png)

>**Note:** For example, this Part Number "CM4108032" has Wireless, 4GB RAM and 32GB eMMC or this Part Number "CM4108000" has Wireless, 8GB RAM and no eMMC.

## RPi Zero module
In DevKit [Raspberry Pi Zero](https://www.raspberrypi.com/products/raspberry-pi-zero/) is optional and you can use it for example for standalone programming and flashing STUSB4500 USB PD IC or USB7252C Smart HUB IC.

## Flash Raspberry Pi OS to Micro SD Card 
For CM4 versions without eMMC, you need a Micro SD card and a card reader. For Flashing RPi OS download Raspberry Pi Imager tools and follow the instructions on youtube [How to use Raspberry Pi Imager](https://www.youtube.com/watch?v=ntaXWS8Lk34). For more information see [Raspberry Pi Operating system images](https://www.raspberrypi.com/software/operating-systems/). For RPi Zero the procedure is the same as CM4.

## Flash Raspberry Pi OS to CM4 eMMC
For the CM4 version with eMMC, you must mount CM4 eMMC on the PC after that program RPi OS with RPI Imager. First, install The usbboot utility installer from the Raspberry Pi Foundations GitHub Repository from [Official Raspberry Pi ???usbboot??? GitHub Repository](https://github.com/raspberrypi/usbboot/raw/master/win32/rpiboot_setup.exe)

put a jumper on NRPI_BOOT ( [Number 28](#Board-Component-Location) )
![Devkit_CM4_boot_jumper](https://github.com/functionland/BLOX/raw/main/Electrical/DevKit/documents/images/CM4_boot_jumper.jpg)\
\
after that connect USB Type-C near the CM4 module to the PC ( [Number 26](#Board-Component-Location) )
![Devkit_CM4_boot_jumper](https://github.com/functionland/BLOX/raw/main/Electrical/DevKit/documents/images/CM4_USB_type-c.jpg)\
\
and make sure the slide switch is in ENABLE position( [Number 29](#Board-Component-Location) ) and then connect a power adapter to the DevKit. if everything is OK you can see "BCM2711 Boot" in Device Manager.

![CM4_boot_device_manager](https://github.com/functionland/BLOX/raw/main/Electrical/DevKit/documents/images/CM4_boot_device_manager.png)\
\
Now open the "rpiboot" software from the start menu folder by right-clicking and choosing "Run as administrator". if everything is OK The window will disappear at this point and Windows will see the CM4 onboard eMMC as a new mass storage device. Now open the Raspberry Pi Imager utility from the start menu. The CM4 will show up as a drive available to be imaged like this.

![RPi_imager](https://github.com/functionland/BLOX/raw/main/Electrical/DevKit/documents/images/RPi_imager.png)\
\
For more information see these links
- [ Jeff Geerling Tutorial ](https://www.jeffgeerling.com/blog/2020/how-flash-raspberry-pi-os-compute-module-4-emmc-usbboot)
- [ Waveshare Tutorial ](https://www.waveshare.com/wiki/Write_Image_for_Compute_Module_Boards_eMMC_version)
- [ James A. Chambers Tutorial ](https://jamesachambers.com/full-compute-module-4-raspberry-pi-setup-imaging-guide/)


# Next steps

**Flashing VL805 SPI FLASH**

Devkit uses a VL805 PCIe USB3 controller for adding 3 USB3 type A plus USB HUB to CM4. For getting VL805 to work first its SPI Flash must be programmed. for more information see [Flashing VL805 SPI Flash](https://github.com/functionland/BLOX/blob/main/Electrical/DevKit/documents/documents_md/Flashing_VL805_SPI_Flash.md)\
\
\
**Devkit Architecture**

For more information about block diagrams and architecture see [Devkit Architecture](https://github.com/functionland/BLOX/blob/main/Electrical/DevKit/documents/documents_md/Architecture.md)

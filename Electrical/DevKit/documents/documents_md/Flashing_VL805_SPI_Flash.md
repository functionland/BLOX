# Flashing VL805 SPI FLASH
Devkit uses a VL805 PCIe USB3 controller for adding 3 USB3 type A plus USB HUB to CM4. For getting VL805 to work first its SPI Flash must be programmed.

## Flashnig with RPi Zero
we can use RPi Zero as a SPI programmer and Flash VL805 Firmware to SPI Flash Connected to VL805.
First Turn off Devkit and remove RPi Zero form Devkit connector. There is a connector for flashing VL805 SPI Flash on back of the Devkit board. see below picture.

![VL805 SPI FLASH Connector](https://github.com/functionland/BLOX/raw/main/Electrical/DevKit/documents/images/VL805_SPI_FLASH_Connector.png)\
\
![RPi Zero Pinout](https://github.com/functionland/BLOX/raw/main/Electrical/DevKit/documents/images/RPi_Zero_Pinout.png)

Connect these pins of RPi Zero to SPI Flash Connector with some jumper wire.

|Pin Number | Pin Name | Flash pin name|
|-----------|----------|---------------|
| 25        | GND      | GND           |
| 24        | CE0      | CE            |
| 23        | SCLK     | CLK           |
| 21        | MISO     | MISO          |
| 19        | MOSI     | MOSI          |
| 17        | 3.3v     | +3V3,WP,HLD   |


Power On RPi Zero with USB micro connector with PWR IN label. and connect to RPi Zero consol and run below commands.

enable SPI with raspi-config command.

```bash
sudo raspi-config
```

and in "Interfaceing Options" menu select "SPI" and select "Yes" for enabling SPI. see this link for more information [Enable SPI Interface on the Raspberry Pi](https://www.raspberrypi-spy.co.uk/2014/08/enabling-the-spi-interface-on-the-raspberry-pi/)

now install "flashrom" app with this command

```bash
sudo apt install flashrom
```

download firmware with this command

```bash
wget https://github.com/functionland/BLOX/raw/main/Electrical/DevKit/documents/vl805-000138a1_AT25SF321.bin
```

now write firmware to SPI flash with this command

```bash
flashrom -p linux_spi:dev=/dev/spidev0.0,spispeed=1000 -w vl805-000138a1_AT25SF321.bin
```

if eveythig goes OK these message shown.

```
pi@zero:~/flashrom $ flashrom -p linux_spi:dev=/dev/spidev0.0,spispeed=1000 -w new
flashrom v1.2 on Linux 5.15.61-v7+ (armv7l)
flashrom is free software, get the source code at https://flashrom.org

Using clock_gettime for delay loops (clk_id: 1, resolution: 1ns).
Found Atmel flash chip "AT25SF321" (4096 kB, SPI) on linux_spi.
===
This flash part has status UNTESTED for operations: ERASE WRITE
The test status of this chip may have been updated in the latest development
version of flashrom. If you are running the latest development version,
please email a report to flashrom@flashrom.org if any of the above operations
work correctly for you with this flash chip. Please include the flashrom log
file for all operations you tested (see the man page for details), and mention
which mainboard or programmer you tested in the subject line.
Thanks for your help!
Reading old flash chip contents... done.
Erasing and writing flash chip...
Warning: Chip content is identical to the requested image.
Erase/write done.
```

now you can remove jumper wires and power on Devkit

you can test VL805 with this command.

```bash
pi@cm4:~ $ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pi@cm4:~ $
```



see this link for more information about how program SPI Flash with RPi Zero
https://www.flashrom.org/RaspberryPi

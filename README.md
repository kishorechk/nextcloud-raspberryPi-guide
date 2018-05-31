# Setup a Next Cloud server on Raspberry Pi 3

## Hardware Requirements:
* Raspberry Pi 3 Model B+
* MicroSD Card
* External Hard drive/SSD card SATA
* External Hard drive docking station with SATA & USB 3.0
* Wifi Connection

## Software Requirements:
* NextCloud Pi image [download](https://ownyourbits.com/downloads/)
* Etcher [download](https://etcher.io)

## Installation
1. Download the latest NextCloudPi image
2. Write the image to MicroSD card using Etcher
3. Insert the MicroSD card to RaspberryPi
4. Start Raspberry Pi
.. this will boot RaspberryPi in command line, login with user default username/password, i,e Pi/raspberry
5. Change the default password
```
passwd
```
6. Enable SSH
```
sudo raspi-config
```
7. Connect to WiFi automatically when startup

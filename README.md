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
  * this will boot RaspberryPi in command line, login with user default username/password, i,e Pi/raspberry
5. Change the default password
```
passwd
```
6. Enable SSH
```
sudo raspi-config
```
7. Connect to WiFi automatically when startup
* update the file /etc/network/interfaces
```
sudo nano /etc/network/interfaces
```
the contents should look like below:
```
source-directory /etc/network/intefaces.d

auto lo
iface lo inet loopback

iface eth0 inet dhcp

allow-hotplug wlan0
auto wlan0

iface wlan0 inet dhcp
      wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```
* update the file /etc/wpa_supplicant/wpa_supplicant.conf
```
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```
... the contents should look like below:
```
coutry=GB
ctrl_iterface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
  ssid="<wifi n/w name>"
  psk="<wifi password>"
  proto=RSM
  key_mgmt=WPA-PSK
  pairwise=CCMP
  auth_alg=OPEN
}
```

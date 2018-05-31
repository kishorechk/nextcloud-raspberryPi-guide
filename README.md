# Setup a Next Cloud server on Raspberry Pi 3

[Nextcloud](https://nextcloud.com) is an open source, self-hosted file share and communication platform. Access & sync your files, contacts, calendars & communicate and collaborate across your devices. You decide what happens with your data, where it is and who can access it! 

This document will provide instructions and related info which I have captured as part of setting up my own NextCloud server. 

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
4. Inser the external Hard drive in dock station and connect the dock station to RaspberryPi
5. Start Raspberry Pi
  * this will boot RaspberryPi in command line, login with user default username/password, i,e Pi/raspberry
6. Change the default password
```
passwd
```
7. Enable SSH
```
sudo raspi-config
```
8. Connect to WiFi automatically when startup
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
9. Connect Nextcloud to WLAN run the below command and select nc-wifi
```
sudo nextcloudpi-config
```
10. At this step, Access nextcloud from another device connected to the same WiFi network. [More info](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-NextCloudPi)
* Administration can be done via TUI (Terminal User Interface) or WebUI (Web User Interface)
WebUI url: https://localIpAddress:4443
* Default admin username/password is: ncp/ownyourbits
* You can change the default credentials and create new admin user via TUI or WebUI
* NextCloud users can access web ui: https://localIpAddress
11. Connecting NextCloud from external
* Use a Dynamic DNS provider like NoIP or FreeDNS [More info](https://github.com/nextcloud/nextcloudpi/wiki/How-to-access-from-outside-your-network)
12. For NoIp, follow the below steps
* Register with [NoIP](https://www.noip.com), create a free subdomain
* Configure Port forward at Wifi Router. Add new rule, select nextcloudpi device and external/internal port as 443
* Install & Configure NoIP on nextcloud server [More info](https://ownyourbits.com/2017/03/05/dynamic-dns-for-raspbian-with-no-ip-org-installer/)
13. Configuring external Hardrive [More infi](https://github.com/nextcloud/nextcloudpi/wiki/How-to-configure-an-external-USB-drive-with-NextCloudPi)
13. check out [NextCloud apps](https://apps.nextcloud.com)
14. checkout [NextCloud desktop/mobile clients](https://nextcloud.com/clients/)

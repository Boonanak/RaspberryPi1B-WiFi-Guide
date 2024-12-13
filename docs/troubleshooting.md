sudo before cmds if neccesary

lsusb

sudo dmesg | grep wlan0

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

dmesg | grep usb

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

sudo apt-get install firmware-ralink

dmesg | grep wlan0

sudo iwlist wlan0 scan

sudo journalctl -u wpa_supplicant

HWaddr field

CTRL-EVENT-CONNECTED

Test with a different Wi-Fi dongle

Test on another network

DHCP is enabled: Check your router settings to confirm that DHCP is enabled. Most routers have this on by default.
IP address pool: Ensure that the DHCP server has an available range of IP addresses to assign. If the pool is exhausted, the router won’t offer an IP address.
MAC address filtering: If enabled, your router might be blocking the Pi’s MAC address. Try temporarily disabling MAC address filtering or add the Pi’s MAC address to the allowed list. To find the MAC address of your wlan0 interface, run:

Wi-Fi band: Ensure the Pi's Wi-Fi dongle supports the band your router is using (2.4 GHz or 5 GHz). Most Raspberry Pi Wi-Fi dongles support 2.4 GHz, but check the dongle's specifications if you are unsure.
Signal strength: Make sure the Raspberry Pi is within range of the router and that there are no significant obstructions that might interfere with the Wi-Fi signal

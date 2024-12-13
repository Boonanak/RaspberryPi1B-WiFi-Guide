# Establishing a Wi-Fi Connection

This guide will walk you through the steps to connect your Raspberry Pi 1 B to a Wi-Fi network. Since the Raspberry Pi 1 B doesn't have built-in Wi-Fi, we will be using a USB Wi-Fi adapter to establish the connection and do so manually by editing the wpa_supplicant.conf file. Follow the steps below to get your Raspberry Pi 1 B connected to the internet.

## Step 1: Boot up the Raspberry Pi

1. Insert the microSD card into the Raspberry Pi 1 B.
2. Power up the Raspberry Pi using the micro-USB power supply.
3. Wait for the Raspberry Pi to boot into Raspbian.

## Step 2: Install Necessary Drivers

Some older Wi-Fi dongles might require additional drivers. Check the manufacturer's website or forums for instructions. However, this demonstration will be done with the Ralink RT5370 USB Wi-Fi adapter which should not require any additional drivers to be installed.

## Step 3: Set up Wi-Fi Connection

1. Open a terminal and edit the `wpa_supplicant.conf` file:

```bash
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```

2. Add your Wi-Fi network credentials:

```bash
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="YourNetworkName"
    psk="YourPassword"
}
```

3. Save and exit the file (press CTRL+O, Enter, and CTRL+X).

## Step 4: Restart the Networking Service

Restart the networking service:

```bash
sudo systemctl restart wpa_supplicant
```

## Step 5: Check Wi-Fi Connection

Verify the connection by checking if the interface received an IP address:

```bash
ifconfig wlan0
```

Look for an `inet` entry. If it is missing, the Pi failed to connect.

To manually reconnect:

```bash
sudo dhclient wlan0
```

## Step 6: Test the Connection

Ping a website to confirm the connection:

```bash
ping -c 4 google.com
```

Or alternatively, ping a known public IP address:

```bash
ping -c 4 8.8.8.8
```
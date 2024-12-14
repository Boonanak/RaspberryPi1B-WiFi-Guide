# Troubleshooting Guide

This guide outlines useful commands and checks to help debug and resolve issues when connecting a Raspberry Pi 1 B to Wi-Fi. Each command is explained, and common scenarios are addressed.

## Debugging Commands

### Check USB Device Detection

```bash
lsusb
```

- **Description**: Lists all USB devices connected to the Raspberry Pi. Use this to confirm that your Wi-Fi dongle is recognized.

### Check Kernel Messages for WLAN

```bash
sudo dmesg | grep wlan0
```

- **Description**: Displays kernel messages related to the `wlan0` interface. Use this to identify errors or logs for your Wi-Fi connection.

### Reset the wlan0 Interface

```bash
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

- **Description**: Restarts the `wlan0` interface. Useful for resetting the connection.

### Check Kernel Messages for USB Devices

```bash
dmesg | grep usb
```

- **Description**: Displays kernel messages related to USB devices. Use this to check if your Wi-Fi dongle was detected correctly.

### Update and Upgrade Packages

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

- **Description**: Ensures your system and firmware are up to date. This is crucial for compatibility with Wi-Fi drivers.

### Install Wi-Fi Dongle Firmware

```bash
sudo apt-get install firmware-ralink
```

- **Description**: Installs the required firmware for Ralink-based Wi-Fi dongles.

### Scan for Available Wi-Fi Networks

```bash
sudo iwlist wlan0 scan
```

- **Description**: Lists available Wi-Fi networks. Check signal strength and quality for your desired network.

### View Logs for wpa_supplicant

```bash
sudo journalctl -u wpa_supplicant
```

- **Description**: Displays logs for the `wpa_supplicant` service. Useful for diagnosing authentication issues.

### Check IP and Network Configuration

```bash
ifconfig wlan0
```

- **Description**: Shows the configuration of the `wlan0` interface. Look for the `inet` field to confirm if an IP address was assigned.

### Check Wireless Configuration

```bash
iwconfig wlan0
```

- **Description**: Displays wireless interface settings, such as ESSID and signal strength.

### Check for Connection Events
- **Look for**: `CTRL-EVENT-CONNECTED`
  - Indicates a successful connection to the Wi-Fi network.

## Additional Tips

### Test with Different Hardware
- **Use a different Wi-Fi dongle**: To rule out hardware issues.
- **Try another network**: To verify if the issue is network-specific.

### Router Settings to Check
1. **DHCP**: Ensure it is enabled on your router. DHCP assigns IP addresses automatically.
2. **IP Address Pool**: Confirm there are available IP addresses in the pool.
3. **MAC Address Filtering**: Disable it temporarily or add the Raspberry Pi's MAC address to the allowed list. To find the MAC address, run:

   ```bash
   ifconfig wlan0
   ```
   
   Look for the `ether` field.
4. **Wi-Fi Band**: Ensure your Wi-Fi dongle supports the router's band (typically 2.4 GHz).
5. **Signal Strength**: Ensure the Raspberry Pi is within range and there are minimal obstructions.

### Optimize Signal Strength
- Use `sudo iwlist wlan0 scan` to check signal quality. A low signal level or quality below `50/70` may cause connection issues.

---

By systematically using these commands and checks, you can diagnose and resolve most connectivity issues with the Raspberry Pi 1 B. If problems persist, consult the [Optimizations Guide](optimizations.md) or seek additional support.

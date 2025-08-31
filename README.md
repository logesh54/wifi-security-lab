# wifi-security-lab
A hands-on project demonstrating WPA2-PSK Wi-Fi password cracking in a lab environment.
# Wi-Fi WPA2-PSK Cracking Lab

This repository documents a hands-on lab exercise performed in a controlled environment to demonstrate the process of cracking a WPA2-PSK Wi-Fi password. The purpose of this project is purely for educational purposes, highlighting the importance of using strong passwords for wireless networks.

## Tools Used

-   **Operating System:** Kali Linux
-   **Toolkit:** Aircrack-ng suite (airmon-ng, airodump-ng, aircrack-ng)
-   **Wordlist:** rockyou.txt

## Methodology

### Step 1: Interface Setup

The first step was to identify the wireless interface and put it into monitor mode. This allows the card to capture all wireless traffic, rather than just the traffic directed to it.

`$ sudo airmon-ng start wlan0`

### Step 2: Scanning for the Target Network

I used `airodump-ng` to scan for all nearby Wi-Fi networks and gather information such as their BSSID, channel, and ESSID.

`$ sudo airodump-ng wlan0`

### Step 3: Capturing the 4-way WPA Handshake

To crack the password, a crucial WPA handshake is required. I focused on the target network and captured the handshake by waiting for a client to connect.

`$ sudo airodump-ng -c 2 --bssid 48:22:54:CC:2F:76 -w capture wlan0`

### Step 4: Cracking the Password with a Dictionary Attack

With the handshake captured, I used `aircrack-ng` and the `rockyou.txt` wordlist to perform a dictionary attack.

`$ sudo aircrack-ng -w /usr/share/wordlists/rockyou.txt -b 48:22:54:CC:2F:76 capture-01.cap`

### Step 5: Results

The attack was successful, and the password was found, highlighting the need for strong, unique passphrases.


## Conclusion

This lab demonstrates how a weak WPA2-PSK password can be compromised. Using strong passwords with a mix of uppercase and lowercase letters, numbers, and symbols is essential for protecting your wireless network.

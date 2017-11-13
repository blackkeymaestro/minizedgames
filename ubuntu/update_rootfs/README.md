Additional helper scripts to update Ubuntu filesystem with firmware and apps for Minized

Wifi:
1) Copy install_wifi.tar.gz to USB stick and untar to a folder in HOME
2) Run the install.sh script
3) Mount the emmc (/dev/mmcblk1p1) and edit wpa_supplicant.conf with your wifi network credentials
4) Run sudo /usr/local/bin/wifi.sh
5) Run ifconfig to check that wlan0 interface is up.  Use "ping" command to ping a server or website to 
confirm connectivity

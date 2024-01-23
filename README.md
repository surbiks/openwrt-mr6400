# TP-Link TL-MR6400 v5.2

 in this toturial we want to install OpenWrt on **tp-link tl-mr6400(eu) v5.2** and after install OpenWrt we show how can back to orginal framware.
 
## Install OpenWrt

 1. Download OpenWrt firmware from [here](https://openwrt.org/toh/tp-link/tl-mr6400_v5).
 2. install **tftp server** on user pc. for ubuntu `sudo apt install tftpd-hpa`.
 3. edit tftp server config file.make working directory in home and set permission.
 4. create directory in home `mkdir -p tftp`
 5. change directory permission `sudo chown tftp:tftp tftp`
 6. edit tftp server config file like this. but change directory with your path.
```
# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/home/saeid/tftp"
TFTP_ADDRESS=":69"
TFTP_OPTIONS="--secure"
```
7. restart tftp server `sudo systemctl restart tftpd-hpa.service`
8. rename openwrt firmware to `tp_recovery.bin` and copy it to tftp folder.
9. change bin file permission `sudo chown tftp:tftp tftp/tp_recovery.bin` 
10. change interface ip to `192.168.0.225/24` and connect with cable to modem.
11. restart tftp server `sudo systemctl restart tftpd-hpa.service`
12. now power off modem with remove power supply.
13.  power on the modem while holding the reset button and connect to power supply
14. wait at least 8 seconds before releasing reset button
15. After downloading the new firmware image, the power light should flash for about 3mins, then the device should reboot.


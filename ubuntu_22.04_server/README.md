# UBUNTU SERVER CONFIG

**3. Config wifi**


- reboot

**DO NOT EVER UPGRADE DEBIAN, THIS WILL CAUSE ISSUES WITH WIRELESS CONNECTIONS**

------

## On your PC

**1. Download and etch the Debian image on the SD**

1. Download the image at: [https://github.com/radxa-build/radxa-zero3/releases/download/b6/radxa-zero3_debian_bullseye_xfce_b6.img.xz](https://github.com/Joshua-Riek/ubuntu-rockchip/actions/runs/13252925923/artifacts/2569189508)

2. Follow the  tutorial at: https://docs.radxa.com/en/zero/zero3/getting-started/install-os

## On RADXA ZERO 3 with keyboard, screen and mouse

**2. Login**
- Username: ubuntu
- Password: ubuntu


**3. Configure WiFi**
  
```
sudo wpa_passphrase "YourSSID" "YourPassword" | sudo tee /etc/wpa_supplicant/wpa_supplicant.conf
sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
sudo dhclient wlan0
```

Find your IP address:

```
ip a
```

**4. Logout**

## On LAN PC

**5. Connect via SSH**


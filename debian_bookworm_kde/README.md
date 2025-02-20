# DEBIAN BOOKWORK config

**The one provided by RADXA**

**DO NOT EVER UPGRADE DEBIAN, THIS WILL CAUSE ISSUES WITH WIRELESS CONNECTIONS**

------

## On your PC

**1. Download and etch the Debian image on the SD**

1. Download the image at: https://github.com/radxa-build/radxa-zero3/releases/download/b6/radxa-zero3_debian_bullseye_xfce_b6.img.xz

2. Follow the  tutorial at: https://docs.radxa.com/en/zero/zero3/getting-started/install-os

## On RADXA ZERO 3 with keyboard, screen and mouse

**2. Login**
- Username: radxa
- Password: radxa


**3. Configure WiFi**
  

```
sudo su
nmcli dev wifi connect "your_SSID" password "your_password"
```

Find your IP address:

```
ip a
```

**4. Logout**

## On LAN PC

**5. Connect via SSH**

----------

**To disable the GUI**

```
sudo systemctl set-default multi-user.target
```
- Reboot
  
**To reenable the GUI**

```
sudo systemctl set-default graphical.target
```
- Reboot

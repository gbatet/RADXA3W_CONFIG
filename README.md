# RADXA3W_CONFIG

Configuration step-by-step guide for RADXA ZERO 3W to start all the services automatically while maintaining password in ssh service.

------
## Materials:
- RADXA ZERO 3W
- USB C HUB
- HDMI to mini HDMI
- Peripherals:
  - Screen
  - Mouse
  - Keyboard

## On your PC

**1. Download and etch the Debian image on the SD**

1. Download the image at: https://github.com/radxa-build/radxa-zero3/releases/download/b6/radxa-zero3_debian_bullseye_xfce_b6.img.xz

2. Follow the  tutorial at: https://docs.radxa.com/en/zero/zero3/getting-started/install-os

## On RADXA ZERO 3 with keyboard, screen and mouse

**2. Login**
- Username: radxa
- Password: radxa


**3. Configure WiFi**

- Via GUI

  Go to the logo in the upwards right part of the screeen
  
- Via Terminal:

```
nmcli dev wifi connect "your_SSID" password "your_password"
```

Find your IP address:

```
ip a
```

**4. Logout**

## On LAN PC

**5. Connect via ssh**

**5.1. Create username (Optional)**
By default the existing ones are *radxa* and *rock*
    
```
sudo adduser changeme
```
  - Logout from *radxa*
  - Login into *changeme*
  - Make chengeme sudoer
```
sss
```

```
sudo deluser tempuser
sudo rm -rf /home/tempuser
```

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

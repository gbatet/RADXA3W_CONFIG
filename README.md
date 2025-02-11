# RADXA3W_CONFIG

INITIAL configuration step-by-step guide for RADXA ZERO 3W.

**DO NOT EVER UPGRADE DEBIAN, THIS WILL CAUSE ISSUES WITH WIRELESS CONNECTIONS"

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

**O.1. Migrate OS from SD to eMMC**
- Confirm the name of the eMMC:
```
lsblk
```
- Unmount and format the eMMC
- Copy the files from your PC to the RADXA ZERO 3
```
scp C:\Users\user\...\radxa-zero3_debian_bullseye_xfce_b6\radxa-zero3_debian_bullseye_xfce_b6.img username@192.168.xxx.xxx:/home/username/
```
- Flash the image
```
sudo dd if=/home/username/image.img of=/dev/mmcblk0 bs=4M status=progress
```
Once flashed and booted from OS, repeat the 1-4 steps and enable SSH:
```
sudo systemctl enable --now ssh
```

**O.2. Create username**

By default the existing ones are *radxa* and *rock*
    
```
sudo adduser changeme
```
  - Logout from *radxa*
  - Login into *changeme*
  - Make chengeme sudoer
    
```
sudo usermod -aG sudo changeme
```

```
sudo deluser radxa
sudo rm -rf /home/radxa
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

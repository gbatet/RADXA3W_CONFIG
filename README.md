# RADXA ZERO 3W CONFIG

INITIAL configuration step-by-step guide for RADXA ZERO 3W.

--------
## Materials:
- RADXA ZERO 3W
- USB C HUB
- HDMI to mini HDMI
- Peripherals:
  - Screen
  - Mouse
  - Keyboard

## Choose the OS folder and follow the README.md

## Optional steps in every OS

**O.1. Migrate OS from SD to eMMC**
- Confirm the name of the eMMC:
```
lsblk
```
- Format the eMMC
```
sudo mkfs.ext4 /dev/mmcblk0
```
- Copy the files from your PC to the RADXA ZERO 3
```
scp C:\Users\user\...\radxa-zero3_debian_bullseye_xfce_b6\radxa-zero3_debian_bullseye_xfce_b6.img username@192.168.xxx.xxx:/home/username/
```
- Flash the image
```
sudo dd if=/home/username/image.img of=/dev/mmcblk0 bs=4M status=progress
```

**O.2. Create username**
    
```
sudo adduser changeme
```

  - Make chengeme sudoer
    
```
sudo usermod -aG sudo changeme
```
  - Logout from *radxa*
  - Login into *changeme*

```
sudo deluser radxa
sudo rm -rf /home/radxa
```

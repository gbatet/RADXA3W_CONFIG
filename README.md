# RADXA3W_CONFIG

INITIAL configuration step-by-step guide for RADXA ZERO 3W.

--------

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
Once flashed and booted from OS, repeat the 1-4 steps and enable SSH:
```
sudo systemctl enable --now ssh
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

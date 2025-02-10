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

**5.1. Change username or password (Optional)**

- Username (change newuser to your prefered name)
  - Create a admin user (change password admin to your prefered)
    
```
sudo adduser admnin
sudo passwd admin
```
  - Logout from *radxa*
  - Login into *admin*
  - Change the name of the *radxa* user
```
sudo usermod -l newuser -d /home/newuser -m RADXA
sudo groupmod -n newuser RADXA
```

- Password
  
```
sudo passwd username
```

- if admin is not needed:

In newuser loggedout form admin
```
sudo deluser tempuser
sudo rm -rf /home/tempuser
```


**Enable auto-login while keeping ssh with password**

1. In GUI:

```
sudo nano /etc/lightdm/lightdm.conf
```

Find and uncomment:

```
[Seat:*]
autologin-user=rock
autologin-user-timeout=0
```
Restart the lightdm system

```
sudo systemctl restart lightdm
```

2. In Terminal
  
```
sudo mkdir -p /etc/systemd/system/getty@tty1.service.d/
sudo nano /etc/systemd/system/getty@tty1.service.d/autologin.conf
```

Add (changing username by your username, e.g. radxa if default):

```
[Service]
ExecStart=
ExecStart=-/sbin/agetty --autologin username --noclear %I $TERM
```

Reboot the service:

```
sudo systemctl daemon-reexec
sudo systemctl restart getty@tty1
```

- ssh

```
sudo nano /etc/ssh/sshd_config
```
Change to:

```
PasswordAuthentication yes
PermitRootLogin no
PubkeyAuthentication yes
```
And restart the service:

```
sudo systemctl restart ssh
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

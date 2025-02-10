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
- Username: RADXA
- Password: RADXA
  
**2.1. Change username or password (Optional)**

- Username (change newuser to your prefered name)
```
sudo usermod -l newuser -d /home/newuser -m RADXA
sudo groupmod -n newuser RADXA
```
Now change your display name:

```
sudo chfn -f "New User Name" newuser
```

- Password
  
```
sudo passwd username
```

**3. Configure WiFi**
- Via GUI

  Go to the logo in the upwards right part of the screeen
  
- Via Terminal:

```
nmcli dev wifi connect "your_SSID" password "your_password"
```

Find your IP address:





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

# RADXA3W_CONFIG

**Download and etch the Debian image on the SD**

1. Download the image at: https://github.com/radxa-build/radxa-zero3/releases/download/b6/radxa-zero3_debian_bullseye_xfce_b6.img.xz

2. Follow the  tutorial at: https://docs.radxa.com/en/zero/zero3/getting-started/install-os

**Enable auto-login while keeping ssh with password**

- In GUI:

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

- In Terminal
  
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

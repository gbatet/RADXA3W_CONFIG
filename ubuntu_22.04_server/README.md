# UBUNTU SERVER CONFIG

**1. Download the image at:**
- https://github.com/Joshua-Riek/ubuntu-rockchip/actions/runs/13252925923/artifacts/2569189508
  (https://github.com/Joshua-Riek/ubuntu-rockchip/actions/runs/13252925923)

**2. Login**
- ubuntu
- ubuntu

**3. Config wifi**

```
sudo wpa_passphrase "YourSSID" "YourPassword" | sudo tee /etc/wpa_supplicant/wpa_supplicant.conf
sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
sudo dhclient wlan0
ip a
```
- reboot

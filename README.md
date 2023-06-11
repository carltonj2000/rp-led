# LED Lights Controlled By A Raspberry Pi

Never release this due to not liking the reset style of tailwind.
Should use the tailwind default markdown styles.

## Sofware - Flashing

```bash
sudo apt install rpi-imager
rpi-imager # use ctrl-shift-x to set hostname, user, pw, wifi ssid, ssh
```

## Software Raspberry Pi

- On the desktop version of rpi use `Preferences > Raspberry Pi Configuration`
  in order to enable SSH.
- On the non-desktop version of rpi use `sudo raspi-config`.

```bash
sudo apt update
sudo apt upgrade
sudo apt install python3-pip # desktop does not need this
sudo pip install rpi_ws281x
sudo apt install git # desktop does not need this
git clone https://github.com/rpi-ws281x/rpi-ws281x-python
```

Edit `sudo nano /etc/modprobe.d/snd-blacklist.conf` add the content below.

```
blacklist snd_bcm2835
```

Edit `` and comment out the audio as noted below.

```
# Enable audio (loads snd_bcm2835)
#dtparam=audio=on
```

```bash
sudo reboot # reboot to take effect
```

The details above are from the following links.

- https://tutorials-raspberrypi.com/connect-control-raspberry-pi-ws2812-rgb-led-strips/
- https://phoenixnap.com/kb/enable-ssh-raspberry-pi

## Creation History

```bash
npm create astro@latest
npx astro add tailwind
```

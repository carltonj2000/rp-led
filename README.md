# LED Lights Controlled By A Raspberry Pi

Never release this due to not liking the reset style of tailwind.
Should use the tailwind default markdown styles.

## Software - Flashing

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

Edit `sudo nano/vi /etc/modprobe.d/snd-blacklist.conf` add the content below.

```
blacklist snd_bcm2835
```

Edit `sudo nano/vi /boot/config.txt` and comment out the audio as noted below.

```
# Enable audio (loads snd_bcm2835)
#dtparam=audio=on
```

```bash
sudo reboot # reboot for audio disable to take effect
```

```bash
cd rpi-ws281x-python/examples
sudo python3 strandtest -c # update LED_COUNT in code to 300
```

To run the script automatically on start-up do the following.

```text title="/etc/rc.local"
sudo python3 /home/carltonj2000/rpi-ws281x-python/examples/strandtest.py &
```

The details above are from the following links.

- https://tutorials-raspberrypi.com/connect-control-raspberry-pi-ws2812-rgb-led-strips/
- https://phoenixnap.com/kb/enable-ssh-raspberry-pi

## Creation History

```bash
npm create astro@latest
npx astro add tailwind
```

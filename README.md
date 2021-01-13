# How I Setup Klipper on a fresh Raspberry PI
- [Choose your PI](#choose-your-pi)
- [Prepare the Raspberry PI](#prepare-the-raspberry-pi)
- [Connect to your pi and update](#connect-to-your-pi-and-update)
- [Install the install script for Klipper and install those](#install-the-install-script-for-klipper-and-install-those)
- [Setup the webcam](#setup-the-webcam)
- [Setup the file share](#setup-the-file-share)


## Choose your PI
I have experience with most Raspberry PIs now. Because I started out with Octoprint, I started out with a Raspberry PI 4.
It's not great, because:
- it's picky with what power source it wants (recommended the RPi official charger)
- it runs HOT (I burned my fingers on it), so it needs a FAN
- it does not have WIFI onboard

This makes for a bit of a mess, so now I'm going to set it up on my Raspberry PI Zero W

## Prepare the Raspberry PI
- [x] Raspberry PI
- [x] Charger & cables
- [x] MicroSD card
- [x] PI camera (optional)
- [x] Raspberry PI case (optional)
- [x] Touchscreen (optional)

Preparing the OS on the SD card is super simple:
1. Connec the SD card to your pc
2. Download the Raspberry PI imager (https://www.raspberrypi.org/software/)
3. Let it flash the SD card

The same OS now works for all Raspberry PIs. Nice.

4. Re-insert the SD card in your pc because you want to setup:
- [x] Wifi credentials (you are going to run this headless)
https://www.raspberrypi-spy.co.uk/2017/04/manually-setting-up-pi-wifi-using-wpa_supplicant-conf/
- [x] Enable SSD: Create an empty file with the name 'SSH' and put it on the BOOT partition.
5. Put your pi in your case (optional) with your camera (optional) and power it up!

## Connect to your pi and update
So, there's this nifty thing where devices on your local network are now addressable with \<hostname>.local.
The raspberry pi has "raspberrypi" as hostname, so connect to 'raspberrypi.local' with Putty (or another SSH client)

Do a few things:
1. Change your password
2. Change your hostname (sudo raspi-config -> system options)
3. [optional] Add your RSA public fingerprint to .ssh (chmod 700) / authorized_keys (chmod 644)
4. sudo apt-get update && sudo apt-get upgrade

## Install the install script for Klipper and install those
This is awesome by `th33xitus`:

https://github.com/th33xitus/kiauh

```
sudo apt-get install git -y
cd ~
git clone https://github.com/th33xitus/kiauh.git
cd kiauh
chmod +x kiauh.sh scripts/*
./kiauh.sh
```

I install:
- [x] Klipper (duh)
- [x] Moonraker (API, required)
- [x] Mainsail (Website, uses API)
- [x] KlipperScreen (I have a touchscreen attached)

## Setup the webcam
This works for the PI cam or any attached USB webcam.

## Setup the file share


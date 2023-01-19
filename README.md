# rocinante
Space heater powered by and Antminer S9 controlled by an RPi4

## Initial Setup

### Create microSD card on an admin workstation

```shell
RPI_IMG=2022-09-22-raspios-bullseye-arm64-lite.img
RPI_IMG_URL=https://downloads.raspberrypi.org/raspios_lite_arm64/images/raspios_lite_arm64-2022-09-26/${RPI_IMG}.xz
MICROSD=/dev/sda

wget $RPI_IMG_URL
xz -d $RPI_IMG.xz

# insert microSD, ensure all partitions are NOT mounted

sudo dd if=$RPI_IMG of=$MICROSD bs=1M status=progress
```

### First Boot
- Boot RPi from microSD card created above
- Complete initial setup, default options are fine if you're unsure
- Run `./rpi-wifi.sh` to configure your WiFi client & AP settings
  - `rpi-wifi -a PiFiNet pifipass -c MyIsp myisppass`
- Run ./bridge.sh` to configure the wifi-ethernet bridge
- Reboot

#### First Boot WIP
- TODO: verify AP mode
- TODO: verify wifi client mode
- TODO: verify ethernet connectivity

### Normal Operation
- TODO: flask server listening on PiFiNet interface
- TODO: integrate [pyasic](https://github.com/UpstreamData/pyasic) or [hass-miner](https://github.com/Schnitzel/hass-miner)
- TODO: DHT11 temperature/humidity sensor

---

## Acknowledgements
- [rpi-wifi](https://github.com/lukicdarkoo/rpi-wifi) by lukicdarkoo
  - Special thanks to [albeec13](https://albeec13.github.io/2017/09/26/raspberry-pi-zero-w-simultaneous-ap-and-managed-mode-wifi/) for sharing your research with the world
- [RPi wifi ethernet bridge](https://www.willhaley.com/blog/raspberry-pi-wifi-ethernet-bridge/) by Will Haley

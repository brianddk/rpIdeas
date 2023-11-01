# PiZero Gadgetmode Internet bootstrap

- Download [Imager and Sig][a]
- Download OS [Lite image and Sig][b]
- Add SSH key using Imager utility
- Enable SSH using Imager utility
- Set hostname / username / password using Imager Utility
- If WiFi is wanted, set password using Imager Utility
- If WiFi is not wanted, set `dtoverlay=disable-wifi` in config.txt
- Add ` modules-load=dwc2,g_ether ` after `rootwait` in cmdline.txt
- Add `dtoverlay=dwc2` at end of config.txt
- Add `enable_uart=1` in config.txt to enable UART on default serial pins
- Add `dtoverlay=gpio-shutdown` to enable boot/shutdown on GPIO3 low.
- Place `custom_init.sh` on SD card next to config.txt (see below)
- In `firstrun.sh`, replace `rm -f /boot/firstrun.sh` with `custom_init.sh\nrm -f /boot/firstrun.sh`
- Install [RNDIS driver if Win10][c]
- Connect PiZero "usb" port to USB of PC
- Watch for new network card to show up on Windows PC
- Enable ICS in windows bridging WAN NIC to your RNDIS nic
- Short physical pins 5 and 6 for 1s to initiate a soft shutdown
- Short physical pins 5 and 6 for 1s to initiate a poweron
- SSH to <username>@<hostname>.local to login to your Pi
- `sudo apt update` should now complete network queries without error.
- You can now remove `custom_init.sh` and the shutdown, wifi, and uart setings in config.txt as desired

NOTE: Not sure if the context of `firstrun.sh` will see the boot files at `/boot` or `/boot/firmware`

[a]: https://downloads.raspberrypi.org/imager/
[b]: https://downloads.raspberrypi.com/raspios_lite_armhf/images/
[c]: https://www.reddit.com/r/raspberry_pi/comments/41xnj9/comment/k4ax60j/


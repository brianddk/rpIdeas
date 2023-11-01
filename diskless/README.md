# Gadgetmode diskless NFS bootstrap

Would have to run on bullseye since bookworm [doesn't bring USB0 up at boot][f].

1. Create a "server" to power PiZero and run [rpiboot][e] (has Win32 installer too)
2. Create a PiZero bullseye install as normal
3. Move the `boot` partition to a directory on "server"
4. Run [rpiboot][e], pointing to the boot directory
5. Configure ICS on "server"
6. Configure boot directory to enable g_ether/dcw2 mode
7. Configure boot directory to NFS mount rootfs
8. Run NFS server on "server"
9. Move `root` FS to the NFS server
10. Remove uSD from PiZero and plug it into "server" USB port.
11. Should boot in `rpiboot` mode then bootstrap to gadget mode.

TODO: Figure out how to run an NFS server on Pi

[d]: https://forums.raspberrypi.com/viewtopic.php?t=358743
[e]: https://github.com/raspberrypi/usbboot
[f]: https://forums.raspberrypi.com/viewtopic.php?p=2146074
[g]: https://pimylifeup.com/raspberry-pi-nfs/

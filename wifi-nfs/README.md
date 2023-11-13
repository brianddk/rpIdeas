## NFS WiFi Boot

Booting from NFS requires getting WiFi and the NFS client up in the initramfs before the `root_pivot` call.  It's [impossible in systemd][u], but may be [possible in Dracut][w], but only [after modificaiton][v]

[u]: https://raspberrypi.stackexchange.com/a/113755/43868 (can't be done with systemd)
[v]: https://github.com/dracutdevs/dracut/discussions/2514 (Gentoo <dracut> requires modification)
[w]: https://forums.gentoo.org/viewtopic-t-1122257-start-0.html (Dracut with OpenRC)


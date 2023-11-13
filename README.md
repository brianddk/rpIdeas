# rpIdeas

This repo is a list of ideas / projects to do on a Raspberry Pi

## WIP

- [ ] Headless install of bookworm on Pi0r1W using g_ether (ether gadget) IPv6
- [ ] Headless install of bookworm on Pi1Br2 using eth0 IPv6
- [ ] Headless install of bookworm on Pi0r1W/Pi1Br2 using USB-TTL serial
- [ ] Headless install of bookworm on Pi0r1W/Pi1Br2 using Pico as a USB-TTL serial (picoprobe)
- [ ] Use CD4504B to do TTL transition from 3V3->5V->3V3
- [ ] Do an I2C loopback from I2C0 to BSC on Pi0r1W
- [ ] Drive a 6502 processor using a PICO in bitbang mode
- [ ] Drive a 6502 processor using a PICO in PIO mode
- [ ] Drive a 6502 processor using Pi0r1W
- [ ] 8bit i2C expander (MCP23008), 16bit SPI expander (MCP23S18)
- [ ] Power and boot and login to Pi0r1W using a USB-TTL widget
- [ ] piDaisy - Pi1Br2->Pico(spi); Pi1Br2->Pi0r1W(i2c); Pi1Br2->ODroid(g_ether/serial/ether);
- [ ] Build vasm for 6502 project
- [ ] Build burn utility for 6502 project
- [ ] Install micropython default script (main.py) then break into it via serial.
- [ ] Set hardware-ids on g_ether modulule parameters to remove floating IPs
- [ ] Combine [g_ether][5], [ICS][5], and rootnfs to make a [diskless boot][6]
- [ ] Combine [g_ether][5], [rpiboot][6], [ICS][5], and net_install boot.img to do a network install on PiZero
- [ ] Perform a [Win10 IoT][7] install to run powershell on a Pi2/Pi3
- [ ] Install [Win11 on 4GB Pi4][8]
- [ ] Use PINN to dual boot a Pi.
- [ ] [Add another disk to WSL][9]
- [ ] [LFS from WSL][a]
- [ ] Try `systemd.debug_shell` in initramfs to swap USB from rpiboot to USB
- [ ] Use [hamming-codec][b] for piSlave project
- [ ] Make 5v Relay curcuit so that you can switch from on OTG device to another (dual honed cable)
- [ ] [Use the PiOS from scratch][c] project
- [ ] pigpio polls slave I2C, figure out how to hook the intterrupt.
- [ ] Using cc65 with 6502 project ([ref1][d], [ref2][e])
- [ ] Make a Gentoo bin-pkg server ([with datacenter SATA drive][j] and [PWR adapter][i], and splitter][k])
- [ ] Install [slackware on Pi][g] ([Slack 15 requires armv7 or higher][f])
- [ ] [Add GParted to initramfs][h]
- [ ] [Gentoo from scratch using catalyst][l]
- [ ] [Add WiFi to Dracut][m] (Gentoo initramfs)
- [ ] Learn how to launch a [U-Boot shell][n]
- [ ] Request that RPi `bootcode.bin` support GPT (test with Gentoo builder)
- [ ] [Gentoo build server][o]
- [ ] [Make a user Raspberry Pi Wiki page][p]
- [ ] [Make a Gentoo pull request for raspi-config][q] for eventual [GURU submission][r]
- [ ] [Try an IO Expander][s]
- [ ] Try [adding a disk to WSL2][t] and perform LFS on it.
- [ ] [RTC for Pi][x] with a [wake alarm][y]
- [ ] [WiFi NFS Boot][z]
- [ ] [Install Arch][u]

[9]: https://joeferguson.me/adding-another-disk-to-wsl2/
[a]: https://www.reddit.com/r/linuxfromscratch/comments/vtgu3h/can_i_create_lfs_using_wsl/
[b]: https://pypi.org/project/hamming-codec/
[c]: https://s-matyukevich.github.io/raspberry-pi-os/
[d]: https://www.reddit.com/r/beneater/comments/kn52w3/using_cc65_to_write_code_in_c_for_the_6502/
[e]: https://www.reddit.com/r/beneater/comments/fprcsz/using_cc65_to_compile_c_code_for_my_slightly/
[f]: https://arm.slackware.com/releases/
[g]: https://docs.slackware.com/howtos:hardware:arm:raspberrypi
[h]: https://stackoverflow.com/a/54152399
[i]: https://www.amazon.com/dp/B00MYU0EAU/
[j]: https://www.amazon.com/dp/B01I7SAHO0/
[k]: https://www.amazon.com/dp/B095NKT5F7/
[l]: https://wiki.gentoo.org/wiki/Stage_tarball
[m]: https://github.com/dracutdevs/dracut/discussions/2514
[n]: https://docs.u-boot.org/en/latest/
[o]: https://forums.gentoo.org/viewtopic-p-8807124.html
[p]: https://duckduckgo.com/?q=gentoo+wiki+user+Pi+Install+Guide&t=brave&ia=web
[q]: https://wiki.gentoo.org/wiki/GitHub_Pull_Requests
[r]: https://wiki.gentoo.org/wiki/Project:GURU
[s]: https://www.mouser.com/ProductDetail/Microchip-Technology/MCP23008-E-P?qs=8FMarzwez060sofcCmNWdQ%3D%3D
[t]: https://joeferguson.me/adding-another-disk-to-wsl2/
[x]: https://www.amazon.com/dp/B00LX3V7F0
[y]: https://forums.raspberrypi.com//viewtopic.php?f=65&t=166853&p=1075093&hilit=time+lapse#p1074313
[z]: wifi-nfs#readme
[u]: arch#readme (needs copy-edit)

<!-- Next = 10,11,12,13 -->

## Fleshed out
- [Share usb0 internet][5] connection through PC, see linux guides ([arch][3], [xmodulo][4])
- SPI SD-Card to boot from SD1 instead of SD0 ([post question][1])
- [Build micropython][2] for 6502 project
- [Install Gentoo][v]
- [Make InitRamFS install][w]

[8]: https://www.youtube.com/watch?v=zGF_HaSdFyA "Win11WoR"
[7]: https://www.youtube.com/watch?v=JPRUbGIyODY "Win10IoT"
[6]: diskless#readme
[5]: g_ether#readme
[4]: https://www.xmodulo.com/internet-connection-sharing-iptables-linux.html
[3]: https://wiki.archlinux.org/title/Internet_sharing
[2]: micropython#readme
[1]: https://forums.raspberrypi.com/viewtopic.php?t=358559
[v]: gentoo#readme (needs copy-edit)
[w]: initramfs#readme

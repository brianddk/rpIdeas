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

## Fleshed out
- [Share usb0 internet][5] connection through PC, see linux guides ([arch][3], [xmodulo][4])
- SPI SD-Card to boot from SD1 instead of SD0 ([post question][1])
- [Build micropython][2] for 6502 project

[6]: diskless#readme
[5]: g_ether#readme
[4]: https://www.xmodulo.com/internet-connection-sharing-iptables-linux.html
[3]: https://wiki.archlinux.org/title/Internet_sharing
[2]: micropython#readme
[1]: https://forums.raspberrypi.com/viewtopic.php?t=358559

## InitRamFS

sudo bash
modprobe configs
gunzip -c /proc/config.gz > /boot/config-$(uname -r)
https://www.raspberrypi.com/documentation/computers/config_txt.html#model-filters
https://www.raspberrypi.com/documentation/computers/config_txt.html#cmdline
https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#bootcode-bin-uart-enable
cmdline-pi0w.txt
  console=serial0,115200 init=/bin/sh
config.txt
  [pi0w]
  initramfs initramfs followkernel
  cmdline=cmdline-pi0w.txt

https://chat.openai.com/share/68d45c2a-ac75-4f46-953f-78aafe04fff1
https://wiki.gentoo.org/wiki/Raspberry_Pi_Serial_Ports
https://www.youtube.com/watch?v=f5S2lAB4w7s (wifi nfsroot failure)

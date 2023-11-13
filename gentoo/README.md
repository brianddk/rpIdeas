## GenToo

https://wiki.gentoo.org/wiki/Raspberry_Pi/Quick_Install_Guide
lsblk
export device=/dev/sda
export ghfwtag=1.20230405
export kver=6.1.21+
sudo gdisk ${device} (o,n {1g efi, 1g swap, rest linux}, p,r,h {1 2 3} o,w)
sudo mkfs.vfat -F 32 -n 'GENTOO_BOOT' ${device}1
sudo mkswap -L 'gentoo_swapfs' ${device}2
sudo mkfs.ext4 -L 'gentoo_rootfs' ${device}3
sudo bash
mkdir -p /mnt/gentoo
mount ${device}3 /mnt/gentoo
mkdir -p /mnt/gentoo/{boot,usr/src/rpi-firmware}
mount ${device}1 /mnt/gentoo/boot
cd /mnt/gentoo/usr/src/rpi-firmware
git clone -b ${ghfwtag} --depth 1 https://github.com/raspberrypi/firmware/ .
git checkout -b "local/${ghfwtag}"

wget https://github.com/raspberrypi/firmware/archive/refs/tags/${ghfwtag}.tar.gz
tar -xzvf 1.20230405.tar.gz -C .. --strip-components=2 firmware-1.20230405/boot/
echo "dwc_otg.lpm_enable=0 console=ttyS0,115200 kgdboc=ttyS0,115200 console=tty1 root=/dev/mmcblk0p3 rootfstype=ext4 elevator=deadline rootwait" > ../cmdline.txt

wget https://github.com/RPi-Distro/firmware-nonfree/archive/refs/heads/bullseye.tar.gz
tar -xzvf rpi-brcm-bullseye.tar.gz -C /mnt/gentoo/lib/firmware --strip-components=4 firmware-nonfree-bullseye/debian/config/brcm80211/cypress
tar -xzvf rpi-brcm-bullseye.tar.gz -C /mnt/gentoo/lib/firmware --strip-components=4 firmware-nonfree-bullseye/debian/config/brcm80211/brcm

mkdir -p ../../root/lib/modules/${kver}
tar -xzvf rpi-firmware-1.20230405.tar.gz -C ../../root/lib/modules/${kver} --strip-components=3 firmware-1.20230405/modules/${kver}/
cd /mnt/gentoo/root/tarballs
wget https://gentoo.osuosl.org/releases/arm/autobuilds/current-stage3-armv6j_hardfp-openrc/stage3-armv6j_hardfp-openrc-20231104T213159Z.tar.xz
tar -xJvf stage3-armv6j_hardfp-openrc-20231104T213159Z.tar.xz -C ..

https://wiki.gentoo.org/wiki/Upgrading_Gentoo
https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Stage
https://wiki.gentoo.org/wiki/Stage_tarball (Only Stage3 tarballs since 2005)

https://wiki.gentoo.org/wiki/Raspberry_Pi/Quick_Install_Guide
https://wiki.gentoo.org/wiki/Netifrc
https://wiki.gentoo.org/wiki/Raspberry_Pi_Serial_Ports
https://wiki.gentoo.org/wiki/Chroot

https://www.linuxfromscratch.org/blfs/view/svn/basicnet/libnl.html
https://github.com/thom311/libnl/releases/download/libnl3_8_0/libnl-3.8.0.tar.gz
https://www.linuxfromscratch.org/blfs/view/svn/basicnet/wpa_supplicant.html
https://w1.fi/releases/wpa_supplicant-2.10.tar.gz

https://forums.gentoo.org/viewtopic-p-8806831.html

mkdir -p /etc/wpa_supplicant/
cat > /etc/wpa_supplicant/wpa_supplicant.conf << "EOF"
network={
    ssid="Your_Network_Name"
    key_mgmt=WPA-PSK
    psk="Your_Wi-Fi_Password"
}
EOF
wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
dhcpcd -N wlan0

https://wiki.gentoo.org/wiki/Handbook:AMD64/Networking/Wireless

emerge --sync --quiet
  time    49m 7.480s
eselect profile list
eselect profile set 29
cd $(portageq distdir)
emerge --fetchonly --pretend wpa_supplicant
wget ...
exit, reboot, swapSD
emerge wpa_supplicant
  time    1h 12m 18.039s
emerge ntp
  time    1h 43m 12.877s
emerge sys-apps/rng-tools
  time    9m 34.925s
emerge net-dns/avahi
  time    7h 48m 9.433s
emerge dev-vcs/git
  time    2h 14m58.944s
emerge --sync guru
emerge --update --deep --newuse --with-bdeps=y @world

https://wiki.gentoo.org/wiki/Project:Portage/Sync#Portage_configuration


https://wiki.gentoo.org/wiki/Avahi
https://wiki.gentoo.org/wiki/Knowledge_Base:Accepting_a_keyword_for_a_single_package
emerge --autounmask=y --autounmask-write --ask sys-auth/nss-mdns
dispatch-conf
emerge sys-auth/nss-mdns

https://wiki.gentoo.org/wiki/Project:GURU/Information_for_End_Users
emerge --sync --quiet
  time    24m 33.105s
emerge app-eselect/eselect-repository
  real    3m34.096s
eselect repository enable guru
emerge dev-vcs/git

emerge --sync guru

https://forums.gentoo.org/viewtopic-t-1085556-start-0.html

4.2.1 - make install libnl
4.2.2 - make install wpa_supplicant
4.2.3 - make uninstall libnl
4.2.4 - wpa_supplicant -B -i wlan0 -c ...
4.2.5 - dhcpcd -N wlan0
4.2.6 - emerge --sync --quiet
4.2.7 - emerge -av net-wireless/wpa_supplicant
/usr/local/sbin/wpa_supplicant

3.5.1 - Chroot - https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Base#Chrooting
3.5.2 - emerge --sync --quiet
3.5.3 - eselect profile list | grep armv6
3.5.4 - eselect profile set 29 # default/linux/arm/17.0/armv6j (stable)
3.5.3 - cd $(portageq distdir)
3.5.4 - download: emerge --fetchonly --pretend net-wireless/wpa_supplicant net-wireless/wireless-regdb dev-libs/libnl

4.1.1 - install: emerge --ask wpa_supplicant
4.1.2 - initialize /etc/conf.d/net
4.1.3 - initialize /etc/wpa_supplicant/wpa_supplicant.conf
4.2   - perform step replacing net0 with wlan0

cat > /etc/conf.d/net < EOF
# Note: This depends on wpa_supplicant being installed
modules_wlan0="wpa_supplicant"
config_wlan0="dhcp"
EOF

eselect profile set 29
[29]  default/linux/arm/17.0/armv6j (stable)

reset-boot.sh: 15m 1.719s

mount --rbind /dev /mnt/gentoo/dev
mount --make-rslave /mnt/gentoo/dev
mount --types proc /proc /mnt/gentoo/proc
mount --rbind /sys /mnt/gentoo/sys
mount --make-rslave /mnt/gentoo/sys
mount --rbind /tmp /mnt/gentoo/tmp
mount --bind /run /mnt/gentoo/run
sudo cp /etc/resolv.conf /mnt/gentoo/etc
sudo chroot /mnt/gentoo /bin/bash

cp /usr/share/zoneinfo/America/Chicago /etc/localtime
echo "America/Chicago" > /etc/timezone

cp /mnt/gentoo/usr/share/zoneinfo/America/Chicago /mnt/gentoo/etc/localtime
echo "America/Chicago" > /mnt/gentoo/etc/timezone

emerge --sync --quiet

sudo umount /mnt/gentoo/{dev,proc,sys,tmp,run,boot,.}


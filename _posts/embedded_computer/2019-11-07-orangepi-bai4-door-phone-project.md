---
layout: post
title: Bài 4 - Door phone project - Hướng dẫn voice IP project
author: Thong Ho
date: '2019-11-07 21:35:23 +0530'
categories: embedded_computer
summary:  Hướng dẫn cài đặt
thumbnail: siteleaf.jpg
permalink: /:categories/orangepi-bai4-door-phone
---


## Make it announce itself in the network
- First things first. This should be the default. Incredibly it still isn't.

```
apt install -y avahi-daemon
cd /etc/avahi/services/
wget -c https://raw.githubusercontent.com/lathiat/avahi/master/avahi-daemon/sftp-ssh.service
wget -c https://raw.githubusercontent.com/lathiat/avahi/master/avahi-daemon/ssh.service
cd -
service avahi-daemon restart
```
- Bây giờ ta có thể accessed . ví dụ linux desktops under network as a "file share".


## Make it read only (using overlayroot)
- This package seems to exist only in the Ubuntu version of Armbian, not in the Debian one. On Debian, fsprotect or bilibop-lockfs can probably be used instead.

```
# On Debian I COULD NOT GET IT TO WORK USING THIS SO FAR, only on Ubuntu
# On Debian I get:
# Failure: overlayroot: missing kernel module overlayfs
# in early boot
# The "solutions" in
# https://forum.armbian.com/topic/1526-armbian-in-read-only-mode/
# are not really convincing/clean...
wget http://mirrors.kernel.org/ubuntu/pool/main/c/cloud-initramfs-tools/overlayroot_0.27ubuntu1_all.deb
sudo apt install busybox-static
sudo dpkg -i overlayroot_0.27ubuntu1_all.deb
sudo dpkg -f install

```

```
sudo apt update
sudo apt-get remove unattended-upgrades
sudo mv /usr/lib/apt/apt.systemd.daily /usr/lib/apt/apt.systemd.daily.DISABLED
sudo apt-get install overlayroot
echo 'overlayroot="tmpfs"' > /etc/overlayroot.conf
```

```
cd /media/root-ro
mount -t proc proc proc/
mount -t sysfs sys sys/
mount -o bind /dev dev/
overlayroot-chroot

```

## Audio 
- Check overlays at [https://docs.armbian.com/User-Guide_Allwinner_overlays/](https://docs.armbian.com/User-Guide_Allwinner_overlays/)

- Need to enable audio overlay

```
nano /boot/armbianEnv.txt
# Make sure to have these two lines as separate lines
overlay_prefix=sun8i-h3
overlays=analog-codec i2c0 spi-spidev uart1 uart2 usbhost2 usbhost3
```

## Radio



## Tham khảo :
- project door phone [here](https://github.com/gravaigu/doorphone.git)
- Hướng dẫn [here](https://gist.github.com/probonopd/97f6826cc5aa3c0c0950682b0bc266bc)



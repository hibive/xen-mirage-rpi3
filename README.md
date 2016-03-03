# Install Xen and MirageOS Environment on Rasperry Pi 3

## Aim

This document records attempts to get the Xen Hypervisor running on a RaspberryPi 3.

### Links
* [Raspberry Pi 3 on sale now](https://www.raspberrypi.org/blog/raspberry-pi-3-on-sale/)
  1.2GHz 64-bit quad-core ARM [Cortex-A53](http://www.arm.com/products/processors/cortex-a/cortex-a53-processor.php) CPU.
* [http://wiki.xenproject.org/wiki/Xen_ARM_with_Virtualization_Extensions](http://wiki.xen.org/wiki/Xen_ARM_with_Virtualization_Extensions)
  Seems to meet the requirements described on the Xen site.
* The Cubieboard seems to be a comparable machine and there is a
  method for running Xen, Ubuntu and Mirage on it.
  [Build an SDcard image for Xen/ARM, for a Cubieboard](https://github.com/mirage/xen-arm-builder)
  Could this be forked/modified for the RPi3?


## Current Attempt (Work in Progress _FAILING_):

[Ubuntu MATE for the Raspberry Pi 2 and Raspberry Pi 3](https://ubuntu-mate.org/raspberry-pi/)

Write image to an SD card in (OSX)
```sh
diskutil list
sudo dd bs=8m if=~/mirage-downloads/ubuntu-mate-15.10.3-desktop-armhf-raspberry-pi-2.img of=/dev/disk{{x}}
```

SSH on to Pi3:
```sh
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install vim
sudo apt-get install xen-hypervisor-4.5-armhf bridge-utils build-essential git
reboot
```

SSH in:
```sh
sudo xl list
# ERROR:  Can't find hypervisor information in sysfs!
```

[Can't find hypervisor information in sysfs!](https://xen-orchestra.com/blog/cant-find-hypervisor-information-in-sysfs/)

It doesn't appear that there is a grub bootloader on Raspberry Pi Ubuntu Mate.

U-Boot seems to be an alternative and is used on the Cubieboard image.


## To try:

* Try using/modifying the [xen-arm-builder](https://github.com/mirage/xen-arm-builder) image on RPi3
* [Ubuntu 14.04 LTS (Trusty Tahr) image for the Raspberry Pi 2](https://wiki.ubuntu.com/ARM/RaspberryPi)
* [Ubuntu Server for ARM](http://www.ubuntu.com/download/server/arm)

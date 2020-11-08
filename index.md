# Homepage

[Back to main page](..)

I started working on a port of UBports Ubuntu Touch on the Xperia 10 (kirin) after I got tired of using Sailfish OS and its app selection. This port is a Halium 9 port using the GSI, however, many modifications are required to install it even though it's a GSI. Here I document how to install and use Ubuntu Touch on this device. 

This port is experimental. It may or may not be daily driver ready, considering your needs. Normal phone functions (phone calls, data connection, SMS messages) are working properly. Features such as the fingerprint reader, media player, etc are not working. 

## Disclaimer

```
/*
 * After you install this, your warranty will be void.
 *
 * I am not responsible for bricked devices, dead SD cards,
 * thermonuclear war, or you getting fired because the alarm app failed. Please
 * do some research if you have any concerns about features included in this ROM
 * before flashing it! YOU are choosing to make these modifications, and if
 * you point the finger at me for messing up your device, I will laugh at you.
 */
 
```

When you unlock the bootloader (I won't go into that here) you WILL lose data and camera algorithms. 

## Prerequisites

* Sony Xperia 10 i3123 (tested) or other variants (should work) - but NOT Xperia 10 Plus
* Unlocked bootloader
* Stock android 9 ROM installed - Note: if you have Sailfish OS/Android 10/etc installd on your phone you need to install the Stock Android9 ROM. This will require using the Sony Emma tool which requires Windows.
* Carefulness and desire to learn

## How to Install

1. Boot TWRP
2. Install the boot.img from the GitHub releases
3. Install [halium-ramdisk.zip](https://build.lolinet.com/file/halium/GSI/tools/halium-ramdisk.zip), [apparmor-enabler.zip](https://build.lolinet.com/file/halium/GSI/tools/apparmor_enabler.zip), [Halium boot no console patch](https://build.lolinet.com/file/halium/GSI/tools/Halium-boot_no_console_patch.zip), and [latest GSI](https://build.lolinet.com/file/halium/GSI)
4. Reboot

## Problems and fixes

First check [the What works/what doesn't list](feature-list)

* Bluetooth not functioning: `sudo stop bluebinder && sudo start bluebinder`
* Wifi not functioning: move kernel modules to proper location, `depmod -a`, and add kernel module names in modules-load.d

## How to build kernel

**NOTE: The kernel sources are currently out of date because I messed up some apparmor files. The kernel sources in my kernel repo will cause some stuff to break, such as wifi.**

You might want to modify the kernel to get more features working. After you modify the kernel, compile it:

```
export CROSS_COMPILE=[YOUR CROSS COMPILER PATH]
export ARCH=arm64
export KBUILD_DIFFCONFIG=kirin_diffconfig

make clean O=./out
make mrproper
make sdm660-perf_defconfig O=./out ARCH=arm64 
./check-kernel-config out/.config -w # https://github.com/erfanoabdi/halium-boot/blob/halium-9.0/check-kernel-config
make -j16 O=./out
```

## Resources

* [Kernel](https://github.com/hengyedev/kirinkernel) **currently out of date**
* [UBports Project Homepage](https://ubports.com/)

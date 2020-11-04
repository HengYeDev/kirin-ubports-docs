# Homepage

[Back to main page](..)

## DIsclaimer

```
/*
 * Your warranty is now void.
 *
 * I am not responsible for bricked devices, dead SD cards,
 * thermonuclear war, or you getting fired because the alarm app failed. Please
 * do some research if you have any concerns about features included in this ROM
 * before flashing it! YOU are choosing to make these modifications, and if
 * you point the finger at me for messing up your device, I will laugh at you.
 */
 
```

## How to Install

1. Boot TWRP
2. Install the boot.img
3. Install [halium-ramdisk.zip](https://build.lolinet.com/file/halium/GSI/tools/halium-ramdisk.zip), [apparmor-enabler.zip](https://build.lolinet.com/file/halium/GSI/tools/apparmor_enabler.zip), [Halium boot no console patch](https://build.lolinet.com/file/halium/GSI/tools/Halium-boot_no_console_patch.zip), and [latest GSI](https://build.lolinet.com/file/halium/GSI)
4. Reboot

## Problems and fixes

* Bluetooth not functioning: `sudo stop bluebinder && sudo start bluebinder`
* Wifi not functioning: move kernel modules to proper location, `depmod -a`, and add kernel module names in modules-load.d

## How to build kernel

You might want to modify the kernel to get more features working. After you modify the kernel, compile it:

``
export CROSS_COMPILE=[YOUR CROSS COMPILER PATH]
export ARCH=arm64
export KBUILD_DIFFCONFIG=kirin_diffconfig

make clean O=./out
make mrproper
make sdm660-perf_defconfig O=./out ARCH=arm64 
./check-kernel-config out/.config -w # https://github.com/erfanoabdi/halium-boot/blob/halium-9.0/check-kernel-config
make -j16 O=./out

## Resources

* Kernel: https://github.com/hengyedev/kirinkernel

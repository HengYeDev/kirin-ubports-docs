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
3. Install (halium-ramdisk.zip)[https://build.lolinet.com/file/halium/GSI/tools/halium-ramdisk.zip], (apparmor-enabler.zip](https://build.lolinet.com/file/halium/GSI/tools/apparmor_enabler.zip), (Halium boot no console patch](https://build.lolinet.com/file/halium/GSI/tools/Halium-boot_no_console_patch.zip), and (latest GSI)[https://build.lolinet.com/file/halium/GSI]
4. Reboot

## Problems and fixes

* Bluetooth not functioning: `sudo stop bluebinder && sudo start bluebinder`
* Wifi not functioning: move kernel modules to proper location, `depmod -a`, and add kernel module names in modules-load.d

## Resources

* Kernel: https://github.com/hengyedev/kirinkernel

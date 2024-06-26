<img align="right" src="https://raw.githubusercontent.com/Xhdsos/Port-Windows-POCO-F5-RN12T/main/marble.png" width="425" alt="Windows running on POCO F5/Redmi Note 12 Turbo">

# Running Windows on the POCO F5/Redmi Note 12 Turbo

## Root guide

### Prerequisites
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [KernelSU](https://github.com/tiann/KernelSU/releases) > [Melt kernel](https://github.com/Pzqqt/android_kernel_xiaomi_marble/releases) > [Silvercore](https://github.com/karthick-kk/android_kernel_common_silvercore/releases)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modded TWRP](-)

##### Boot TWRP recovery
> If your recovery has been replaced back to stock, flash it again in fastboot with:
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

##### Backing up your boot image
> Sometimes flashing Magisk can cause a bootloop. To fix this, you'll need to restore a boot.img backup.

Use the TWRP backup feature to make a backup of the boot partition.
##### Flashing KernelSU
- Flash the AnyKernel3-android12-5.10.хх or Melt // Silvercore kernel with KernelSU support and reboot your phone. 
- Once booted, install the KernelSU app and open it.

Your phone succesfully rooted with kernelsu.
##### Flashing Magisk
- Flash the magisk.apk (you may have to rename it to magisk.zip) and reboot your phone. 
- Once booted, locate the Magisk app and open it.
- Follow any instructions provided. Select the direct install method if you are provided with several methods.

Your phone will now reboot, and you have succesfully rooted it with magisk.

> [!IMPORTANT]
> After you've rooted your phone, create a new boot.img backup in Android and in Windows (using the WOA Helper app) and remove any remaining boot.img backups you have made previously. If you don't do this, switching to Android will unroot your phone.
> 
> After updating or changing your rom (and rerooting) you will have to repeat all the steps on this page.

## Finished!

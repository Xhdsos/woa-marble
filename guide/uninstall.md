<img align="right" src="https://raw.githubusercontent.com/Xhdsos/Port-Windows-POCO-F5-RN12T/main/marble.png" width="425" alt="Windows running on POCO F5/Redmi Note 12 Turbo">

# Running Windows on the POCO F5/Redmi Note 12 Turbo

## Uninstallation

### Why is this needed?
If you want to uninstall windows this is used instead of deleting partitions manually to avoid human error + writing a whole dedicated guide to just uninstalling.

If you want to relock your bootloader you'll need your partition table to be stock.

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [Modded TWRP](-)
- [gpt_both0.bin](-)

### Uninstall instructions

# Method 1

> Boot to the TWRP recovery
```cmd
fastboot flash recovery path/to/twrp.img reboot recovery
```

#### Restore the partition layout
> [!Warning]
> This will wipe your Android files. Backup first if needed.

> Unmount all partitions via the mount menu on your phone
```cmd
adb shell restore
```
### Reboot to Android
```cmd
adb reboot 
```
## Done!

# Method 2

> [!Important]
> There is a very small chance this guide might not work if your partition table is completely fucked up. If you find yourself not being able to boot to recovery / Android after, you will have to reflash your device with EDL.


#### Boot into fastboot mode
> Hold the volume down + power button while the phone is turned off, or run the following command while it is booted
```cmd
adb reboot bootloader
```

#### Restore GPT
> Replace ```path\to\gpt_both0.bin``` with the path to the gpt_both0.bin file.

```cmd
fastboot flash partition:0 path\to\gpt_both0.bin
```

> [!Warning]
> Flash stock rom to avoid dead phone or edl

## Finished!














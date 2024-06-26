<img align="right" src="https://raw.githubusercontent.com/Xhdsos/Port-Windows-POCO-F5-RN12T/main/marble.png" width="425" alt="Windows running on POCO F5/Redmi Note 12 Turbo">

# Running Windows on the POCO F5/Redmi Note 12 Turbo

## Installing Windows

### Prerequisites
- [Windows on ARM image](https://worproject.com/esd)

- [Modded TWRP](-)
  
- [UEFI Image](-)

### Boot to TWRP recovery
> If your recovery has been replaced by the stock recovery, flash it again using
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Enabling mass storage mode

Use [Mass-Storage.zip](https://github.com/Robotix22/Mu-Qcom-Guides/files/11005130/Mass-Storage.zip) and copy it contents to a FAT32 Partition on your Device. <br />
After that boot the UEFI Image then it enters Windows Boot Manager select `Developer Menu` -> `USB Mass Storage Mode`. <br />

### Diskpart
> [!WARNING]
> DO NOT ERASE, CREATE OR OTHERWISE MODIFY ANY PARTITION WHILE IN DISKPART!!!! THIS CAN ERASE ALL OF YOUR UFS OR PREVENT YOU FROM BOOTING TO FASTBOOT!!!! THIS MEANS THAT YOUR DEVICE WILL BE PERMANENTLY BRICKED WITH NO SOLUTION! (except for taking the device to Xiaomi or flashing it with EDL, both of which will likely cost money)
```cmd
diskpart
```

#### Selecting the Windows partition
> Use `list volume` to find it, replace `$` with the actual number of **WINMARBLE**
```diskpart
select volume $
```

#### Add letter to Windows
```cmd
assign letter x
```

#### Selecting the ESP partition
> Use `list volume` to find it, replace `$` with the actual number of **ESPMARBLE**
```diskpart
select volume $
```

#### Add letter to ESP
```cmd
assign letter y
```

#### Exit diskpart
```cmd
exit
```

### Installing Windows
> [!Warning]
> DO NOT USE 24H2!!!

> Replace `path\to\install.esd` with the actual path of install.esd (it may also be named install.wim)

```cmd
dism /apply-image /ImageFile:path\to\install.esd /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:path\to\install.esd`, then replace `index:6` with the actual index number of **Windows 11 Pro** in your image

#### Create Windows bootloader files
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Enabling test signing
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Disabling recovery
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" recoveryenabled no
```

#### Disabling integrity checks
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" nointegritychecks on
```

### Unassign disk letters
> So that they don't stay there after disconnecting the device
```cmd
diskpart
```

#### Select the Windows volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **WINMARBLE**
```diskpart
select volume $
```

#### Unassign the letter X
```diskpart
remove letter x
```

#### Select the ESP volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **ESPMARBLE**
```diskpart
select volume $
```

#### Unassign the letter Y
```diskpart
remove letter y
```

#### Exit diskpart
```diskpart
exit
```

### Reboot to Android
> Hold **volume down** + **power** to force reboot your phone

## [Last step: Setting up dualboot](/guide/dualboot.md)


















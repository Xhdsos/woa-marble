<img align="right" src="https://raw.githubusercontent.com/Xhdsos/Port-Windows-POCO-F5-RN12T/main/marble.png" width="425" alt="Windows running on POCO F5/Redmi Note 12 Turbo">

# Running Windows on the POCO F5/Redmi Note 12 Turbo

## Installing Windows

### Prerequisites
- [Windows on ARM image](https://worproject.com/esd)

- [Modded TWRP](-)

### Boot to TWRP recovery
> If your recovery has been replaced by the stock recovery, flash it again using
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Installing WinPe

This Guide will show you how to Install Windows PE on your Device.

<table>
<tr><th>Table of Contents</th></th>
<tr><td>

- Installing Windows PE
    - [What's needed](#things-you-need)
    - [Installing](#installation)
        - [Method 1](#method-1-cust)
            - [Preparing](#preparing-step-1)
            - [Formating](#formating-cust-partition-step-2)
            - [Copy Files](#copying-windows-pe-files-step-3)

</td></tr> </table>

## Things you need:

- Windows PE (Recommended: - [WindowsPE](https://drive.google.com/file/d/1d-rGVm2Zk3-4mxaICWAz5LA3k3zIDkbA/view?usp=sharing))

## Installation

## Preparing (Step 1)

First of we need to prepare some things before we install Windows PE on our Device. <br />
Make sure you have an Custom Recovery installed on your Device and have ADB on your PC / Laptop. <br />
Download Windows PE and extract the zip File somewhere, where you can reach it.

## Formating Cust Partition (Step 2)

We will now format the cust Partition to FAT32:
```
mkfs.fat -F32 -s1 /dev/block/by-name/cust
```

## Copying Windows PE Files (Step 3)

After that we copy the Windows PE Files into cust. <br />
First mount cust with ADB Shell:
```
mkdir /cust
mount /dev/block/by-name/cust /cust
```
then use `adb push` to copy all Windows PE Files to cust:
```
adb push <Path to Windows PE Files> /cust/
```
After that it should contain `sources`, `efi` and `boot`. <br />
You have now successfully installed Windows PE.



### Installing Windows
> [!Warning]
> DO NOT USE 24H2!!!



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



## [Last step: Setting up dualboot](/guide/dualboot.md)


















<img align="right" src="https://raw.githubusercontent.com/Xhdsos/Port-Windows-POCO-F5-RN12T/main/marble.png" width="425" alt="Windows running on POCO F5/Redmi Note 12 Turbo">

# Running Windows on the POCO F5/Redmi Note 12 Turbo

## Reinstalling Windows

### Prerequisites
- [Windows on ARM image](https://worproject.com/esd)
  
- [UEFI image](-)

### Boot to the UEFI
> Replace `path\to\Mu-marble.img` with the actual path of the UEFI image
```cmd
fastboot boot path\to\Mu-marble.img
```


### Boot into Windows
Reboot your phone. If you end up in Android instead of Windows, flash the UEFI again using WOA Helper.

#### Setting up Windows
> Your device will now set up Windows. This will take some time. It will eventually reboot, and after that the initial setup (oobe) should launch.

> [!Note]
> To skip the Microsoft Account login, use "g" for the email and password. Windows will then let you make a local account

## Finished!

















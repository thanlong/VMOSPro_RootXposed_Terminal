## Description

<a href="https://youtu.be/hW93qhU4TA0"><img src="https://i.ytimg.com/vi_webp/hW93qhU4TA0/hqdefault.webp"/></a>


Root and Xposed is the Paid features of VMOS Pro. I hate having to purchase to get Root/Xposed, so I make a Terminal script instead and it is very easy to use!

This post will guide you how to root and install Xposed Framework on VM which is not GEEK ROM, so you needn't pay VIP service fee for VMOS or download another rooted ROM.  Not only root and install xposed but also unroot and uninstall xposed on any ROM.

 1. Download VMOS Pro Terminal Tool zip
 2. Import zip to VMOS Pro
 3. Use ES Files or any file manager app to copy `system` folder inside zip files to root path `/`
 4. Apply overwrite
 5. Then open Terminal Emulator or Material Terminal (available on Play Store)
 6. Type command: `chmod 777 /system/xbin/*` (set command to be executable!)
 7. Type `tool` command to open Tool

<img src="https://i.imgur.com/3XXA2Sy.png" />

 8. Type `root` command to root or unroot

<img src="https://i.imgur.com/FviSSe3.png" />

 9. Type `xposed` command to install/uninstall Xposed Framework

<img src="https://i.imgur.com/4xMi7fx.png" /> 

This script/tool can be used on VMOS, VMOS and any virtual machine (F1VM, VphoneGaga, X8Sandbox) with read-write system partition!

Only Superuser by Koush root supported, not Magisk or SuperSU.

Also, My GEEK ROM have Terminal Tool v1.3 pre-installed.


### Why can I add files to `/` path in VMOS?
System partition in vmos is read-write.
So i can add files to `/` without root.

### Does VMOS support Magisk?
VMOS currently doesn't supported Magisk because it doesn't have boot.img and recovery mode. Also VMOS cannot run magiskinit when replacing init.

### Superuser crash, lost root after reboot?

VMOS Dev may add some "sort of anti-piracy" to prevent you from installing root on non-Rooted ROM. This can be fixed by change root package: Open Terminal, type `root` then type `1` to change superuser package.


## VM Android version

Support Android 7.1, 5.1 and 4.4

## Download

SUHelper and Xposed Terminal now are in [VMOSPro_Terminal_Tool.zip](http://link1s.com/W2GN7)

## Changelogs

Always update!!!

v1.4: Add "Change root package". VMOS Pro will prevent you from installing root on non-rooted ROM by causing superuser app to crash because Root is not free. This option also change superuser app package from `com.koushikdutta.superuser` to `com.koushikdutta.sumasterz`!

v1.3: Create applet symlinks during Busybox installation.

v1.2: Update `root.sh` script. Add "Wipe dalvik-cache"

v1.1: Support Root and Xposed for Android 4.4

v1.0: SU Helper and Xposed are in VMOS Pro Terminal Tool. Add Busybox installer

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
 8. Type `root` command to root or unroot
 9. Type `xposed` command to install/uninstall Xposed Framework

Only Superuser by Koush root supported, not Magisk or SuperSU.
My GEEK ROM have Terminal Tool pre-installed!


### Why can I add files to `/` path in VMOS?
System partition in vmos is read-write.
So i can add files to `/` without root.

### Does VMOS support Magisk?
VMOS currently doesn't supported Magisk because it doesn't have boot.img and recovery mode. Also VMOS cannot run magiskinit when replacing init.

### Lost root after reboot?
Because VMOS Team may have added some sort of anti-piracy to cause Superuser to crash on 7.1 or prevent root from installing on non-GEEK ROMs so every boot you will need to type `root` to get root access!



## VM Android version

Support Android 7.1, 5.1 and 4.4

## Download

SUHelper and Xposed Terminal now are in [VMOSPro_Terminal_Tool.zip](http://link1s.com/W2GN7)

## Changelogs

v1.1: Add Root and Xposed for Android 4.4

v1.0: Add Busybox installer

## Description

<a href="https://youtu.be/hW93qhU4TA0"><img src="https://i.imgur.com/LDSRrFt.png"/></a>


Root and Xposed is the Paid features of VMOS Pro. I hate having to purchase to get Root/Xposed, so I make a Terminal script instead and it is very easy to use!

This post will guide you how to root and install Xposed Framework on VM which is not GEEK ROM, so you needn't pay VIP service fee for VMOS or download another rooted ROM.  Not only root and install xposed but also unroot and uninstall xposed on any ROM.

 1. Download VMOS Pro Terminal Tool zip
 2. Import zip to VMOS Pro
 3. Use ES Files or any file manager app to copy `system` folder inside zip files to root path `/`
 4. Apply overwrite
 5. Then open Terminal Emulator or Material Terminal (available on Play Store)
 6. Type command: `chmod 777 /system/xbin/*` (set command to be executable!)
 7. Type `tool` command to open Tool

<img src="https://i.imgur.com/kRuEqPJ.png" />

 8. Type `root` command to root or unroot

 9. Type `xposed` command to install/uninstall Xposed Framework

This script/tool can be used on any virtual machine with read-write system partition!

My GEEK ROM have Terminal Tool v1.8 pre-installed:

[Android 7.1.2 64-bit GEEK (gapps)](http://link1s.com/geQV5)

[Android 7.1.2 64-bit GEEK (vanilla)](http://link1s.com/VuBG)

[Android 7.1.2 32-bit GEEK (gapps)](http://link1s.com/13YlGTOA)

[Android 7.1.2 32-bit GEEK (vanilla)](http://link1s.com/LFzYlm)

[Android 5.1.1 32-bit GEEK (gapps)](http://link1s.com/h4w80)

[Android 5.1.1 32-bit GEEK (vanilla)](http://link1s.com/4o4k9)



### Why can I add files to `/` path in VMOS?
System partition in vmos is read-write.
So i can add files to `/` without root.

### Does VMOS support Magisk or SuperSU?

Only supports Superuser by Koush root, does not support Magisk or SuperSU.

VMOS currently doesn't supported Magisk because it doesn't have `boot.img` and recovery mode. Also VMOS cannot run `magiskinit` when replacing `init`.

VMOS may support Magisk in the future.


### Root installed but cannot grant root access

This maybe because daemon su is not running.
Try to shut down and restart the VM.

### Superuser crash, lost root after reboot?

This issue appears on VMOS Pro Global

VMOS Dev may add some "sort of anti-piracy" to prevent you from installing root on non-Rooted ROM. This can be fixed by change root package: After root and reboot, if you have Superuser crashed, you can open Terminal, type `root` then type `1` to change superuser package.

## How does it work?

This tool simply does these jobs.

Root: Push `su` binary to `/system/xbin` so that it can grant root permission to any app that call `su` command. 

Xposed: Run script to replace some files in system include `app_process`

Busybox: Push `busybox` binary to `/system/xbin` and create applet symlinks.

Uninstall: Delete and restore files

## VMOS Tool module (v1.8)

### About

VMOS Tool module is folder placed in `/sdcard/toolflash`, include `system` folder, `config.sh` and `custom.sh`

During installation, VMOS Tool will execute `config.sh` first.  If you list folders and files in `REMOVE_LIST`, VMOS Tool will delete these folders and files.  Then, if `IGNORE_PLACE` is set to false, VMOS Tool will copy all the files in the `system` directory to the `/system` directory.  Finally, the VMOS Tool will execute `custom.sh` if it is existed.
VMOS Tools module settings are summarized as follows:

Stage 1: Execute `config.sh` script

Stage 2: Copy files to `/system` (`IGNORE_PLACE`=false)

Stage 3: Execute `custom.sh` script

### How to install a module?


1. Install VMOS Pro Terminal Tool v1.8 if it's not installed!

2. Download `<custom_name>.zip` and import file to VMOS Pro

3. Extract `<custom_name>.zip` to `<custom_name>` folder

4. Copy `<custom_name>` folder to `/sdcard/toolflash/`

5. Open Terminal app, type `tool` to run VMOS Pro Terminal Tool, then type `6` (Enter) and `yes` (Enter) to install module.

`<custom_name>` is optional name and should only include only `abc123-_.` characters.

## VM Android version

Support Android 7.1, 5.1 and 4.4

## Download

SUHelper and Xposed Terminal now are in [VMOSPro_Terminal_Tool.zip](http://link1s.com/W2GN7)

## Changelogs

Always update!!!

v1.8: Add "Install VMOS Tool modules" function.

v1.7: "Change VMOS property" now is call "VMOS Props Config". Add Merge vmos.prop with build.prop (VMOS Props Config)

v1.6: Add "Change VMOS property". Change GPU Vendor, GPU Renderer and IMEI without reboot.

v1.5: Add "Check su binary" in SU Helper to check daemon root is running or not.

v1.4: Add "Change root package" in SU Helper. VMOS Pro will prevent you from installing root on non-rooted ROM by causing superuser app to crash because Root is not free. This option also change superuser app package from `com.koushikdutta.superuser` to `com.koushikdutta.sumasterz`!

v1.3: Create applet symlinks during Busybox installation.

v1.2: Update `root.sh` script. Add "Wipe dalvik-cache"

v1.1: Support Root and Xposed for Android 4.4

v1.0: SU Helper and Xposed are in VMOS Pro Terminal Tool. Add Busybox installer

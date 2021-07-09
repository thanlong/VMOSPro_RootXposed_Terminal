## Why did I write this script?

<a href="https://youtu.be/hW93qhU4TA0"><img src="https://i.imgur.com/LDSRrFt.png"/></a>


Root and Xposed is the Paid features of VMOS Pro. I hate having to purchase to get Root/Xposed, so I make a Terminal script instead and it is very easy to use!

**If your love VMOS Dev's work, you can pay monthly and yearly VIP. It's big effort so they can serve you with better experience**

## Installation

 1. Download VMOS Pro Terminal Tool zip
 2. Import zip to VMOS Pro
 3. Extract zip then use MT file manager and execute `config.sh` script or use any file manager app to copy `system` folder inside zip files to root path `/`. Apply overwrite
 5. Then open Terminal Emulator or Material Terminal (available on Play Store)
 6. Type command: `chmod 777 /system/xbin/*` (set command to be executable!)
 7. Type `tool` command to open Tool

<img src="https://i.imgur.com/fQlu8JL.png" />

 8. Type `root` command to root or unroot

 9. Type `xposed` command to install/uninstall Xposed Framework


This script/tool can be used on any virtual machine with read-write system partition!

My GEEK ROM have Terminal Tool pre-installed:

[Android 7.1.2 64-bit GEEK (gapps)](http://link1s.com/geQV5)

[Android 7.1.2 64-bit GEEK (vanilla)](http://link1s.com/VuBG)

[Android 7.1.2 32-bit GEEK (gapps)](http://link1s.com/13YlGTOA)

[Android 7.1.2 32-bit GEEK (vanilla)](http://link1s.com/LFzYlm)

[Android 5.1.1 32-bit GEEK (gapps)](http://link1s.com/h4w80)

[Android 5.1.1 32-bit GEEK (vanilla)](http://link1s.com/4o4k9)

### Functions

1. Superuser/Root: Root, remove root and check su binary.

2. Xposed Framework: Easy to install Xposed and uninstall it.

3. Busybox: Built-in Busybox at `/system/.tool/busybox/busybox` can be installed to `/system/xbin`

4. Wipe dalvik-cache

5. VMOS Props Config: Change VMOS property (GPU, IMEI) without reboot.

6. Install modifications ([VMOS Tool module](https://github.com/HuskyDG/VMOSPro_RootXposed_Terminal#vmos-tool-module-v18))

7. Mount real storage: Mount your device storage to `/sdcard/real_storage` or `/local_disk` in VMOS Pro so you can access your files in real phone storage (internal and external storage) from virtual machine. Note: Read-write external storage at `/sdcard/real_storage/storage/<sdcard_name>/Android/data/com.vmos.pro/`

8. Execute script on `late_start` (path: `/data/adb/script/late_start.d`) or `post-fs-data` (path: `/data/adb/script/post-fs-data.d`)

9. Use external storage as VM storage. 
   Expand your VM storage by using the memory card capacity as the virtual machine's `/sdcard` internal memory (without formatting).
   This feature will be very useful when you want to install a game with an obb file but you run out of internal memory.
   You can convert back to internal storage at any time.
   Don't worry! Data stored in memory card **won't** be lost during swapping

10. Install app into external storage (Coming soon)


### Benefits

Root your virtual machine without paying for VMOS Pro VIP. You don't need to download other rooted ROM. And you can un-root the VM easily.


### Why can I add files to `/` path in VMOS?
System partition in vmos is read-write with user permission.
So i can add files to `/` without root.

### Does VMOS support Magisk or SuperSU?

Only supports Superuser by Koush root, does not support Magisk or SuperSU.

VMOS currently doesn't supported Magisk because it doesn't have `boot.img` and recovery mode. Also VMOS cannot run `magiskinit` when replacing `init`.

VMOS may support Magisk in the future.

Magisk on VMOS project: https://github.com/HuskyDG/Magisk-on-VMOS

### Root installed but cannot grant root access

This maybe because daemon su is not running.
Type `getprop init.svc.daemonsu` to check daemonsu. Make sure `init.svc.daemonsu` is `running`, not `stopped` or `restart`.
Try to shut down and restart the VM.

### Superuser crash, lost root after reboot?

This issue appears on VMOS Pro Global

It won't allow you to use root if you are on free virtual machine.

Fix: Change root package

## How does rooting VM work?

This tool simply does these jobs.

Root: Push `su` binary to `/system/xbin` and launch daemon by `/system/xbin/su --daemon` command so that it can grant root permission to any app that call `su` command. 

Xposed: Run script to replace some files in system include `app_process`

Busybox: Push `busybox` binary to `/system/xbin` and create applet symlinks. Almost mods work on rooted devices need Busybox.

Uninstall: Delete and restore files

## VMOS Tool module (v1.8+)

### About

VMOS Tool module (modification) is folder placed in `/sdcard/toolflash`. It include `system` folder, `config.sh` and `custom.sh`. Support `post-fs-data` and `late_start` script.

VMOS Tool allows you to modify system in VM with simplest way!

VMOS Tools module installation are summarized as follows:

Stage 1: Execute `config.sh` script

Stage 2: Place files to `/system` when `IGNORE_PLACE=false`. If `APPLY_ON_BOOT=true`, instead of placing files to `/system` during installation, modifications of `/system` will be stored temporarily in `/data/adb/.boot/system` and it will apply `/system` changes only after reboot.

Stage 3: Execute `custom.sh` script

You can make a module / modification by youself and it is easy!
Download template here: [template_toolflash_mod.zip](https://github.com/HuskyDG/VMOSPro_RootXposed_Terminal/blob/main/template_toolflash_mod.zip?raw=true)


```
/sdcard/toolflash/
├── .
├── .
|
├── mymod.zip
│   ├── system/  #files in this folder will be added to /system
│   │
│   ├── config.sh   #script will be executed on the beginning
│   │
│   ├── custom.sh   #script will be executed after config.sh
│   │
│   ├── <your_post-fs-data_script_name>.sh
│   │
│   ├── <your_late_start_script_name>.sh
│
│ 
├── another_mod.zip
│   ├── .
│   └── .
├── .
├── .


```



`config.sh` (must have) is a script which is executed before `/system` is being writed.

Configure variables in `config.sh`:

```
# List folders and files here if you want to remove, this will overwrite values above!
REMOVE_LIST="

"

# == IGNORE PLACE ==
# Set to true of you don't want place any file into /system

IGNORE_PLACE=false

# == SCRIPT ==

# Input your post-fs-data script name here

POSTFSDATA=<your_post-fs-data_script_name>.sh 

# Input your late_start script name here

LATESTART=<your_late_start_script_name>.sh

# Set to true if you want to apply changes (replace or remove some files /system) only after boot 

APPLY_ON_BOOT=false

### YOUR SCRIPT
echo "- Mod by HuskyDG"

```

`system` folder include files and folders that will write to `/system`

`custom.sh` is a script which is executed after `config.sh`.


### How to install a module?

No need to extract zip file to `/sdcard/toolflash/` anymore!

1. Need VMOS Pro Terminal Tool v1.15+

2. Place your mod `.zip` file at `/sdcard/toolflash/`

3. Open Terminal app, type `tool` then `6` (Enter) and `yes` (Enter) to install mods.

## Supported VM & Android version
### Supported

Virtual machine with Read-write `/system`

VMOS Pro Chinese & Global: Android 7.1.2, 5.1.1 and 4.4.4

VMOS Pro from Google Play Store: Android 7.1.2

VMOS old version: Android 5.1.1

F1VM & X8 Sandbox: Maybe?

Virtual Android: You are not able to root this VM because `daemonsu` can't launch.

### Not supported

F1VM Lite from Google Play Store (Read-only system): You are not able to change any thing in `/system`.

VphoneGaga (Read-only system): You are not able to change any thing in `/system` even you granted root access.


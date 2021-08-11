## About

<a href="https://youtu.be/hW93qhU4TA0"><img src="https://i.imgur.com/LDSRrFt.png"/></a>


A simple scripting tool that gives you useful features. Add or remove Root and Xposed Framework, Busybox, etc. without paying for VMOS Pro VIP 😎

## Installation

Watch video: https://youtu.be/N8A183ELU3Y

 1. Download VMOS Pro Terminal Tool zip
 2. Import zip to VMOS Pro
 3. Extract zip then use any file manager app to copy `system` folder inside zip files to root path `/`. Apply overwrite
 5. Then open any Terminal app (available on Play Store)
 6. Type command: `chmod 777 /system/xbin/*` (set command to be executable, do this once)
 7. Type `tool` command to open Tool

<img src="https://i.imgur.com/O8NQvMl.png" />


Download my GEEK ROM with Terminal Tool pre-installed:

[HuskyDG/VMOSPro_ROM](https://github.com/HuskyDG/VMOSPro_ROM)

## Functions

### **SU Helper**
Install/uninstall root: Tool can help you to root or unroot your VM. Support rooting Android 4.4 ROM VM.

Hide root access: `su` binary is hidden (deleted temporarily)

Change root package: change package of Superuser app and `su` binary.

Root checker: Check if `su` binary is working properly.

### **Xposed Framework**
Tool can help you to install or uninstall Xposed Framework on VM.

### **Busybox**
Built-in Busybox at `/system/.tool/busybox/busybox` can be installed to `/system/xbin`

### **Wipe dalvik-cache**
Free up your memory space temporarily, note that the next boot will take long time.

### **VMOS Props Config**

Change VMOS property (GPU, IMEI) without reboot, unlock PUBG Mobile max settings.

### **Install modifications** 
[See "VMOS Tool modification"](https://github.com/HuskyDG/VMOSPro_RootXposed_Terminal#vmos-tool-modification-zip-v18)

### **Mount real storage**
Your real device storage can be mounted to `/sdcard/real_storage` or `/local_disk` in VMOS Pro. Access your files in real phone storage (internal and external storage) from virtual machine. Note: Read-write external storage at `/sdcard/real_storage/storage/<sdcard_name>/Android/data/com.vmos.pro/`

### **Init script**
Execute script on `late_start` (path: `/data/adb/script/late_start.d`) or `post-fs-data` (path: `/data/adb/script/post-fs-data.d`)

### **Use external SD Card as VM storage**
Expand your VM storage by using the memory card capacity as the virtual machine's `/sdcard` internal memory.
You can revert back to internal storage at any time.
   
<img src="https://i.imgur.com/OQZydzV.png"/>

### **Dual space**
Create second space, switch between two space easily. Two independent space on one virtual space. You can clear data on dual space.

<img src="https://i.imgur.com/PjNnCqw.png"/>

### **Google Services** 

Easy to install or uninstall Google Services


## FAQ

### Why can I add files to `/` path in VMOS?
System partition in vmos is read-write with user permission.
So i can add files to `/` without root.

### Does VMOS support Magisk or SuperSU?

Only supports Superuser by Koush root, does not support Magisk or SuperSU.

VMOS currently doesn't supported Magisk because it doesn't have `boot.img` and recovery mode. Also VMOS cannot run `magiskinit` when replacing `init`.

VMOS may support Magisk in the future.

Magisk on VMOS project: https://github.com/HuskyDG/Magisk-on-VMOS


### Root installed but cannot grant root access

This maybe because **daemon su process** is **not running** as **ROOT**.

<img src=https://i.imgur.com/RSGtxK7.jpg/>

Root status must be `running`, not `stopped` or `restarting`.
Run `root` command to check root status.

Fix: Shut down and restart your virtual machine. This can solve the problem.

### Superuser app keeps crash or lost root after reboot?

<img src="https://i.imgur.com/dsw2DfD.jpg"/>

This issue appears on VMOS Pro Global

It won't allow you to use root if you are on **free virtual machine**.

Fix: Type `root` command then **Change root package**


## VMOS Tool modification zip (v1.8+)

### About

Because VMOS Pro doesn't have Recovery mode, Modification zip is alternative way of flashable recovery zip which allows you to apply changes into system as you want. Example: Change boot animation, remove some app, change system user interface,...

You are recommended to make a modification zip instead of making custom ROM because it can import everything you need to add or remove into ROM.


### Create mods


1. Download template here: [template_toolflash_mod.zip](https://github.com/HuskyDG/VMOSPro_RootXposed_Terminal/blob/main/template_toolflash_mod.zip?raw=true)

2. Extract template file.

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


3. Place your files that you want to replace in `/system` in `system` folder.

4. `config.sh` (must have) is a script which is executed before `/system` is being writed.

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
# Write your script here ...
echo "- Mod by HuskyDG"

```

5. `custom.sh` is a script which is executed after `config.sh`.

6. Finally, compress all files and folders into a zip file. Now you have a Modification zip, you can flash it to apply your changes into any virtual machine.

### How to install a module?

No need to extract zip file to `/sdcard/toolflash/` anymore!

1. Need VMOS Pro Terminal Tool v1.15+

v1.18 add **Flash a zip by path**

2. **Flash all zip in /sdcard/toolflash** Place your mod `.zip` file at `/sdcard/toolflash/`, open Terminal app, type `tool` command then `6` (Enter) and `1` (Enter) to install mods.

3. **Flash a zip by path** Open Terminal app, type `tool` command then `6` (Enter) and `2` (Enter) then type your zip path (Example: `/sdcard/Download/mymod.zip`)

## Supported VM & Android version
### Supported

Virtual machine with Read-write `/system`

VMOS Pro Chinese & Global: Android 7.1.2, 5.1.1 and 4.4.4

VMOS Pro from Google Play Store: Android 7.1.2

VMOS old version: Android 5.1.1

Virtual Android: You are not able to root this VM because `daemonsu` can't launch.

### Not supported

F1VM, X8 Sandbox, VphoneGaga (Read-only system): You are not able to change any thing in `/system` even you granted root access.


## Download


Download tool from [MEGA](http://link1s.com/W2GN7) or [Mediafire](http://link1s.com/VMOSTool)


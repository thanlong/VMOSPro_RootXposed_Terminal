## About

<a href="https://youtu.be/hW93qhU4TA0"><img src="https://i.imgur.com/LDSRrFt.png"/></a>


A simple scripting tool that gives you useful features. Add or remove Root and Xposed Framework, Busybox, etc. without paying for VMOS Pro VIP 😎

<img src="https://i.imgur.com/Az9a6rH.jpg" width="70%"/>


## Installation

### VMOS Pro Chinese v1.0.0 - v1.2.3

Watch video: https://youtu.be/N8A183ELU3Y

 1. Download `vmostool.zip`
 2. Import zip to VMOS Pro
 3. Extract zip then use any file manager app to copy `system` folder inside zip files to root path `/`. Apply overwrite
 5. Then open any Terminal app (available on Play Store)
 6. Type command: `chmod 777 /system/xbin/*` (set command to be executable, do this once)
 7. Type `tool` command to open Tool



### VMOS Pro Chinese v1.3.1 - above

Because `/system` is locked at Read-only on VMOS Pro from v1.3.1 and above, your cannot copy/move anything to `/system` without Root access.

 1. Download `vmostool_systemless.zip` and extract it to `vmostool_systemless` folder
 2. If you want to install tool into the installed virtual machine, back up your ROM, after that you can find it at `/sdcard/vmospro/backup`.
    Place your ROM to `/sdcard/vmospro/backup`
 3. Notice about the path to `vmostool_systemless` folder

    Example, I download `vmostool_systemless.zip` to `/sdcard/Download` folder and extract it to `/sdcard/Download/vmostool_systemless`. 
    I have backup Android 7.1.2 64 bit ROM

 4. Run follow command in Terminal app (on your phone not virtual machine)

```
cd /sdcard/Download/vmostool_systemless
sh patch.sh
```

Now, Terminal will start to patch your ROM. On your Terminal will like this:

<img src="https://i.imgur.com/RSd4QSj.jpg"/>


After that you can recovery ROM and tool will be installed. Run `tool` command to open tool.
    
   
 
### ROM with VMOSTool

Download my GEEK ROM with Terminal Tool pre-installed:

[HuskyDG/VMOSPro_ROM](https://github.com/HuskyDG/VMOSPro_ROM)

## Functions

### **SU Helper**
Install/uninstall root: Tool can help you to root or unroot your VM. Support rooting Android 4.4 ROM VM.

Hide root access: `su` binary is hidden (deleted temporarily)

Fix Superuser crash: change package of Superuser app and `su` binary.

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

### **SD Card Tool**
Expand your VM storage by using the memory card capacity as the virtual machine's `/sdcard` internal memory.

Move installed to SD Card

- Mount readable sdcard to `/mnt/asec` - the location where you store apps on SD Card
- Some app will not work properly if it is moved to SD Card
- If you discarded SD Card then boot the virtual machine, the apps that you moved to SD Card will be uninstalled [ Be careful ]
 
<img src="https://i.imgur.com/OQZydzV.png"/>

### **Dual space**
Create second space, switch between two space easily. Two independent space on one virtual space. You can clear data on dual space.

<img src="https://i.imgur.com/PjNnCqw.png"/>

### **Google Services** 

Easy to install or uninstall Google Services


## VMOS Tool modification zip (v1.8+)

### About

Because VMOS Pro doesn't have Recovery mode, Modification zip is alternative way of flashable recovery zip which allows you to apply changes into system as you want. Example: Change boot animation, remove some app, change system user interface,...

You are recommended to make a modification zip instead of making custom ROM because it can import everything you need to add or remove into ROM.


### Create mods


1. Download template here: [template_toolflash_mod.zip](https://github.com/HuskyDG/VMOSPro_RootXposed_Terminal/blob/main/template_toolflash_mod.zip?raw=true)

2. Extract template file.

<img src="https://i.imgur.com/Xs7TJBz.png"/>


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

# From Terminal Tool v1.20 and above, APPLY_ON_BOOT is always actived even you set to false

APPLY_ON_BOOT=true

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

4. **Flash a zip by call command**

```
source utils
install_mod path/to/zip
```

## Supported VM & Android version
### Supported

Virtual machine with Read-write `/system`

VMOS Pro Chinese v1.0.0 - v1.2.3

VMOS Pro Global

VMOS Pro from Google Play Store: Android 7.1.2

VMOS old version: Android 5.1.1

Virtual Android: You are not able to root this VM because `daemonsu` can't launch.

### Not supported

F1VM, X8 Sandbox, VphoneGaga (Read-only system): You are not able to change any thing in `/system` even you granted root access.

## Download


Download tool from [MEGA](http://link1s.com/W2GN7) or [Mediafire](http://link1s.com/VMOSTool)

Tool will be automatically updated after reboot

## About

<a href="https://youtu.be/hW93qhU4TA0"><img src="https://i.imgur.com/LDSRrFt.png"/></a>


A simple scripting tool that gives you useful features: Root and Xposed Framework, Busybox, v.v

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

**Direct install**
1. Download `vmostool_systemless.zip`
2. Import it to VMOS Pro, then you can find it at `/sdcard/VMOSfiletransferstation` path
3. Extract it to `vmostool_systemless` folder
4. Run command on Material Terminal app (example if files are at `/sdcard/VMOSfiletransferstation/vmostool_systemless`):

```
sh /sdcard/VMOSfiletransferstation/vmostool_systemless/vmos.sh
```
5. Reboot the virtual machine.

**Install into ROM zip**

Watch video: https://youtu.be/uQsPoYyLm5c

 1. Download `vmostool_systemless.zip` and extract it to `vmostool_systemless` folder
 2. If you want to install tool into the installed virtual machine, back up your ROM, after that you can find it at `/sdcard/vmospro/backup`.
    Place your ROM to `/sdcard/vmospro/backup`
 3. Notice about the path to `vmostool_systemless` folder

    Example, I download `vmostool_systemless.zip` to `/sdcard/Download` folder and extract it to `/sdcard/Download/vmostool_systemless`. 
    I have backup Android 7.1.2 64 bit ROM

 4. Run follow command in Terminal app (on your phone not virtual machine)
    
    Remember to grant Terminal app **Storage** permission
```
cd /sdcard/Download/vmostool_systemless
sh patch.sh
```
Or
```
sh /sdcard/Download/vmostool_systemless/patch.sh
```


Now, Terminal will start to patch your ROM. On your Terminal will like this:

<img src="https://i.imgur.com/RSd4QSj.jpg"/>


After that you can recovery ROM and tool will be installed. Run `tool` command to open tool.
 

### VphoneGaga 2.1.3 (with Magisk)
Read here https://github.com/HuskyDG/Magisk-on-VphoneGaga
 
### ROM with VMOSTool

Download my GEEK ROM with Terminal Tool pre-installed:

[HuskyDG/VMOSPro_ROM](https://github.com/HuskyDG/VMOSPro_ROM)

## Functions

### **SU Helper**
Enable Root to grant Superuser permission to any apps, also hide superuser binary temporarily.

Athough virtual machine systemfiles can be modified without performing root access but many root-needed apps work on the way only pass command though `su` command.

VMOS cannot run Magisk properly

### **Xposed Framework**
Install or uninstall Xposed on virtual machine. 

Note: Xposed Framework will make system boot longer, waste much RAM or slow performance down.

### **Busybox**
Built-in Busybox at `/tool_files/main/exbin/busybox` can be installed to `/system/xbin`

### **Wipe dalvik-cache**

VMOS waste too much your memory...

Free up your memory space temporarily, note that the next boot may take long time (if you have installed Xposed Framework, it will longer than normal!)

### **VMOS Props Config**

Override GPU, IMEI immediately without reboot, unlock game max settings.

### **Install modifications** 
[See "VMOS Tool modification"](https://github.com/HuskyDG/VMOSPro_RootXposed_Terminal#vmos-tool-modification-zip-v18)

### **Mount real storage**
Your real device storage can be mounted to `/sdcard/real_storage` or `/local_disk` in VMOS Pro. Allow you to access your files in real phone storage (internal and external storage) through virtual machine.

### **Init.d script support**
Execute script on `late_start` (path: `/data/adb/script/late_start.d`) or `post-fs-data` (path: `/data/adb/script/post-fs-data.d`)

### **SD Card Tool**
Expand your VM storage by using the memory card capacity as the virtual machine's `/sdcard` internal memory.

Force move any installed apps to SD Card to gain your Internal memory capacity

- Mount readable sdcard to `/mnt/asec` - the location where you store apps on SD Card
- Some app will not work properly if it is moved to SD Card
- If you discarded SD Card then boot the virtual machine, the apps that you moved to SD Card will be uninstalled [ Be careful ]
 
<img src="https://i.imgur.com/OQZydzV.png"/>

### **Dual space**
Create second space, switch between two space easily. Two independent space on one virtual space. You can clear data on dual space.

<img src="https://i.imgur.com/PjNnCqw.png"/>

### **Google Services** 

Install Google Services on any virtual machine.

After your enable Google Services in settings, you cannot turn it off. Tool can uninstall Google Services when you don't need it anymore...

### Backup data

Do you know you can import data from a virtual machine to another virtual machine. VMOS Pro provide you with **Backup virtual machine** (known as **Backup ROM**) which backup entire systemfiles. Everytime you backup ROM, it waste too much your memory.

This function only backup `/data` (not include dalvik-cache) as modification zip. It is lighter than backup ROM. You can flash zip on any virtual machine to restore your data.


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

VphoneGaga (Root with Magisk)

Virtual Android: You are not able to root this VM because `daemonsu` can't launch.

### Not supported

F1VM, X8 Sandbox (Read-only system): You are not able to change any thing in `/system` even you granted root access.

## Download


Download tool from [MEGA](http://link1s.com/W2GN7) 

Tool will be automatically updated after reboot

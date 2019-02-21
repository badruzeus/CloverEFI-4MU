# CloverEFI-4MU
### Introduction 
First, I have to tell that Clover binary used on this repo is same as what you could get from <b>Official SourceForge</b> [here](https://sourceforge.net/projects/cloverefiboot/files/Bootable_ISO/). The differences maybe compiler and host version (I use Xcode 8.2.1 under Mac OS X 10.11.6) for build process. So, it definitely is able to boot OS X as well (if your mach is Hackintosh compatible, with advanced configs for sure).
 
But, I decided to create a separated topic for answering a question: "How to use Clover w/o installing macOS on PC with UEFI firmware?". As we've known, provided Clover [Package](https://en.wikipedia.org/wiki/.pkg) is installable only on a Hackintosh based with macOS running.
 
Simply, <b>"CloverEFI-4MU"</b> as project here's: Clover bootloader for non-Hackintosh-able UEFI PC with Manual installation via Ubuntu Linux, using minimalized sample config, efi drivers, etc. I make it to be specific with UEFI only for easier configs compared to Legacy (though with GUID Partition Scheme: GPT, is actually able to.. but I don't wanna mess your current legacy bootloader settings), as well as via Ubuntu is to keep focus on guides. Uploaded ["CLOVER"](https://github.com/badruzeus/CloverEFI-4MU/CLOVER) folder is just for guide supplement.

--------------------------------------------------------------------------------------------

### What is Clover?
<img src="/img/CloverEFI-Bootloader.png?raw=true" alt="Clover EFI Bootloader" align="right">

Clover is one of bootloaders developed by Slice, Apianti, BlackOSX, Dmazar, Blusseau, and other devs with great community for booting OS X, Windows and Linux on Mac or PC with UEFI / BIOS firmware.
 
Some of Clover features are:
- [x] Supports for booting OS X, Windows and Linux (Android x86 as well)
- [x] Running on Legacy BIOS (MBR, GPT) or UEFI firmware (GPT only)
- [x] Customizable GUI including themes, icons, fonts, background images, animations, and mouse pointers.
- [x] ... and much more. [Here's](https://sourceforge.net/projects/cloverefiboot/) for details.

--------------------------------------------------------------------------------------------

### Requirements
However, following this project you have to meet conditions below:
- [x] Only for PC (Desktop / Laptop) with UEFI firmware capable: Check your BIOS Features
- [x] Make sure that your PC is able to reach Clover GUI:
      Create USB Clover with [this Tool](http://cvad-mac.narod.ru/index/bootdiskutility_exe/0-5) via Windows.
      <p>Then boot from it for testing purpose (UEFI Mode)
- [x] Basic knowledge about bootloader and UEFI / BIOS settings
- [x] Pre-installed Ubuntu Linux (and it's flavours) or Live Mode
- [x] Make a backup of whole "Internal EFI Partition" is highly recommended.

--------------------------------------------------------------------------------------------

### How to Use
1. Clone or Download whole repo: $ `git clone https://github.com/badruzeus/CloverEFI-4MU`
2. My Clover Themes collection: $ `git clone https://github.com/badruzeus/MyCloverThemes` (Optional)
   - Go to [docs](https://github.com/badruzeus/CloverEFI-4MU/blob/master/docs/How-to-use-Clover-Themes.txt) for Theming how to
3. Then, just follow provided ["Video Tutorial"](https://www.youtube.com/watch?v=YPWWinxwOcY) below: (be really carefull when accessing EFI Partition with root access)
 
   [![CloverEFI-4MU](https://github.com/badruzeus/CloverEFI-4MU/raw/master/img/CloverEFI-4MU.png)](https://www.youtube.com/watch?v=YPWWinxwOcY)

   Video Chapters:
   - GUID Partition Scheme (GPT) with EFI Partition
   - Cloning the repos using git via Terminal
   - Manually placing "CLOVER" to EFI Partition using Nautilus (root)
   - Clover GUI configurations: Create Custom Entries for Windows, Ubuntu and PhoenixOS
   - Hiding Legacy (non-bootable) Volumes for UEFI
   - Setting up "Native Screen Resolution"
   - Clover Theme installation
   - Save "/EFI/CLOVER/config.plist" changes
   - Adding "CLOVER" as New Boot Entry on UEFI firmware
   - Setting up "CLOVER" as 1st Boot order
   - Rebooting PC and Boot with Clover
   - Clover Themes preview (with animations)
   - Done! Congratulations; Try Clover before you die!

--------------------------------------------------------------------------------------------

### Legacy-GPT Installation
Assummed "Target_Disk" is /dev/sda (Whole Disk) and "Target_Partition" is /dev/sda1 (EFI System Partition).
<br>Check with Terminal: `$ sudo blkid` or `sudo fdisk -l`<br/>
1. Clone the repo, located on ~/CloverEFI-4MU (Home)
2. Run these Terminal commands:
   
   // <i>Marking /dev/sda as active partition (also useful for MBR scheme)</i>
   - $ `cd ~/CloverEFI-4MU/BootSectors`
   - $ `sudo dd if="/dev/sda" bs=512 count=1 >origMBR`
   - $ `cp origMBR newMBR`
   - $ `sudo dd if=boot0af of=newMBR bs=440 count=1 conv=notrunc`

   // <i>Set /dev/sda1 as Primary Boot Record (PBR)</i>
   - $ `sudo dd if="/dev/sda1" bs=512 count=1 >origPBR`
   - $ `cp boot1f32 newPBR`
   - $ `sudo dd if=origPBR of=newPBR skip=3 seek=3 bs=1 count=87 conv=notrunc`

   // <i>Writing bootsector's changes</i>
   - $ `sudo dd if=newPBR of="/dev/sda1" bs=512 count=1`
   - $ `sudo dd if=newMBR of="/dev/sda" bs=512 count=1 conv=nocreat,notrunc`

3. Installing Clover on EFI System Partition (ESP)
   <br>(Please note that `\EFI\BOOT` dir is not always empty, some linux distros maybe placing `grub, kernel or ramdisk` here. If this is your case, just copy `BOOTX64.efi` file, not replacing a whole dir).<br/>

   (a) Option 1 via Command Line
   <br>// <i>Mounting EFI System Partition</i><br/>
   - $ `cd ~/`
   - $ `mkdir esp`
   - $ `sudo mount -t vfat /dev/sda1 esp`

   // <i>Copying Clover required files (BOOT & CLOVER)</i>
   - $ `cd ~/CloverEFI-4MU`
   - $ `sudo cp boot ~/esp`
   - $ `sudo cp -r EFI/BOOT ~/esp/EFI`
   - $ `sudo cp -r EFI/CLOVER ~/esp/EFI`

   (b) Option 2 via File Manager (GUI)
   - Mount ESP as point (a) first
   - Terminal: $ `sudo [FileManager]` // File manager could be nautilus, thunar, etc.
   - Manually copy-paste required files as point (a), be careful!
   - Terminal: $ `sudo umount ~/esp` (if all have done).

--------------------------------------------------------------------------------------------

### Bugs & Troubleshooting
- [ ] Press "F1" for Clover Help (Shortcut keys, Functions, etc.)
- [ ] Depends on your UEFI firmware, for adding CLOVER as "New Boot Entry" is usually:
   - `fs0:\efi\clover\cloverx64.efi` or
   - `\efi\clover\cloverx64.efi`

- [ ] Phoenix or InsydeH2O maybe not including "Boot" Entry Option on it's firmware (BIOS). On this case, you need manually adding Entry via UEFI Shell. For example adding Clover Entry located on FS0 (could be FS1, FS2 etc. depends on ESP):
<br> > `map FS*`<br/>
<br> > `bcfg boot dump`<br/>
<br><i>// If `02` is last Boot Entry, add Clover on `03`:</i><br/>
<br> > `bcfg boot add 03 FS0:\EFI\CLOVER\CLOVERX64.efi "Clover EFI Bootloader"`<br/>
<br> <i>// OFC, you could add another entries eg. Windows Boot Manager, Linux Grub2, etc. on 04, 05..</i><br/>
<br> If Clover is not set as 1st boot order, you need pressing Combo key (could be F12, Esc, etc) and manually select it once computer powered on.<br/>

- [ ] If you're unable to run "EFI Shell" from BIOS, place "SHELLX64.EFI" on your ESP root (not EFI dir).
<br>Some old AMI Aptio firmwares (eg. v2.00) need this.<br/>

- [ ] Still having trouble accessing Shell via Firmware? Install Clover to Bootable USB FlashDisk using BDUtility.exe under Windows then boot from it. Run UEFI Shell provided by Clover.

--------------------------------------------------------------------------------------------

### Credits
[Apple](https://www.apple.com) | [Canonical](https://www.ubuntu.com) | [Microsoft](https://www.microsoft.com/en-us/windows) | [Clover](https://sourceforge.net/projects/cloverefiboot) | [cvad](http://cvad-mac.narod.ru/index/bootdiskutility_exe/0-5) | [fusion71au](http://www.insanelymac.com/forum/topic/310038-manually-install-clover-and-configure-boot-priority-with-easyuefi-in-windows/#entry2200235) | [InsanelyMac](https://www.insanelymac.com/forum), [Olarila](http://olarila.com/forum) and [OSXLatitude](https://osxlatitude.com/forums) Forum.
 
 
:: <i>Follow me on [AppleLife](https://www.applelife.ru/members/badruzeus.112558/) / [Facebook](https://fb.com/badruzeus) / [InsanelyMac](https://www.insanelymac.com/forum/profile/826765-badruzeus) / [MacRumors](https://forums.macrumors.com/members/badruzeus.1133819/) /  [Reddit](https://www.reddit.com/user/Badruzeus) / [SourceForge](https://sourceforge.net/u/badruzeus/profile) / [Youtube](https://www.youtube.com/channel/UCM2mZ2r2Gy914X-3N18b6qA)</i> ::

# CloverEFI-4MU
### Introduction 
First, I have to tell that Clover binary used on this repo is same as what you could get from <b>Official SourceForge</b> [here](https://sourceforge.net/projects/cloverefiboot/files/Bootable_ISO/). The differences maybe compiler and host version (I use Xcode 8.2.1 under Mac OS X 10.11.6) for build process. So, it definitely is able to boot OS X as well (if your mach is Hackintosh compatible, with advanced configs for sure).
 
But, I decided to create a separated topic for answering a question: "How to use Clover w/o installing macOS on PC with UEFI firmware?". As we've known, provided Clover [Package](https://en.wikipedia.org/wiki/.pkg) is installable only on a Hackintosh based with macOS running.
 
Simply, <b>"CloverEFI-4MU"</b> as project here's: Clover bootloader for non-Hackintosh-able UEFI PC with Manual installation via Ubuntu Linux, using minimalized sample config, efi drivers, etc. I make it to be specific with UEFI only for easier configs compared to Legacy (though with GUID Partition Scheme: GPT, is actually able to.. but I don't wanna mess your current legacy bootloader settings), as well as via Ubuntu is to keep focus on guides. Uploaded ["CLOVER"](https://github.com/badruzeus/CloverEFI-4MU/CLOVER) folder is just for guide supplement.

### What is Clover?
<img src="/img/CloverEFI-Bootloader.png?raw=true" alt="Clover EFI Bootloader" align="right">

Clover is one of bootloaders developed by Slice, Apianti, BlackOSX, Dmazar, Blusseau, and other devs with great community for booting OS X, Windows and Linux on Mac or PC with UEFI / BIOS firmware.
 
Some of Clover features are:
- [x] Supports for booting OS X, Windows and Linux (Android x86 as well)
- [x] Running on Legacy BIOS (MBR, GPT) or UEFI firmware (GPT only)
- [x] Customizable GUI including themes, icons, fonts, background images, animations, and mouse pointers.
- [x] ... and much more. [Here's](https://sourceforge.net/projects/cloverefiboot/) for details.
 
### Requirements
However, following this project you have to meet conditions below:
- [x] Only for PC (Desktop / Laptop) with UEFI firmware capable: Check your BIOS Features
- [x] Make sure that your PC is able to reach Clover GUI:
      Create USB Clover with [this Tool](http://cvad-mac.narod.ru/index/bootdiskutility_exe/0-5) via Windows.
      <p>Then boot from it for testing purpose (UEFI Mode)
- [x] Basic knowledge about bootloader and UEFI / BIOS settings
- [x] Pre-installed Ubuntu Linux (and it's flavours) or Live Mode
- [x] Make a backup of whole "Internal EFI Partition" is highly recommended.

### How to Use
1. Clone or Download whole repo: $ `git clone https://github.com/badruzeus/CloverEFI-4MU`
2. My Clover Themes collection: $ `git clone https://github.com/badruzeus/MyCloverThemes` (Optional)
   - Go to [docs](https://github.com/badruzeus/CloverEFI-4MU/blob/master/docs/How-to-use-Clover-Themes.txt) for Theming how to
3. Then, just follow provided ["Video Tutorial"](https://youtu.be/YPWWinxwOcY) below: (be really carefull when accessing EFI Partition with root access)
 
   [![CloverEFI-4MU](https://github.com/badruzeus/CloverEFI-4MU/raw/master/img/CloverEFI-4MU.png)](https://youtu.be/YPWWinxwOcY)

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
 
### Bugs & Troubleshooting
- [ ] Press "F1" for Clover Help (Shortcut keys, Functions, etc.)
- [ ] Provided "ShellX64U.efi" is not accessible for some UEFI firmwares
- [ ] Depends on your UEFI firmware, for adding CLOVER as "New Boot Entry" is usually:
   - `fs0:\efi\clover\cloverx64.efi` or
   - `\efi\clover\cloverx64.efi`
- [ ] More linux distros support is coming soon..
 
 
### Credits
[Apple](https://www.apple.com) | [Canonical](https://www.ubuntu.com) | [Microsoft](https://www.microsoft.com/en-us/windows) | [Clover](https://sourceforge.net/projects/cloverefiboot) | [cvad](http://cvad-mac.narod.ru/index/bootdiskutility_exe/0-5) | [fusion71au](http://www.insanelymac.com/forum/topic/310038-manually-install-clover-and-configure-boot-priority-with-easyuefi-in-windows/#entry2200235) | [InsanelyMac](https://www.insanelymac.com/forum), [Olarila](http://olarila.com/forum) and [OSXLatitude](https://osxlatitude.com/forums) Forum.
 
 
:: <i>Follow me on [AppleLife](https://www.applelife.ru/members/badruzeus.112558/) / [Facebook](https://fb.com/badruzeus) / [InsanelyMac](https://www.insanelymac.com/forum/profile/826765-badruzeus) / [MacRumors](https://forums.macrumors.com/members/badruzeus.1133819/) / [SourceForge](https://sourceforge.net/u/badruzeus/profile) / [Youtube](https://www.youtube.com/channel/UCM2mZ2r2Gy914X-3N18b6qA)</i> ::

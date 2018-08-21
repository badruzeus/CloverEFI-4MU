# CloverEFI-4MU
### Introduction 
First, I have to tell that Clover binary used on this repo is same as what you could get from <b>Official SourceForge</b> [here](https://sourceforge.net/projects/cloverefiboot/files/Bootable_ISO/). So, it definitely is able to boot OS X / macOS as well (if your mach is Hackintosh compatible, with advanced configs for sure).
 
But, I decided to create a separated topic for answering a question: "How to use Clover w/o installing macOS on UEFI PC?". As we've known, provided Clover [Package](https://en.wikipedia.org/wiki/.pkg) is installable only on a Hackintosh based with macOS running.
 
Simply, <b>"CloverEFI-4MU"</b> as project here's: Clover bootloader for non-Hackintosh-able UEFI PC with Manual installation via Ubuntu Linux, using minimalized sample config, efi drivers, etc. I make it to be specific with UEFI only for easier configs compared to Legacy (though with GUID Partition Scheme: GPT, is actually able to.. but I don't wanna mess your current legacy bootloader settings), as well as via Ubuntu is to keep focus on the guides. Uploaded "CLOVER" folder is just for guide's supplement.

### What is Clover?
Clover is one of bootloaders developed by Slice, Apianti, BlackOSX, Dmazar, Blusseau, and other devs with great community for booting OS X, Windows and Linux on Mac or PC with UEFI / BIOS firmware.
 
Some of Clover features are:
- [x] Supports for booting OS X, Windows and Linux (Android x86 as well)
- [x] Running on Legacy BIOS (MBR, GPT) or UEFI firmware (GPT only)
- [x] Customizable GUI including themes, icons, fonts, background images, animations, and mouse pointers.
- [x] ... and much more. [Here's](https://sourceforge.net/projects/cloverefiboot/) for details.
 
### Requirements
However, to follow this specific project you have to meet these conditions:
- [x] Only for PC (Desktop / Laptop) with UEFI firmware capable: Check your BIOS Features
- [x] Make sure that your PC is able to reach Clover GUI: Test it by creating USB Clover with [this Tool](http://cvad-mac.narod.ru/index/bootdiskutility_exe/0-5) via Windows then boot from it
- [x] Basic knowledge about bootloader and UEFI / BIOS settings
- [x] Pre-installed Ubuntu Linux (and it's flavours) or LiveMode
- [x] Make a backup of whole "Internal EFI Partition" is recommended.

### How to Use
1. Clone or Download whole repo: $ `git clone https://github.com/badruzeus/CloverEFI-4MU`
2. (Optional) My Clover Themes collection: $ `git clone https://github.com/badruzeus/MyCloverThemes`
   Go to [docs](https://github.com/badruzeus/CloverEFI-4MU/docs/) for Theming how to
3. Then, just follow provided "Video Tutorial" below: (be really carefull when accessing EFI Partition with root access)
 
embed_url("https://www.youtube.com/watch?v=XHECZDy_ctg")
 
### FAQ & Troubleshooting
_(...Coming soon)_

### Credits
[Apple](https://www.apple.com) / [Canonical](https://www.ubuntu.com) / [Microsoft](https://www.microsoft.com/en-us/windows) / [Clover](https://sourceforge.net/projects/cloverefiboot) / [cvad](http://cvad-mac.narod.ru/index/bootdiskutility_exe/0-5) / [fusion71au](http://www.insanelymac.com/forum/topic/310038-manually-install-clover-and-configure-boot-priority-with-easyuefi-in-windows/#entry2200235) / [InsanelyMac](https://www.insanelymac.com/forum), [Olarila](http://olarila.com/forum) and [OSXLatitude](https://osxlatitude.com/forums) Forum.
# Hackintosh-Asus-A43SJ
This is my complete EFI folder to be used for hackintosh on Asus A43SJ notebook with multibooting:
- Mac OS X El Capitan 10.11.6
- macOS Mojave 10.14
- Ubuntu 18.04, and
- Windows 10.
 
<img src="/img/macOS-Mojave.png?raw=true" alt="macOS Mojave" align="center">
 
### How to Get
- Clone whole repo: $ `git clone https://github.com/badruzeus/Hackintosh-Asus-A43SJ`
- Download [Specific Folder](https://minhaskamal.github.io/DownGit/#/home) only.
 
--------------------------------------------------------------------------------------------
 
### Notebook Specs
<img src="/img/Asus-A43SJ-VX400D.png?raw=true" alt="Asus A43SJ" align="right">

- [x] <b>Model</b>: Asus A43SJ-VX400D (K43SJ Board) 2012
- [x] <b>CPU</b>: Intel Core i3-2330M (4) @ 2.20GHz (2nd Gen)
- [x] <b>Chipset</b>: Intel® HM65 Express Chipset
- [x] <b>GPU</b>: Nvidia GeForce <b>GT 520M</b> (Fermi GF119M) @ 1GB
- [x] <b>RAM</b>: 4GB DDR3 SDRAM @ 1333MHz (upgradable to 8GB)
- [x] <b>HDD</b>: 500GB SATA @ 5400rpm (GUID Partition Table)
- [x] <b>Audio</b>: Realtek ALC269-VB HD Audio Controller
- [x] <b>Wifi</b>: AzureWave AR9002WB-1NG (Atheros AR9285)
- [x] <b>Ethernet</b>: Realtek RTL8168BE PCI-e Gigabit Ethernet
- [x] <b>Others</b>: 1 USB3.0 + 2 USB2.0 ports, Elan PS/2 TouchPad, HDMI/VGA, Asus WebCam, 14.0" 16:9 HD (1366x768) LED, Pioneer DVD-RW, (SD/ MS/ MS Pro/ MMC) Card Reader, 6-Cell @5200mAh 56Wh Lithium-ion Battery
- [x] <b>BIOS</b>: Ver. 317 (Asus).
 
--------------------------------------------------------------------------------------------
 
### EFI Contains
- [x] <b>Clover Bootloader binary, config.plist</b>, drivers for legacy/uefi, themes, etc..
- [x] <b>Patched ACPI Tables (DSDT-SSDT)</b> for Graphics, Audio, Wifi, Ethernet, Battery, etc..
- [x] <b>3rd party kexts</b> for working devices under Mac OS X El Capitan (10.11) and macOS Mojave (10.14)
- [x] Windows 10 EFI (bootmgfw.efi), Ubuntu 18.04 boot (grubx64.efi) \\Optional.
 
--------------------------------------------------------------------------------------------
 
### What Worked
- [x] QE/CI Enabled Graphics (GFX0 DSDT Patch), 1366x768 @ 60MHz Native Display resolution
- [x] ACPI Display brightness with hot keys / slider (PNLF DSDT Patch + AsusACPIBackLightPanel.kext)
- [x] Realtek ALC269-VB Audio in-out (HDEF DSDT Patch, with Lilu + AppleALC)
- [x] Atheros AR9285 Wifi (AirPort DSDT Patch)
- [x] Realtek RTL8168BE en0 (DSDT Patch + RealtekRTL8111.kext)
- [x] ELAN TouchPad (EmlyDinesh's ApplePS2SmartTouchpad.kext)
- [x] Battery Indicator (DSDT Patch + Rehabman's ACPIBatteryManager.kext)
- [x] WebCam (with CamTwist as helper)
- [x] Bluetooth (with IOath3kfrmwr.kext as helper)
- [x] AsMedia ASM1042 USB3.0 Port (CalDigit*.kext), USB2.0 Ports (EH0 DSDT Patch)
- [x] Sleep and Wake (PRW DSDT Patch, OS Dependent)
- [x] Better Mach and Graphics Power Management (ACPI_SMC_Platform Inject via FakeSMC)
- [x] Mac App Store Access (NullEthernet DSDT Patch).
 
--------------------------------------------------------------------------------------------
 
### Not Worked / Bugs
- [ ] Realtek USB2.0 CardReader
- [ ] HDMI / VGA Ports (not tested)
- [ ] Random Graphics crash issue with GF119 under macOS 10.14
- [ ] Unsolved "AppleUSBHostPort::interruptOccurred: overcurrent detected" warnings (not error).
 
--------------------------------------------------------------------------------------------
 
### Notes
1. macOS versions used are <b>Retail from Mac App Store</b>, using <b>createinstallmedia</b> for USB Installer
2. Platform Datas (SN, ROM, UUID) used here are <b>ALL FAKE</b>. So, you need to regenerate them.
3. Don't use [Patched DSDT-SSDT](https://github.com/badruzeus/Hackintosh-Asus-A43SJ/tree/master/Bootloader/EFI/CLOVER/ACPI/patched) if you have different <b>BIOS version</b> (need to configure [config.plist](https://github.com/badruzeus/Hackintosh-Asus-A43SJ/blob/master/Bootloader/EFI/CLOVER/config.plist) - ACPI section)
4. To boot with <b>Clover UEFI</b>, you need to configure BIOS (Press <b>Esc</b> when mach power on > Select <b>Setup</b>):
- [x] Go to <b>"Boot"</b> menu and make sure that <b>"UEFI Boot"</b> option is <b>"Enabled"</b>
- [x] Select <b>Add New Entry</b>
- [x] Give it a name (for example: clover) and locate path to <b>EFI Partition</b>
- [x] Set Clover entry (w/o quotes) as: <b>"\efi\clover\cloverx64.efi"</b>
- [x] Confirm the changes by pressing <b>"Create"</b>, then use it as <b>1st boot entry</b>.
5. To get GT 520M working under macOS 10.14 (18A391), use [/Extras/CoreDisplay](https://github.com/badruzeus/Hackintosh-Asus-A43SJ/blob/master/Extras/CoreDisplay.zip) binary and place to:
`/System/Library/Frameworks/CoreDisplay.framework/Versions/A`
6. Install [/Extras/AirPortAtheros40.kext](https://github.com/badruzeus/Hackintosh-Asus-A43SJ/blob/master/Extras/AirPortAtheros40.kext.zip) to SLE using Kext Utility for a working AR9285 Wifi under 10.14.
7. Install [/Extras/AppleIntelSNB~.kext](https://github.com/badruzeus/Hackintosh-Asus-A43SJ/blob/master/Extras/AppleIntelSNB*.zip) to SLE using Kext Utility for a working Intel MEI under 10.14.
8. To fix Display [Color Banding](https://en.wikipedia.org/wiki/Colour_banding) issue under 10.11.x or 10.14, just place [/Extras/DisplayVendorID-da9](https://github.com/badruzeus/Hackintosh-Asus-A43SJ/blob/master/Extras/DisplayVendorID-da9.zip) to:
`/System/Library/Displays/Contents/Resources/Overrides`
 
--------------------------------------------------------------------------------------------

### Video Tutorials
- [Multibooting](https://www.youtube.com/watch?v=vXMNyiEgD6o) Windows, Ubuntu, PhoenixOS & macOS using Clover (UEFI)
- Fixing [Display Color Banding](https://www.youtube.com/watch?v=cX-tBC71hHM) issue with Nvidia graphics (Hackintosh)
- Video demonstration about [Full Graphics Acceleration support](https://www.youtube.com/watch?v=q1gjphKdIVQ) (QE/CI enabled) under macOS.
 
--------------------------------------------------------------------------------------------
 
### Credits
[Apple](https://www.apple.com) | [Canonical](https://www.ubuntu.com) | [Microsoft](https://www.microsoft.com/en-us/windows) | [Clover](https://sourceforge.net/projects/cloverefiboot) | [Acidanthera](https://github.com/acidanthera) | [Rehabman](https://github.com/RehabMan/Laptop-DSDT-Patch) | [Mieze](https://github.com/Mieze/RTL8111_driver_for_OS_X) | [Mirone](https://github.com/Mirone/AppleHDAPatcher) | [EmlyDinesh](https://osxlatitude.com/forums/topic/1948-elan-focaltech-and-synaptics-smart-touchpad-driver-mac-os-x) | [AnV](https://github.com/andyvand/FixEDID_Devel) | [Piker R. Alpha](https://github.com/Piker-Alpha/ssdtPRGen.sh) | [InsanelyMac](https://www.insanelymac.com/forum), [Olarila](http://olarila.com/forum) and [OSXLatitude](https://osxlatitude.com/forums) Forum | <b>Other devs</b> who aren't mentioned.
 
 
:: <i>Follow me on [AppleLife](https://www.applelife.ru/members/badruzeus.112558/) / [Facebook](https://fb.com/badruzeus) / [InsanelyMac](https://www.insanelymac.com/forum/profile/826765-badruzeus) / [MacRumors](https://forums.macrumors.com/members/badruzeus.1133819/) / [Reddit](https://www.reddit.com/user/Badruzeus) / [SourceForge](https://sourceforge.net/u/badruzeus/profile) / [Youtube](https://www.youtube.com/channel/UCM2mZ2r2Gy914X-3N18b6qA)</i> ::

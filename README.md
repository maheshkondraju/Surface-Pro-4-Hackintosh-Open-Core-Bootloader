The only difference between SSD EFI & USB EFI is Advise Features quirk under Generic PlatformInfo is required during installation to fix the error "A Required Firmware Update Could Not Be Installed".

surface-pro-4-hackintosh-monterey
Surface Pro 4 + macOS 12 Monterey, no touchscreen/bluetooth/camera (Wi-Fi uses USB), otherwise full

📢recently updated
⚠️WWDC22 and Ventura⚠️
It looks like Apple's support for Skylake has run its course. If nothing else, Monterey will be the last generation of macOS supported by this project.

If you have any ideas, you can communicate in the Issue area.

⭐Now supports Monterey⭐
After several days of trying, this project has supported direct upgrading to macOS 12 Monterey while retaining Big Sur support.

The testing process is very complicated, and a lot of parameters have been modified, so I won’t describe it here. If you have any questions or ideas, you can open an Issue to communicate.

Monterey

🍎edible
This project is not responsible for any actions. Before eating, please be sure to read the preconditions and requirements described in Dortania's official tutorial

compatibility
The project supports both Big Sur and Monterey. See Releases for version history and update records .

fresh install
Download the latest stable version of this project in Releases (click Source code (zip)to download)

Follow Dortania's official tutorial to create a macOS boot disk

Paste the EFI folder into the root directory of any empty partition of the U disk, refer to the official tutorial of Dortania for details (note that the file system of the U disk must be recognized by Surface UEFI)

Surface into UEFI, turn off Boot Lock, Secure Boot and TPM, etc., put the U disk first in the boot order

Plug in the U disk and install macOS

Reset NVRAM (If you suddenly find that any function becomes abnormal one day, remember to Reset NVRAM before trying to repair it)

After confirming that everything is normal, follow Dortania's official tutorial to EFIoverwrite it on the local hard disk, and pull out the boot disk

Start a pleasant fruit journey

If you encounter problems in use, remember to check the notes below or create a new issue here; if you have successfully used macOS, don't forget to come back and give a little bit to this project and the components mentioned below⭐star oh!

upgrade
Before starting, be sure to back up the existing according to Dortania's official tutorial ; it is recommended to back up to the OpenCore boot U disk, which can be renamed toEFIEFI备份

Download the latest stable version of this project in Releases (click Source code (zip)to download) and write it to the U disk

[Pre-update] Surface enters UEFI, put the U disk first in the boot sequence and use the latest version of OpenCore in the U disk to try to boot; if it starts normally, you can follow Dortania's official tutorialEFI to replace the one in the local hard disk with the latest version; if it cannot be started, you need to perform [post-update] operation during or after the upgrade

[System upgrade (not recommended)] If you really trust the update provided by Apple, you can directly download and install the update in System Preferences. After downloading and installing, you don’t need to perform the following manual upgrade operations; otherwise, it is recommended to perform system upgrades as little as possible. If you really want to upgrade, use the following [Manual upgrade] steps

[Manual upgrade] Make a macOS boot disk according to Dortania's official tutorial ; just get the file, no need to write to the U diskdmg

[Manual upgrade] Load the dmgfile , double-click to runInstall macOS <系统版本>.app

The system may take several hours to upgrade; if it freezes/infinitely restarts halfway through the upgrade, then enter UEFI, put the U disk first in the boot order, and use the latest version of OpenCore in the U disk to try to boot

[Post-update] After the update is complete and everything is normal, follow the official tutorial of Dortania toEFI replace the on the local hard disk with the latest version; if it has been updated before installation, this operation is not necessary

⚠️Precautions
Wi-Fi
If you bought COMFAST CF-811ACa need to download this App separately for Wi-Fi. After downloading and installing, restart and you can find the icon on the taskbar.

touch pad
Turn it off in the touchpad settings Force click and haptic feedback, otherwise it will be a bit strange to use (Voodoo touchpad driver will treat the touchpad as a press Force Click)

Reset NVRAM
If any function suddenly becomes abnormal one day (especially brightness control and sound), if restarting cannot solve the problem, select Reset NVRAM to run on the OpenCore interface at startup

renew
The default configuration has SIP disabled. There is a high risk of system damage using updates provided by Apple. To resume updating, you may need to re-enable SIP. Reference: Disabling SIP

Note: It is highly not recommended to directly upgrade the system through system update. It is recommended to manually download the system installer for installation and upgrade.

Disabling updates may also affect app updates in the App Store. Please weigh the pros and cons for yourself.

Update: Some partners reported that they still received the update of macOS 12.4 even though SIP was disabled in the default configuration. Direct installation is highly not recommended. If necessary, download the installer manually.

External display turns purple
Download the patch-edid.rb file and run it, then follow the steps in Writing to the macOS system partition to map the system partition as a writable partition, and finally copy the DisplayVendorIDgenerated folder to the /System/Library/Displays/Contents/Resources/Overridesdirectory to overwrite the original file. Remember to backup the original file.

Note: Modifying system partition files may compromise system integrity (not damage the system) and prevent you from receiving Apple updates. Remember to backup when modifying files.

Also note that you need to go through the above steps every time you connect a new display screen visually.

DSDT
The DSDT in the current repo is mainly for the power management function. If you find a problem related to DSDT (such as #3 ), you can create a new DSDT and replace it.

Installed successfully, but rebooted on OOBE
You can refer to the edible fix-tsc branch. Try this , this and this version. Also try v4 with TSC patch and v3 with TSC patch . See #5 for more information .

ℹ️project information
hardware
components	describe
model	Surface Pro 4 8G 256G
CPU	Intel Core i5-6300U 2.5GHz
graphics card	Intel HD Graphics 520 2GB
sound card	Realtek ALC3269 (layout 3)
USB wireless network card	COMFAST CF-811AC (self-purchased)
Target corresponding model
official name	MacBook Pro (13-inch, 2016, two Thunderbolt 3 ports)
identifier	MacBookPro13,1
Part Number	MLL42xx/A、MLUQ2xx/A
Source & Acknowledgments
components	from
macOS	Apple
OpenCore	acidanthera
DSDT	bigsadan/surface-pro-4-hackintosh
Keyboard & Touchpad etc.	VoodooI2C (Basic) , Xiashangning/BigSurface
audio	AppleALC + layout 3
Wireless network card driver	chris1111/Wireless-USB-OC-Big-Sur-Adapter
LICENSE
All files and codes in this repo are only for archiving, and their copyright belongs to the original author.

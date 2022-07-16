# Hackintosh | 10900k-Z490I
This repository is about my personal journey when creating my first Hackintosh build on my gaming machine. The machine is dual booting macOS Monterey 12.4 & Windows 11. First off, I'd like to thank the awesome Hackintosh community and the creators/devs for the loads of help with this project.
In this repo, I'll be explaining the useful tidbits of information I have found that made my system work the way it does as well as include the software I used.

## Preface
I highly encourage you to read the full OpenCore Install guide before you even begin anything. It has so much information and it will really save you so much time when you are actually starting the install. Note: This EFI contains settings for OpenCanopy for a nice and clean launcher. Change this as you see fit.

## Hardware
* CPU: Intel i9 10900k
* GPU: Intel UHD 630 (iGPU)
* Motherboard: ROG STRIX Z490i GAMING
      * Ethernet: Integrated (Intel I225-V 2.5Gb)
      * Wifi/Bluetooth: Integrated (Intel Wi-Fi 6 AX201)
      * Audio: Integrated (Audio Realtek ALCS1220A)
* RAM: Corsair LPX 32gb 3600Mhz
* SSD: Crucial P5 Plus 1Tb M.2, WD Blue 1Tb M.2
* BIOS: 2403 10/27/2021

## Software
* Bootloader: OpenCore 0.8.0 - Release
* OS: macOS Monterey 12.4 (iMac Pro 1,1)
     * ProperTree
     * MountEFI
     * GenSMBIOS
     * USBMap

## Working
* Ethernet
* Wifi
* Bluetooth
* iMessage/FaceTime
* iCloud
* All USBs
* 100hz @ 3840x1600

## Not Working
* Handoff
* Universal Control
* Sidecare
* AirDrop
     As I understand it, to get these features to work, you NEED a native Mac Wifi/Bluetooth card.
     
## Special Changes & Troubleshooting
My first issue arose when trying to install macOS where I would get repeated kernal panic texts mentioning "USB" and something else. This was fixed by setting ```XhciPortLimit False```.

After the fresh install and getting past the setup screen, I had constant system freezes/crashes direclty seconds after signing in. It didn't give me any kernal panic text so this error was hard to daignose. Eventually, I noticed that the machine did not have issues when the ethernet was unplugged. I stumbled upon a post where an indivdual had my exact same problem and it was fixed by setting the Ethernet ```device-id F2158680```. Also, I had to change the ethernet PciRoot pathway to ```PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0)```.

On every reboot after shutting down, my BIOS would post in safe mode which required F1 to be pressed. Simple fix was found on YouTube where I set ```DisableRtcChecksum True```.

Bluetooth wasn't working on first startup. My solution was found on an OpenIntelWireless post where adding IntelBluetoothFirmware.kext and BlueToolFixup.kext resoloved the problem. The order of injection matters; use ProperTree as it will automatically order them correctly. Do not add the injector kext like in previous macOS versions. 

I was having issues with sound outputs as well. I found a similar post on GitHub where setting ```boot-args alcid=7``` gave proper sound outputs. I later swapped this bootarg with the actual device properties using ```PciRoot(0x0)/Pci(0x1f,0x3) layout-id 7```.

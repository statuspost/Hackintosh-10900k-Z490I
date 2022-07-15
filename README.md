# Hackintosh|10900k-Z490I
This repository is about my personal journey when creating my first Hackintosh build on my gaming machine. The machine is dual booting macOS Monterey 12.4 & Windows 11. First off, I'd like to thank the awesome Hackintosh community and the creators/devs for the loads of help with this project.
In this repo, I'll be explaining the useful tidbits of information I have found that made my system work the way it does as well as include the software I used.

## Preface
I highly encourage you to read the full OpenCore Install guide before you even begin anything. It has so much information and it will really save you so much time when you are actually starting the install. 

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
My first issue arose when trying to install macOS and it was related to USB (forgot the error code specifically) but it was fixed by switching <XhciPortLimit> from True to False. This information is presented in the OpenCore guide but I missed it during the install. My install proceeded just fine from then on.

# MacOS Ventura on the MSI B450M Bazooka Max WiFi

## System details
- Ryzen 7 5800 (non-X, 8-core, should work fine with any other CPU, see below)
- Radeon RX 6800 (non-XT, should work with any other 6600 or 6800, see below)
- 32GB (2x16GB) DDR4 3200 RAM, frequency manually set in OC menu (not an overclock though)
- 1TB SiliconPower NVME (TRIM works by default)

## What works: [Almost Everything]
- WiFi/Bluetooth (Intel 3... chip).
- iCloud, iMessage, etc.
- Continuity/Handoff/Hotspot.
- CPU/GPU and power saving.
- USB with patched ACPI tables (all external USB 2 ports disabled in favor of USB 3 ports).
- DRM (Apple Tv, most things in Safari so far...)

## What doesn't work:
- Apps that use intel-specific instructions. These need to be patched manually according to the dortania guide.
- Weird bug where waking by USB requires two taps/clicks instead of one. Also fixed in the dortania guide.

## Installation

- Follow [Dortania guide for Ryzen](https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html), compare and merge 
changes in my EFI. Notably DeviceProperties>Add and ACPI>Add.
- Don't forget to fill out PlatformInfo.

## If iMessage doesn't work
- You are on Sonoma and AirportItlwm hasn't been updated past 
2.3.0-alpha; there's a bug where [iCloud/AppleID doesn't 
work](https://github.com/OpenIntelWireless/itlwm/issues/942).
- You didn't properly follow the Dortania guide, make sure to fill out PlatformInfo.


## CPU/GPU Variants
- If you use a CPU with a differing amount of cores, make sure you update the core count as specified in the Dortania guide. If you use the 5800X3D you shouldn't need to make any changes to this.
- If you use the RX 6600 or 6800, they should work fine. If you use any other 6000 series, disable/remove WhateverGreen and add [NootRX](https://github.com/ChefKissInc/NootRX/).

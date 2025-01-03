# Only OpenCore EFI for HP Pavilion Gaming 15-ec2900nc
## Note: It is still in development due to various bugs and other errors.
In the opencore-2024-........txt file is the OpenCore Log Dump from the last attempt to run it.

# Hardware
There are a lot of types of this laptop,
so I am listing the hardware of mine, for which I did the EFI,
to avoid that someone will try this EFI and have the same laptop, but at the same time completely different.
By that I mean, maybe it will be the same product but have different hardware,
or very similar but still not compatible at all. I'm including paths involving hardware ID, BIOS, etc...
As well as listing the Kext versions and decompiled ACPI

| Component | Product           | Hardware ID            | BIOS Device Name | Additional |
| --------- | ----------------- | ---------------------- | ---------------- | ---------- |
| CPU       | AMD Ryzen 5 5600H | ACPI\VEN_ACPI&DEV_0007 | \_SB.PLTF.P000   | 6 physical and 12 logical cores |
| RAM       | N/A               | N/A                    | N/A              | N/A |
| M.2 NVMe SSD | N/A            | SCSI\DiskNVMe_____________________MTFDHBA512QFD-1AX1AABHA_HPS1022 | N/A | N/A |
| iGPU      | AMD Radeon Graphics | PCI\VEN_1002&DEV_1638&SUBSYS_88DE103C&REV_C6 | \_SB.PCI0.GP17.VGA | 512MB Dedicated Memory |
| dGPU      | NVIDIA GeForce RTX 3050 | PCI\VEN_10DE&DEV_25A2&SUBSYS_88DE103C&REV_A1 | \_SB.PCI0.GPP0.PEGP | 4GB Dedicated Memory |
| Display   | N/A               | N/A                    | N/A              | 1920x1080 15.6" 60Hz matte IPS display with WLED backlight Full HD resolution UWVA AntiGlare 300 nits (cd/m^2) 72% NTSC |
| Audio     | B&O (2 Speakers and 1 integrated microphone) | HDAUDIO\FUNC_01&VEN_10EC&DEV_0285&SUBSYS_103C88DE&REV_1000 | N/A | N/A |
| Webcamera | HP TrueVision     | USB\VID_30C9&PID_0035&REV_0003&MI_00 | \_SB.PCI0.GP17.XHC1.RHUB.PRT3.CAM3 | I really don't understand why they put this in the specs because it doesn't make sense: HD 720p |
| WiFi      | Realtek RTL8852AE WiFi 6 | PCI\VEN_10EC&DEV_8852&SUBSYS_88E1103C&REV_00 | \_SB.PCI0.GPP3.XPDV | 802.11ax PCIe Adapter |
| Bluetooth | Realtek Wireless Bluetooth Adapter | USB\VID_0BDA&PID_2852&REV_0000 | \_SB.PCI0.GP17.XHC0.RHUB.PRT4 | Bluetooth version is 5.2 |
| Ethernet  | Realtek Gaming GbE Family Controller | PCI\VEN_10EC&DEV_8168&SUBSYS_88DE103C&REV_16 | \_SB.PCI0.GPP1.XPDV | If I'm not mistaken, the speed should be either 1GB/s or 10GB/s |
| SD Card Reader | Alcorlink USB 2.0 Card Reader | USB\VID_058F&PID_6366&REV_0100 | \_SB.PCI0.GP17.XHC1.RHUB.PRT4 | N/A |
| Thunderbold / USB-C 3.2 | N/A | N/A | N/A | Version 3.2 . 5GB/s speed, can function as a normal USB (USB-A) and can power devices |
| HDMI      | N/A | N/A | N/A | Maximum possible resolution 4096x2160, 60Hz frequency. Leads from dGPU. |
| Backlit keyboard with numeric part | N/A | N/A | N/A | Classic backlit PS/2 keyboard with numeric part |

# SSDTs
After some research on what SSDT and DSDT are and what they are actually for, I used the SSDTs listed below.
If anyone is interested in using them in their own EFI, unfortunately they can't use them because I have customized them to
my device. So I guess.
| Selected SSDT | Why did I choose this |
| ------------- | --------------------- |
| SSDT-EC-USBX  | macOS needs some EC controllers. Without them, it wouldn't even boot. |
| SSDT-GPU-DISABLE | macOS from Mojave onwards does not support NVIDIA graphics. If you could install NVIDIA drivers, performance would be terrible and RTX wouldn't work anyway. |
| SSDT-HPET | Simple and straightforward. Fixing IRQ signals. |
| SSDT-PNLF | Again, plain and simple. Backlit keyboard. |

# Drivers
I left all the drivers as they were in the default settings,
because I would like to modify something in the future and I don't want it to tell me erroros or cause problems again because of other things.

# Kexts
Kexts are my favorite part. I mean that in quotes, because sometimes getting all the kexts is hell,
but sometimes it's a walk in the park. Just a little heads-up. All kexts, but also OpenCore itself in this EFI is in the Release.
| Selected kexts | For a component |
| -------------- | --------------- |
| AppleALC       | Audio           |
| AppleMCEReporterDisabler | Just a necessity that all AMD-based systems must have. That concerns me too. So. |
| BrightnessKeys | Fix keyboard shortcuts to increase or decrease brightness. |
| ECEnabler      | Battery Status  |
| Lilu           | Just as a patching engine. A must have for anyone using OpenCore. |
| NootedRed      | AMD Radeon Graphics |
| NVMeFix        | NVMe |
| RealtekRTL8111 | Ethernet |
| SMCRadeonSensors | AMD Radeon Graphics |
| UTBMap         | USB |
| VirtualSMC     | A must-have for anyone who uses OpenCore but is not on a native Mac. |
| VoodooI2C      | Touchpad |
| VoodooI2CELAN  | Mouse and other things that support ELAN. |
| VoodooI2CHID   | Various things and components using HID. |
| VoodooPS2Controller | Keyboard |
| WhateverGreen  | That's the basis for all graphics. |

# Resources and Tools
Again, I didn't change anything. Everything is as it was after the standard OpenCore extraction.
And one more thing. The OpenCore version is 1.0.3 .

# config.plist
I configured it according to the instructions in the manual.

# Finally
That's about it.
This was just supposed to be some "documentation" of my EFI,
but I need to modify it so that macOS boots successfully,
and not so that OpenCore gets stuck either on the ACPI tables or throws me a Kernel Panic.

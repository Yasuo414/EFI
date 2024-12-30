# Only OpenCore EFI for HP Pavilion Gaming 15-ec2000nc
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
| Thunderbold / USB-C | N/A |

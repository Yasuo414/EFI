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

# AsRock B365M Pro4 Opencore (MacOS Monterey 12.x.x)

[OpenCore Legacy Patcher]: https://github.com/dortania/OpenCore-Legacy-Patcher/releases

![Screenshot](https://i.imgur.com/AcR3B6S.png)
*The screenshot is a conceptual example, it may not match the final result.*


Hardware | Model
--- |:--:
![motherboard](https://i.imgur.com/Nqpg4wb.png) | AsRock B365 Pro4 (Kaby Lake X/Coffee Lake)
![bios](https://i.imgur.com/RmYixFt.png) | Aptio's V v4.50 (by American Megatrends (AMI)/AsRock)
![processor](https://i.imgur.com/BzXF1mf.png) | Intel Core i5 (8th Gen) 8500 6 Cores/Threads@3Ghz
![igpu](https://i.imgur.com/HS92HLo.png)| UHD 630 Graphics 1,2GB VRAM @1,2GHz
![dgpu](https://i.imgur.com/nUQquVP.png) | Nvidia/Asus GT730 1GB VRAM@902MHz (Officially supported until MacOS High Sierra)
![audio](https://i.imgur.com/A7RRuUn.png) | ALC892 (in-build)
Ethernet | Intel Ethernet I219-V
![ddr4](https://i.imgur.com/5MAnSyf.png) | Kingston HyperX Fury 8GB(x1) DDR4@3200Mhz
![nvme](https://i.imgur.com/J9Q96yY.png) | Kingston NV2 500GB SSD Nvme (TLC PS5021 Controller)
---


### Works:
---
<details>

- Installer Boot ✅ (Installation on SATA: ~30/35 minutes | Installation on Nvme: ~20/25)

- System Boot ✅

- USB Ports ✅

- Screen ✅ (1336x768, 1080x1920)

- Audio Card ✅ (Inputs and Outputs)

- Ethernet ✅

- PCI Express Ports (M.2 Ports included, Nvmefix kext it's added)✅

- Sleep Mode ✅

 
</details>


### IMPORTANT NOTES:
---

## For use AMD Graphics only:

1. Add the boot-arg:

- "**radpg=15**" for enabling 3D Acceleration (In almost all 2017 or older GPUs, Eg: RX 580, RX 470, R9 Fury X, HD 7730, etc).

- "**agdpmod=pikera**" for try enabling drivers (In almost all 2018 or newer GPUs, Eg: Vega 56, Radeon VII, RX 5700XT, RX 6600, etc).
From *NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82*

2. Rename the "**model** key" by yours in **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)** and **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x1)**" from *DeviceProperties* with your graphic card data (Eg: AMD Radeon RX 5700XT and Bermuda HDMI Audio [Navi Series])

---

## For use Nvidia Graphics only:

1. Add the boot-arg "**nv_disable=1**" (for using Vesa drivers); later, create a new table like this (for enabling Nvidia Drivers):

![nvidiatable](https://i.imgur.com/1crQGj1.png)

**Usually for Pascal (GTX1000 Series), Maxwell (GTX900 Series) and Kepler (GTX600/700 Series) GPUs.***

all on *NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82*; if Nvidia GPU isn't recognize after that, add "**agdpmod=pikera**" boot-arg too.

2. Rename the "**model** key" by yours in **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)** and **PciRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x1)**" from *DeviceProperties* (Eg: Nvidia GeForce GTX 1070Ti and Nvidia HDMI Output)

3. Download and install [OpenCore Legacy Patcher] for try patch your GPU (Pascal *GTX1000* and older generations *GTX900, 700, 600* are supported; **ALL RTX MODELS AREN'T SUPPORTED**), later, go to *config.plist --> NVRAM --> 7C436110-AB2A-4BBB-A880-FE41995C9F82* and remove "**nv_disable=1**" and reboot.

---

## What audio codec I can use?:

With boot-arg "**alcid=**":

- If you have the Realtek ALC892, you can use these layouts: *1, 2, 3, 4, 5, 7, 11, 12, 15, 16, 17, 18, 20, 22, 23, 28, 31, 32, 90, 92, 97, 99, 100*

--- 

## Do you want Wi-Fi on your PC?:

- If is a TP-Link, Edimax, Ralink or Mediatek wireless adapter, use the D-Link Utility (https://github.com/chris1111/D-LinkUtility-Package) or Wireless USB Adapters: (https://github.com/chris1111/Wireless-USB-OC-Big-Sur-Adapter) (*see the supported devices*)

- If is some Asus, TP-Link or Intel PCI wireless adapter, use the AirportItlwm (https://github.com/OpenIntelWireless/itlwm) (*see the supported devices on https://openintelwireless.github.io/itlwm/Compat.html*); for Asus and TP-Link adapters, check if the used Wi-Fi card is made by Intel.

---

## Do you only have your Android Phone/Device on hand?:

 1. HoRNDIS it's included with my EFI folder, connect your device via USB and enable USB Tethering.

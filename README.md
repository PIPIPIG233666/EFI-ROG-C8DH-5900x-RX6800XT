# ASUS ROG Strix B550I + Ryzen 9 5900X + RX 6650 XT

- OpenCore ver 0.8.0
- MacPro7,1
- Monterey 12.4

## Current hardware

Powerful and near-silent even under full CPU load.

![](media/SS.png)
#![](media/sliger-s620.jpeg)
![](media/radeon.jpeg)
![](media/Screen Shot 2022-05-30 at 7.26.28 PM.png)
![](media/unigine-heaven.png)

- [ROG STRIX B550-I GAMING](https://rog.asus.com/us/motherboards/rog-strix/rog-strix-b550-i-gaming-model/) motherboard.
- AMD [Ryzen 9 5900X](https://www.amd.com/en/products/cpu/amd-ryzen-9-5900x) CPU.
- Phanteks [Glacier One 240MPH](https://phanteks.com/Glacier-One-MP.html) AIO with Noctua NF-A12x25 x2 under the radiator.
- AMD [RX 6650 XT](https://www.amd.com/en/products/graphics/amd-radeon-rx-6650-xt) graphics card, PCIe 4.0 riser from case.
- G.Skill [Ripjaws V](https://www.gskill.com/product/165/184/1562833535/F4-3600C18D-32GVK) 32 GB (2 x 16 GB) DDR4 3600MHz CL18 Samsung A-die.
- SK Hynix [Platinum P41](https://ssd.skhynix.com/platinum_p41/) 1TB NVMe SSD (Windows).
- WD_BLACK [SN 750](https://www.westerndigital.com/products/internal-drives/wd-black-sn750-nvme-ssd#WDS250G3X0C) 512 GB NVMe SSD.
- Corsair [SF600 Platinum](https://www.corsair.com/us/en/Categories/Products/Power-Supply-Units/Power-Supply-Units-Advanced/SF-Series/p/CP-9020182-NA) SFX PSU.
- Lian Li [A4-H2O](https://lian-li.com/product/a4h2o/) SFF case.

### WiFI / Bt

The built-in components support WiFi 6 / Bluetooth 5 with the itlwm.kext and IntelBluetoothFirmware.kext.

### BIOS

Version 2423

- Fast Boot: `Disabled`
- CSM: `Disabled`
- Above 4G Decoding: `Enabled`
- Resizable Bar Support: `Enabled`
- PCIe slot speed: `Auto`
- XMP Profile activated
- PBO2 PPT: 170 TDC: 45 EDC: 140.

## Usage

1. [Update `PlatformInfo/Generic` stuff](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial) with your own, inside `config.plist`
2. Use your Ethernet’s MAC address for `ROM` value, as explained in the Dortania guide. Don’t leave it as all 0s.

### What’s working

Everything.

- CPU Power Management.
- NVMe and 2.5in SATA SSD.
- WiFi, Bluetooth, Ethernet.
- All USB ports (without map, just with RHUB reset).
- Radeon GPU is natively supported(after spoofing).
- 4K HDMI or DisplayPort with HDR.
- Watch unlock, Handoff, iMessage, iCloud, Keychain, Xcode etc.
- System Integrity Protection (SIP) fully enabled.
- Sleep / Wake.
- All media & DRM

### What’s not working

Sidecar most likely. Did not even try it but I suspect it does not work.

## Notes

Use at your own risk. 

- All `.efi` drivers and `.kext` are `-RELEASE` builds from the respective packages. 
- OpenCanopy (GUI boot menu) is up and running.
- I do boot Windows 10 using OC, thus I can guarantee it will work. I have Win 11 installed on separate SSD.

Good luck.

## Give back

If you found this code useful, please consider [buying me a coffee](https://www.buymeacoffee.com/radianttap) or two. ☕️😋

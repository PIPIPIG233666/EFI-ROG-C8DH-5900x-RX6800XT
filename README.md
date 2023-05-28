# ASUS ROG Crosshair VIII Dark Hero + Ryzen 9 5900X + RX 6800 XT

- OpenCore ver 0.9.3
- MacPro7,1
- Ventura 13.4

## Current hardware

Powerful and silent even under full CPU + GPU load (Thanks to external radiator).

- [ROG Crosshair VIII Dark Hero](https://rog.asus.com/us/motherboards/rog-crosshair/rog-crosshair-viii-dark-hero-model/) motherboard.
- AMD [Ryzen 9 5900X](https://www.amd.com/en/products/cpu/amd-ryzen-9-5900x) CPU.
- AMD [RX 6800 XT](https://www.amd.com/en/products/graphics/amd-radeon-rx-6800-xt) GPU.
- Crucial [Ballistix RGB](https://www.crucial.com/memory/ddr4/bl2k32g32c16u4bl) 64 GB (2 x 32 GB) DDR4 3800MHz CL16 Micron B-die.
- SK Hynix [Platinum P41](https://ssd.skhynix.com/platinum_p41/) 1TB TLC NVMe SSD (Windows + Hackintosh).
- Western Digital [Ultrastar DC SN640](https://www.westerndigital.com/products/internal-drives/data-center-drives/ultrastar-dc-sn640-nvme-ssd) 7.68TB TLC NVMe SSD (Games + Linux)
- Corsair [HX1000i Platinum](shorturl.at/oAL03) 1000W ATX PSU.
- ASUS [TUF GT502](https://www.asus.com/us/motherboards-components/gaming-cases/tuf-gaming/tuf-gaming-gt502/) M-ATX case.

### WiFI / Bt

The built-in components support WiFi 6 / Bluetooth 5 with the itlwm.kext and IntelBluetoothFirmware.kext, however, after Ventura, BT stopped working. Therefore, I switched to the Fenvi T919 for PnP Wi-Fi + BT experience.
Note that on Ryzentosh, in order for the BCM_20702B0 chipset to work, USB ports have to be mapped, and `BlueToolFixup` is required even for a PnP card like the Fenvi T919.

### BIOS

Version 4501

- Fast Boot: `Enabled`
- CSM: `Disabled`
- Above 4G Decoding: `Enabled`
- Resizable Bar Support: `Enabled`
- PCIe slot speed: `Auto`

## Usage

1. [Update `PlatformInfo/Generic` stuff](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#generate-a-new-serial) with your own, inside `config.plist`
2. Use your Ethernet’s MAC address for `ROM` value, as explained in the Dortania guide. Don’t leave it as all 0s.

<details>
  <summary><h2> Hackintosh Checklist </h2>
</summary>

## What's working?

**Working:** check-mark. **Not Working:** bold.&#x20;

**Not Tested:** leave as-is. **Not applicable:** Strikethrough or delete.&#x20;

### Desktop and General

#### OpenCore Booting

* [x] Correct OS choices shown in OpenCore Menu/GUI
* [ ] Keyboard shortcuts working (see details below in _OpenCore Boot Key Combinations_)
  * CMD+V — verbose mode _(check KeySwap)_
* [ ] NVRAM working: [Verifying if you have working NVRAM](https://dortania.github.io/OpenCore-Post-Install/misc/nvram.html#verifying-if-you-have-working-nvram)
  * Apple -> System Preferences -> Startup Disk (uses NVRAM).
* [ ] Security (especially SIP) use _Menu Bar SIP Detector_
* [ ] FileVault (if used)
* [x] Windows 10 and/or Linux Multi-Boot
* [x] Recovery (macOS) Boot
* [x] Serial Number: ensure that it does not exist elsewhere, [Check Apple Coverage](https://checkcoverage.apple.com/us/en/) _(and not uploaded to Github)_

#### Display

* [x] Display via HDMI
* [x] Display via DisplayPort
* [ ] Display via DVI
* [x] Native Resolution
* [x] Refresh rates
* [x] Multimonitor displays

#### Graphics Acceleration

* [x] dGPU dedicated GPU
  * In _Terminal_: `gfxutil -f GFX0` or check in _IORegistryExplorer_
* [ ] iGPU internal GPU
  * In _Terminal_: `gfxutil -f IGPU` or check in _IORegistryExplorer_
* [ ] QE/CI _(full acceleration requires both Quartz Extreme and Core Image)_
  * Check for transparent menu bar and fast smooth UI.
* [ ] VDA _(Video Decode Acceleration framework)_
  * _Hackintool -> System -> System -> VDA Decoder_ (should show '_fully supported_')
  * Or use `VDADecoderChecker`
* [x] Metal
  * _System Information_ -> Graphics/Displays -> Metal: Supported
  * _GLView_
  * _Geekbench_ -> Compute -> Metal
* [x] Intel Quick Sync, H.264 & HEVC (H.265) hardware decoding/encoding
  * _Intel Power Gadget > GFX_ (green line) check while exporting H.264 from FCP-X
* [x] dGPU hardware acceleration

#### Audio

* [ ] Audio out (see in _Audio MIDI Setup_)
* [ ] Audio in
* [ ] Frontpanel audio connectors
* [ ] Audio over HDMI
* [x] Audio quality

#### Sleep & Power

Use _Energy Saver > Restore Defaults_

* [x] Check Hibernate Mode (desktop `0`, laptop `3`): `pmset -g | grep hibernatemode`
* [x] Shutdown (from Apple menu)
* [x] Restart (from Apple menu)
* [ ] Manual Sleep (Apple menu -> Sleep)
* [ ] [Press and hold power button for 1.5 seconds](https://support.apple.com/en-us/HT201236), select Sleep
* [x] Auto Sleep (_System Preferences_ -> Energy Saver)
* [x] Wake by keyboard
* [x] Wake by mouse/trackpad

#### CPU

* [x] CPU Power Management [Optimizing Power Management](https://dortania.github.io/OpenCore-Post-Install/universal/pm.html#optimizing-power-management)
  * Check with _IORegistryExplorer_
* [x] Temperatures and stability with 100% CPU
  * Use _Prime95_ Torture Test

#### Disk

Test with _AJA System Test Lite_

* [x] NVMe SSD (PCIe Gen3 or Gen4 speeds)
* [x] SATA SSD
* [x] TRIM support (_System Information_ -> SATA -> SSD drive)

#### Sensors

Check with HWMonitorSMC2

* [x] CPU
* [x] GPU
* [x] SSD, NVMe, HD
* [x] Fans

#### Keyboard

* [x] Option/Command correctly mapped in macOS
  * For PC Keyboards swap in: _System Preferences_ -> Keyboard -> Modifier Keys
  * Press _Spacebar_ and the key left of the Spacebar. This should show Spotlight
* [x] Fn keys working (Audio Volume keys, etc.)

#### USB

Check with _USBToolBox_ or _Hackintool_ (shows connection speed)

Test external drive speed with _AJA System Test Lite_

* [x] USB 2 ports
* [x] USB 2 on USB 3 ports
* [x] USB 3 and 3.1 ports (check transfer speed during copy)
* [x] USB Type-C ports
* [ ] SD Card Reader
* [ ] Camera (Photo Booth, Facetime, Zoom)
* [ ] Fingerprint reader

#### ThunderBolt

* [ ] File transfer
* [ ] Display

#### Ethernet

* [x] Gigabit LAN (_System Preferences_-> Network -> Ethernet -> Advanced -> Hardware -> Speed should be 1000baseT)
* [x] 2.5GBase-T (especially on Comet Lake and above boards)
* [ ] 10GBase-T (Aquantia with updated firmware)

#### Wifi & Bluetooth

* [x] Wifi transmission speed (Option Click -> Wifi menu bar icon -> check Tx Rate)
* [x] Bluetooth devices (trackpad, mouse, keyboard, headset)
* [x] AirDrop (test with iDevices)
* [x] AirPlay to Mac (macOS Monterey or later, test with iOS 14 or later devices)
  * tap the AirPlay icon on your Apple device to share videos to your Hackintosh
* [ ] Handoff [System requirements for Continuity](https://support.apple.com/en-us/HT204689) and [Use Continuity](https://support.apple.com/en-us/HT204681) which requires macOS Catalina & iOS 13+
* [ ] [Sidecar](https://support.apple.com/en-us/HT210380) requires macOS Catalina or later and a compatible iPad using iPadOS 13 or later.

#### OS Features

* [x] iMessage, FaceTime, App Store, iTunes Store
* [ ] DRM support _(iTunes Movies, Apple TV+. Amazon Prime and Netflix, and others - test in Safari. Requires AMD Polaris or newer GPU.)
</details>

## Notes

Use at your own risk. 

- All `.efi` drivers and `.kext` are `-RELEASE` builds from the respective packages. 
- OpenCanopy (GUI boot menu) is up and running.
- I boot Windows 11 and Gentoo Linux using Opencore, thus I can guarantee it will work. I have Win 11 installed on the same SSD but Gentoo installed on an Optane P1600X that is disabled for this.

Good luck.

## Enabling Secure Boot
Check https://www.reddit.com/r/hackintosh/comments/v91q50/secure_booting_with_oc/

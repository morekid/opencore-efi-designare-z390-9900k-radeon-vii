# OC EFI - Designare Z390 + Radeon VII

[OpenCore](https://dortania.github.io/OpenCore-Install-Guide/) EFI for Gygabite
Designare Z390 motherboards.

[![OpenCore](https://img.shields.io/badge/OpenCore-0.8.5-blue.svg)](https://github.com/acidanthera/OpenCorePkg)
[![macOS-stable](https://img.shields.io/badge/macOS-13.5-brightgreen.svg)](https://www.apple.com/macos/ventura)
[![macOS-stable](https://img.shields.io/badge/macOS-12.6-brightgreen.svg)](https://www.apple.com/macos/monterey)
[![macOS-stable](https://img.shields.io/badge/macOS-10.14-brightgreen.svg)](https://apps.apple.com/us/app/macos-mojave/id1398502828)

## Contents

`EFI - DEBUG` - Debug version of OC and all Kexts, all logging enabled / Slower
boot + verbose boot.  
`EFI - RELEASE` - Release version of OC and all Kexts, all logging disabled /
Faster boot + no verbose.

### Choose config.plist

Both debug and release folders contains two config.plist versions. Depending on
your setup you'll want to choose one of:

1. Use the iGPU for video output:  
   Go to EFI > OC > rename `config-igpu.plist` to `config.plist`.

2. use the Radeon VII for video output and use iGPU in headless mode:  
   Go to EFI > OC > rename `config-headless.plist` to `config.plist`.

### Full desktop configuration:

| Component        | Name                                  | Notes           |
| ---------------- | ------------------------------------- | --------------- |
| Motherboard      | **Gigabyte Designare Z390 (rev 1.0)** | Bios v.F7       |
| CPU              | **Intel Core i9 9900k**               | Coffee Lake     |
| dGPU             | **XFX Radeon VII Aktiv 16GB**         |                 |
| SSD M.2 NVMe     | **Adata XPG SX8200 pro**              |                 |
| SSD M.2 NVMe     | **Samsung 970 EVO Plus**              |                 |
| WiFi / Bluetooth | **Fenvi T919 PCIe**                   | BCM94360CD Chip |
| RAM              | **G.Skill RipJaws V 32GB 3200 DDR4**  |                 |
| Monitor          | **BenQ PD2700U**                      | 27"             |
| FAN              | **Be Quiet PURE LOOP 240mm (BW006)**  |                 |
| Case             | **NZXT H510**                         |                 |

### What works

- [x] iGPU: Intel UHD Graphics 630, full hardware acceleration.
  - [x] DisplayPort (USB-C type) output max: 4K@60Hz.
  - [x] HDMI output max: 4K@30Hz.
- [x] dGPU, full hardware acceleration.
- [x] Audio: Realtek ALC1220 (alcid layout 11).
- [x] WiFi/Bluetooth (w/ Fenvi).
- [x] Ethernet.
- [x] USB (Thanks to
      [seven-of-eleven](https://github.com/seven-of-eleven/designare-z390-opencore-efi)
      for the port map, using n.1 to power the Fenvi card).
- [x] Lifecycle (On, Off, Sleep).
- [x] All iStuff (FaceTime, Messages, etc.).
- [x] OpenCore boot UI (OpenCanopy) and startup chime 🔈.

### What doesn't work

- [ ] DRM, see
      [here](https://dortania.github.io/OpenCore-Post-Install/universal/drm.html#testing-drm)
      for details.

### Not tested

- FileVault.
- Thunderbolt, but no reason it shouldn't work.

## Notes

- BIOS configured as per
  [guide](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#intel-bios-settings).
- You'll need to replace any occurrence of `[CHANGE_ME]` in `OC/config.plist`
  using your own PlatformInfo,
  [see guide](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#platforminfo).
- Tested on Mojave, Monterey, Ventura. Works over full upgrades Mojave >
  Monterey > Ventura or Mojave > Ventura.
- To migrate from Clover to OpenCore it might be enough to replace your existing
  Clover EFI for this, just make sure to:
  - Set your own PlatformInfo (taken from the Clover EFI) to the new one (see
    above).
  - [Cleanup your system from Clover](https://dortania.github.io/OpenCore-Install-Guide/clover-conversion/#cleaning-the-clover-junk-in-macos).

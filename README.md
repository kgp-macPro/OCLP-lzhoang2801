<div align="center">
<img src="docs/images/OC-Patcher.png" alt="OpenCore Patcher Logo" width="256" />
<h1>OCLP 3.0.0 Nightly – Preserved Reference Edition for macOS Tahoe</h1>
</div>

---

## Established Preserved Reference Setup

This repository provides the **established conservative Preserved Reference Edition** of the earlier working OCLP 3.0.0 Nightly Tahoe patch environment using:

**the earlier working lzhoang2801 PatcherSupportPkg with complete Modern Wireless resources and Tahoe `AppleHDA.kext`**

It intentionally retains the historical:

**`amfi=0x80` + `ipc_control_port_options=0`**

AMFI configuration and remains as close as possible to the original Nightly architecture.

For full documentation, compatibility details, proper setup and EFI configuration, see:

**InsanelyMac thread (primary reference):**

https://www.insanelymac.com/forum/topic/362042-experimental-fork-of-oclp-300-nightly-%E2%80%93-modern-wi-fi-awdl-and-applehda-fully-working-under-tahoe/

---

## Three Established Tahoe Approaches

OCLP-CustoMac does not obsolete or withdraw the two earlier KGP Tahoe configurations. All three approaches remain intentionally available.

### 1. OCLP 3.0.0 Nightly – Preserved Reference Edition

Repository: [kgp-macPro/OCLP-lzhoang2801](https://github.com/kgp-macPro/OCLP-lzhoang2801)

- conservative reference environment closest to the earlier working lzhoang2801 OCLP 3.0.0 Nightly Tahoe state;
- uses the earlier working lzhoang2801 PatcherSupportPkg containing Modern Wireless resources and AppleHDA;
- retains the historical `amfi=0x80` and `ipc_control_port_options=0` AMFI path;
- intentionally frozen and preserved for reproducibility, comparison and conservative use.

### 2. OCLP 3.0.0 Nightly – amfipassbeta Edition

Repository: [kgp-macPro/OCLP-lzhoang2801-amfipassbeta](https://github.com/kgp-macPro/OCLP-lzhoang2801-amfipassbeta)

- conservative and extensively tested on real systems over many months;
- remains close to the preserved Nightly architecture;
- uses `AMFIPass.kext + -amfipassbeta`;
- its documented Intel configuration uses a Broadcom `IOName` spoof with AirportItlwm;
- remains fully available; satisfied users do not need to migrate, and migration is optional.

### 3. OCLP-CustoMac

Repository: [kgp-macPro/OCLP-CustoMac](https://github.com/kgp-macPro/OCLP-CustoMac)

Release: [OCLP-CustoMac 3.0.3](https://github.com/kgp-macPro/OCLP-CustoMac/releases/latest)

- current recommended KGP setup for new installations and users who want the further-developed patcher architecture;
- further-developed focused branch with direct Intel detection;
- does not require a Broadcom `IOName` spoof for Intel detection;
- uses `AMFIPass.kext` 1.4.1 + `-amfipassbeta`; `amfi=0x80` is not required;
- selectable Modern Wi-Fi and Modern Audio;
- automatic and optional manual KDK selection;
- strengthened root-patch recovery;
- APFS internal resources;
- reproducible, validated builds.

In contrast to this Preserved Reference Edition, both the amfipassbeta Edition and OCLP-CustoMac use `AMFIPass.kext` 1.4.1 + `-amfipassbeta`; `amfi=0x80` is not required for their validated configurations. The Preserved Reference Edition itself intentionally retains `amfi=0x80` + `ipc_control_port_options=0` and does not use that AMFIPass configuration.

---

## Overview

This repository preserves a reproducible working state of the final **OCLP 3.0.0 Nightly snapshot (Dec 24, 2025)** by lzhoang2801 for macOS Tahoe 26.x.

The original snapshot is no longer directly usable on Tahoe due to incomplete PatcherSupportPkg resources.

This repository restores the functionality required for modern AppleHDA, Wi-Fi and AWDL support by redirecting the Universal-Binaries download to a preserved PatcherSupportPkg including AppleHDA.

No original Tahoe root patch logic has been modified.

---

## Scope Clarification

This repository is intended exclusively for advanced Hackintosh systems running macOS Tahoe 26.x.

It is NOT a general unsupported-Mac patching project.

No additional graphics acceleration patches or unsupported-Mac root patch frameworks are included.

This repository intentionally remains as close as possible to the original OCLP 3.0.0 Nightly Tahoe baseline released by the OCLP developers and later preserved by lzhoang2801.

The fork only enables and preserves the original Tahoe patch functionality already implemented by the OCLP developers.

---

## Functionality

### Modern Audio / AppleHDA

- modern audio (AppleHDA)

### Broadcom Modern Wireless

The validated Broadcom path includes:

- Wi-Fi
- AirDrop (bidirectional)
- AirPlay (bidirectional)
- Screen Mirroring (bidirectional)
- Personal Hotspot
- Continuity Camera
- Handoff (e.g. Mail, Notes, Safari)

**Broadcom / AppleVTD:** For users who want to keep AppleVTD/IOMMU enabled
with legacy Broadcom Wi-Fi under macOS Tahoe, see the independent experimental
[BroadcomVTD-Tahoe](https://github.com/kgp-macPro/BroadcomVTD-Tahoe)
project (`BroadcomVTD.kext`). The Modern Wireless root-patch environment
restores the legacy Broadcom stack under Tahoe; BroadcomVTD-Tahoe addresses
the additional kernel-resident Tahoe runtime DMA/IOMMU compatibility problem
observed when the restored AirPortBrcmNIC stack operates with AppleVTD enabled.

Discussion threads:

- [InsanelyMac](https://www.insanelymac.com/forum/topic/363186-broadcomvtd-tahoe-broadcom-wi-fi-with-applevtd-enabled-on-macos-tahoe/)
- [TonyMacx86](https://www.tonymacx86.com/threads/broadcomvtd-tahoe-broadcom-wi-fi-with-applevtd-enabled-on-macos-tahoe.333357/)

### Intel Wi-Fi

Intel Wi-Fi operation depends on external AirportItlwm. Current AirportItlwm does not provide the complete native AWDL control/data path required for reliable bidirectional AirDrop, Personal Hotspot or Continuity Camera.

Intel therefore does not inherit the complete Broadcom AWDL/Continuity claim above.

### Sidecar

- currently not functional

---

## Requirements

- Boot argument:  
  `amfi=0x80`

- Recommended:  
  `ipc_control_port_options=0`

- A suitable **Kernel Debug Kit (KDK)** is required for OCLP root patching

For full documentation, compatibility details and updates, see:

**InsanelyMac thread (primary reference):**  
https://www.insanelymac.com/forum/topic/362042-experimental-fork-of-oclp-300-nightly-%E2%80%93-modern-wi-fi-awdl-and-applehda-fully-working-under-tahoe/

---

## PatcherSupportPkg Dependency

This repository depends on:

https://github.com/kgp-macPro/PatcherSupportPkg-lzhoang2801

This PatcherSupportPkg provides the required Universal-Binaries including AppleHDA.

### Payload Provenance

The final publicly released lzhoang2801 OCLP 3.0.0 Nightly configuration references a newer PatcherSupportPkg that no longer contains the required Tahoe `AppleHDA.kext` expected by its Modern Audio patch definition. Consequently, when Modern Audio is applicable, that final published configuration cannot complete the expected Tahoe Root Patch because the required AppleHDA payload is absent.

This Preserved Reference Edition intentionally uses an earlier working lzhoang2801 PatcherSupportPkg. That earlier package retains the required Modern Wireless resources and `AppleHDA.kext`; its relevant Modern Wireless framework variants are the earlier ad-hoc-signed versions.

This provenance statement does not claim that entire PatcherSupportPkg repositories are globally byte-identical.

---

## Repository Scope

This repository:

- preserves the original OCLP 3.0.0 Nightly Tahoe state
- restores missing resources required for modern AppleHDA, Wi-Fi and AWDL functionality
- preserves the original `amfi=0x80` workflow
- does **not introduce any new patch logic**

---

## Important Notes

- this fork only enables and preserves the original Tahoe patch functionality already implemented by the OCLP developers
- this fork is **not supported by the OCLP developers**
- intended exclusively for **advanced Hackintosh configurations**
- modern audio (AppleHDA) and the validated Broadcom Modern Wireless AWDL/Continuity path are expected to work reliably; Intel remains subject to external AirportItlwm limitations
- no additional graphics acceleration or unsupported-Mac root patch frameworks are included
- always keep a bootable backup before applying root patches

---

## Community & Discussion

Additional discussion:

**tonymacx86 (mirror thread):**  
https://www.tonymacx86.com/threads/experimental-fork-of-oclp-3-0-0-nightly-modern-wi-fi-awdl-and-applehda-fully-working-under-tahoe-26-x.332849/

---

## Credits

- Dortania OCLP Team (original OCLP authors and developers)
- [crystall1nedev](https://github.com/crystall1nedev) (Eva Isabella Luna) (original OCLP 3.0.0 Nightly release)
- [lzhoang2801](https://github.com/lzhoang2801) (original OCLP 3.0.0 Nightly fork)
- [kgp-macPro](https://github.com/kgp-macPro) (preservation, maintenance, AMFIPass integration, AppleHDA restoration, testing and documentation)
- [YBronst](https://github.com/YBronst) (OCLP Nightly development)
- badbrain (boot-arg ipc_control_port_options=0 support)
- [zxystd](https://github.com/zxystd) (itlwm/AirportItlwm project)
- [lshbluesky](https://github.com/lshbluesky) (IntelBluetoothFirmware maintenance and releases)
- [Vinhts](https://github.com/Vinhts) (IntelBTPatcher Tahoe 26.5 Bluetooth LE fixes)
- [Z3c0ld](https://github.com/Z3c0ld) (IntelBTPatcher Tahoe 26.5 Bluetooth LE fixes)
- InsanelyMac community
- tonymacx86 community (mirror thread)

For a complete list of OpenCore Legacy Patcher contributors, please refer to the original Dortania repository:

https://github.com/dortania/OpenCore-Legacy-Patcher

---

## Maintainer

Maintained by **kgp**

- GitHub: https://github.com/kgp-macPro
- InsanelyMac: kgp (formerly KGP-iMacPro)
- tonymacx86: kgp

---

## Disclaimer

This repository provides a preserved Tahoe patch environment intended for advanced Hackintosh systems.

Not intended for unsupported Macs requiring graphics acceleration root patches.

Use at your own risk.

---

If this preserved reference repository was useful to you:

A coffee is always appreciated ☕  
https://buymeacoffee.com/kgp.macpro

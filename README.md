<div align="center">
<img src="docs/images/OC-Patcher.png" alt="OpenCore Patcher Logo" width="256" />
<h1>OCLP 3.0.0 Nightly – Preserved Reference Edition for macOS Tahoe</h1>
</div>

---

## Recommended Setup: amfipassbeta Edition

A newer recommended variant of this setup is available:

👉 https://github.com/kgp-macPro/OCLP-lzhoang2801-amfipassbeta

It supports **AMFIPass.kext with `-amfipassbeta`** and does not require `amfi=0x80`.

This repository is preserved primarily as a historical and reproducible reference environment for the original `amfi=0x80` workflow.

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

The following components are currently confirmed functional:

- modern audio (AppleHDA)
- modern Wi-Fi (Broadcom + supported Intel chipsets)

AWDL stack:
- AirDrop (bidirectional)
- AirPlay
- Screen Mirroring

Continuity:
- Handoff (e.g. Mail, Notes, Safari)
- Sidecar (currently not functional)

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
- only modern audio (AppleHDA) and modern Wi-Fi + AWDL functionality are expected to work reliably
- no additional graphics acceleration or unsupported-Mac root patch frameworks are included
- always keep a bootable backup before applying root patches

---

## Community & Discussion

Additional discussion:

**tonymacx86 (mirror thread):**  
https://www.tonymacx86.com/threads/experimental-fork-of-oclp-3-0-0-nightly-modern-wi-fi-awdl-and-applehda-fully-working-under-tahoe-26-x.332849/

---

## Credits

- Dortania OCLP Team (development)
- lzhoang2801 (original Tahoe fork)
- kgp (preservation, maintenance, AppleHDA restoration, testing and documentation)
- badbrain (boot-arg `ipc_control_port_options=0` support)
- InsanelyMac community
- tonymacx86 community (mirror thread)

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
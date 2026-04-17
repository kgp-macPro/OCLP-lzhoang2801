<div align="center">
<img src="docs/images/OC-Patcher.png" alt="OpenCore Patcher Logo" width="256" />
<h1>Preserved Tahoe Patchset Reference (OCLP 3.0.0 Nightly state)</h1>
</div>

---

## Recommended Setup: amfipassbeta Variant

A newer variant of this setup is available:

👉 https://github.com/kgp-macPro/OCLP-lzhoang2801-amfipassbeta

It supports **AMFIPass.kext with `-amfipassbeta`** and does not require `amfi=0x80`.

**This repository is kept as a reference for the original `amfi=0x80` workflow.**

---

## Overview

This repository preserves a reproducible working state of the final **OCLP 3.0.0 Nightly snapshot (Dec 24, 2025)** by lzhoang2801.

The original snapshot is no longer directly usable on macOS Tahoe due to missing **AppleHDA** in the referenced PatcherSupportPkg.

This repository restores functionality by redirecting the Universal-Binaries download to a preserved version including AppleHDA.

**No root patch logic has been modified.**

---

## Functionality

The following components are confirmed working:

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

- A suitable **Kernel Debug Kit (KDK)** is required for root patching  

For full documentation, compatibility details and updates, see:

**InsanelyMac thread (primary reference):**  
https://www.insanelymac.com/forum/topic/362042-experimental-fork-of-oclp-300-nightly-%E2%80%93-modern-wi-fi-awdl-and-applehda-fully-working-under-tahoe/

---

## PatcherSupportPkg Dependency

This repository depends on:

https://github.com/kgp-macPro/PatcherSupportPkg-lzhoang2801

Provides the required Universal-Binaries including AppleHDA.

---

## Repository Scope

This repository:

- preserves the original OCLP 3.0.0 Nightly state  
- restores missing resources (AppleHDA)  
- does **not introduce new patch logic**  

---

## Important Notes

- this fork is **not supported by the OCLP developers**  
- intended for **advanced Hackintosh configurations only**  
- only modern audio (AppleHDA) and modern Wi-Fi + AWDL are expected to work  
- always keep a bootable backup before applying root patches  

---

## Community & Discussion

Additional discussion:

**tonymacx86 (mirror thread):**  
https://www.tonymacx86.com/threads/experimental-fork-of-oclp-3-0-0-nightly-modern-wi-fi-awdl-and-applehda-fully-working-under-tahoe-26-x.332849/

---

## Credits

- Dortania OCLP Team  
- lzhoang2801  
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

This is an experimental preservation setup for advanced Hackintosh environments.

Use at your own risk.
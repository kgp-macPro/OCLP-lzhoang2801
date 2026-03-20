<div align="center">
<img src="docs/images/OC-Patcher.png" alt="OpenCore Patcher Logo" width="256" />
<h1>Preserved Tahoe Patchset Reference (OCLP 3.0.0 Nightly state)</h1>
</div>

---

## ⚠️ Update: amfipassbeta Variant Available

A newer variant of this preserved OCLP 3.0.0 setup is now available, supporting **AMFIPass.kext with the boot argument `-amfipassbeta`**.

This allows full functionality **without requiring `amfi=0x80`**, improving compatibility with applications.

👉 New repository:  
https://github.com/kgp-macPro/OCLP-lzhoang2801-amfipassbeta

The amfipassbeta variant is recommended for most users.

This original repository remains available as a reference for the `amfi=0x80` workflow.

---

This repository contains a preserved working state of the Tahoe patchset as it existed in the final lzhoang2801 OCLP 3.0.0 Nightly snapshot (Dec 24, 2025), which is no longer directly reproducible under macOS Tahoe due to missing resources (AppleHDA) in the referenced PatcherSupportPkg.

In the Dec 24, 2025 snapshot, the last upstream commit references Universal-Binaries from an upstream PatcherSupportPkg source whose distributed Universal-Binaries package does not include AppleHDA.  
As a result, the modern audio (AppleHDA) root patch cannot be applied from that snapshot without providing a Universal-Binaries package that contains AppleHDA.

This repository restores a working state by redirecting the Universal-Binaries download to a preserved mirror that includes AppleHDA (and thus matches the intended Tahoe patchset requirements). No new patches are introduced; only the original resource location was restored.

This fork is **not an official upstream release** of OpenCore Legacy Patcher and is not affiliated with or supported by the Dortania OCLP project.

This fork aims to restore:
- modern audio (AppleHDA)
- modern Wi-Fi
- Apple Wireless Direct Link (AWDL: AirDrop, AirPlay, Screen Mirroring)
on advanced Hackintosh systems running macOS Tahoe 26.x. 

Do **not** apply root patches on unsupported native Macs or on Hackintosh systems with unsupported hardware (e.g. GPUs). Apart from modern Wi-Fi and modern audio, other root patches are expected to fail.

## Functionality Status

The following functionality has been verified under macOS Tahoe 26.x:

modern audio (AppleHDA) -- functional  
modern Wi-Fi -- functional  

AWDL stack:
- AirDrop -- fully functional, bidirectional  
- AirPlay -- functional  
- Screen Mirroring -- functional  

Continuity:
- Handoff -- functional (e.g. Mail, Notes, Safari)  
- Sidecar -- currently not functional  

This fork is provided for documentation and testing purposes only and reflects development work originally carried out by the OCLP contributors.

This repository represents a preserved reference implementation of the original Tahoe patchset workflow and is not an actively developed continuation of the patcher.

Active development of the Tahoe patchset continues in the OpenCore Legacy Patcher branch maintained by YBronst (MakAsrock):  
https://github.com/YBronst/OpenCore-Legacy-Patcher/releases

---

## AMFI / Signing notice

The distributed binaries are unsigned. Therefore, when using **AMFIPass.kext**, the boot argument:

`amfi=0x80`

is required in this variant.

Alternatively, use the amfipassbeta-based variant linked above, which allows proper AMFIPass usage without `amfi=0x80`.

With `amfi=0x80`, some applications (for example Firefox) may fail to start.  
To mitigate this behavior, additionally use:

`ipc_control_port_options=0`

*(credits to badbrain)*

---

## Important dependency

Root patching requires **PatcherSupportPkg** resources provided by this preserved mirror:

https://github.com/kgp-macPro/PatcherSupportPkg-lzhoang2801

If this repository becomes unavailable or private, required downloads will fail.

---

## What was changed here

- Redirected PatcherSupportPkg downloads to the preserved mirror containing the full Universal-Binaries.dmg (including AppleHDA)  
- No root patch logic was modified  

---

## Important compatibility notice

Early reports suggested that macOS Tahoe 26.4 introduced fundamental changes to the system patching workflow related to HFS+ based patch images.  
Further testing has shown that this assumption was incorrect.

The issues observed in **macOS 26.4 beta 1** were most likely caused by a temporary **HFS+ mounting bug**, which Apple already fixed in **beta 2**.

The remaining problems encountered during root patching were caused by the absence of a **matching Kernel Debug Kit (KDK)**.  
The required KDK was not released until **macOS 26.4 beta 4**.

With **macOS 26.4 beta 4 and the corresponding KDK installed**, root patching works again with the following patcher versions:

- **OCLP 3.0.0 Nightly** (this repository)  
- **OCLP 3.0.0 Nightly (amfipassbeta variant)**  
- **OCLP-Mod 3.1.7**  
- **OCLP 3.1.7 Nightly**  

All four patchers can successfully apply the modern Wi-Fi and modern audio (AppleHDA) root patches when the matching KDK is available.  
All four patchsets also provide full Apple Wireless Direct Link (AWDL) functionality.

- **OCLP 3.0.0 Nightly (amfipassbeta variant)** and **OCLP-Mod 3.1.7** work with **AMFIPass.kext + `-amfipassbeta`**  
- **OCLP 3.0.0 Nightly** and **OCLP 3.1.7 Nightly** require **`amfi=0x80`**

---

This repository serves as a stable reference environment for macOS Tahoe 26.0–26.4 systems requiring fully working modern Wi-Fi and AppleHDA audio.

Active development of the Tahoe patchset continues in the OpenCore Legacy Patcher branch maintained by YBronst (MakAsrock):  
https://github.com/YBronst/OpenCore-Legacy-Patcher/releases

---

## Setup Guidelines and Community Discussion

Detailed setup instructions, prerequisites, troubleshooting tips and ongoing discussion can be found in the following threads:

**InsanelyMac:**  
https://www.insanelymac.com/forum/topic/362042-experimental-fork-of-oclp-300-nightly-%E2%80%93-modern-wi-fi-awdl-and-applehda-fully-working-under-tahoe/

**tonymacx86 (mirror thread):**  
https://www.tonymacx86.com/threads/experimental-fork-of-oclp-3-0-0-nightly-modern-wi-fi-awdl-and-applehda-fully-working-under-tahoe-26-x.332849/

---

## Credits

This repository builds upon the work of the OpenCore Legacy Patcher project and its contributors.

Special thanks to:

- Dortania OCLP Team  
- lzhoang2801  
- All PatcherSupportPkg contributors  

---

## Maintainer

This preservation repository is maintained by **kgp**.  

Online identities:

- GitHub: https://github.com/kgp-macPro  
- InsanelyMac: kgp (formerly KGP-iMacPro)
- tonymacx86: kgp  

---

## Disclaimer

This is **not an official Dortania release** and is intended for complex Hackintosh configurations.

---
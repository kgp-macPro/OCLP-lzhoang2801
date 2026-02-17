<div align="center">
<img src="docs/images/OC-Patcher.png" alt="OpenCore Patcher Logo" width="256" />
<h1>Experimental Fork of OCLP 3.0.0 Nightly</h1>
</div>

This repository contains a preserved state of **lzhoang2801's fork of OCLP 3.0.0 Nightly** (last upstream commit: Dec 24, 2025). The original upstream state from Dec 24, 2025 is not capable of successfully applying root patches.

The failure is caused by missing AppleHDA resources inside the required PatcherSupportPkg Universal-Binaries package referenced by the patcher. Root patching fails even though the patchset itself is otherwise functional.

This repository restores a working state by allowing OCLP to access preserved resources with ApplHDA required by that patchset.

This fork is **not an official upstream release** of OpenCore Legacy Patcher and is not affiliated with the Dortania OCLP project.

This fork exclusively aims to restore modern Wi-Fi (including AirDrop and AirPlay) and modern audio (AppleHDA) on advanced Hackintosh systems running macOS 26 Tahoe.

This fork is not officially supported by the OCLP developers. It only reflects the development work already done by the original OCLP contributors.

Do **not** apply root patches on unsupported native Macs or on Hackintosh systems with unsupported hardware (e.g. GPUs). Apart from modern Wi-Fi and modern audio, other root patches are expected to fail.

This fork is intended solely for testing the development state of the upcoming OpenCore Legacy Patcher 3.0.0 with regard to modern Wi-Fi and modern audio functionality.

---

## AMFI / Signing notice

The distributed binaries are unsigned and therefore cannot be used together with **AMFIPass.kext**.

AMFIPass requires a properly signed OCLP release. Until an official signed release of OCLP 3.0.0 becomes available, disable AMFIPass.kext and use:

amfi=0x80


After disabling AMFI, some applications (for example Firefox) may fail to start.  
To mitigate this behavior, additionally use:

ipc_control_port_options=0


(credits to badbrain)

---

Initial testing showed stable and reliable Wi-Fi (including AirDrop and AirPlay) and AppleHDA functionality, which should satisfy the requirements of most modern Hackintosh systems.

For setup guidelines, prerequisites and community discussion see:  
https://www.insanelymac.com/forum/topic/362042-experimental-fork-of-oclp-300-nightly-%E2%80%93-wi-fi-airdropairplay-and-applehda-fully-working-under-tahoe/ or https://www.tonymacx86.com/threads/experimental-fork-of-oclp-3-0-0-nightly-wi-fi-airdrop-airplay-and-applehda-fully-working-under-tahoe.332849/

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

## Credits

All credit belongs to the original authors and contributors:

- Dortania OpenCore Legacy Patcher team
- lzhoang2801 for the Tahoe patchset work
- PatcherSupportPkg contributors
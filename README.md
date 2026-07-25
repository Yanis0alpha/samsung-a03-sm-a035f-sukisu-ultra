# SukiSU Ultra Kernel — Samsung Galaxy A03 (SM-A035F)

Custom Android kernel with root support (KernelSU / SukiSU Ultra), built for the **Samsung Galaxy A03 (SM-A035F, Unisoc T606)**. This is the SUSFS-free variant — no susfs4ksu hooks, no `set_memory.h` backport needed.

![Device](https://img.shields.io/badge/device-SM--A035F-blue)
![SoC](https://img.shields.io/badge/SoC-Unisoc%20T606-blue)
![Kernel](https://img.shields.io/badge/kernel-4.14%20%2F%204.19-orange)
![Root](https://img.shields.io/badge/root-SukiSU%20Ultra-green)
![License](https://img.shields.io/badge/license-GPL--2.0-lightgrey)

## Overview

This kernel brings root support to a device family (Unisoc T606, budget Samsung A-series) that has very little official support from the custom-kernel community. It was built and iterated entirely on a low-spec machine (Compaq Presario CQ62) using Google Colab for compilation.

## Features

- **SukiSU Ultra** integration (build 40798) — root management with KPM support
- No SUSFS layer — lighter, fewer moving parts, no mount/root hiding
- Bootloop diagnostics via pstore/ramoops during bring-up

## Compatibility

| Device | Model | SoC | Status |
|---|---|---|---|
| Galaxy A03 | SM-A035F | Unisoc T606 | ✅ Tested, daily driver |

Tested against **VoltageOS** (GSI) as the primary ROM.

## Build

Built via **Google Colab** (no local toolchain required). Build script and instructions: see [`docs/BUILDING.md`](docs/BUILDING.md).

```bash
# high-level flow
1. Clone this repo
2. Run the Colab build notebook
3. Flash via AnyKernel3
```

## Installation

1. Unlock bootloader (SM-A035F, Unisoc preloader-based verification — see notes in `docs/`)
2. Flash a compatible GSI (VoltageOS recommended) or stock-based ROM
3. Flash this kernel via recovery/fastboot using the AnyKernel3 zip from [Releases](../../releases)
4. Install the SukiSU Ultra manager APK to complete root setup

## Known issues / limitations

- Battery charge control via sysfs is currently blocked by SELinux policy (not yet resolved)
- GKI-mode OTA slot switching untested on this device

## Credits

See [CREDITS.md](CREDITS.md) for full attribution to upstream projects and authors.

## License

This project is licensed under **GPL-2.0-only**, consistent with the Linux kernel and upstream KernelSU/SukiSU Ultra licensing. See [LICENSE](LICENSE).

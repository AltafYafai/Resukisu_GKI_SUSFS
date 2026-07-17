# GKI KernelSU-Next SUSFS
### Automated Kernel Build Repository for KernelSU-Next

**Automated GKI Kernel Builds | Integrated KernelSU-Next + SUSFS**

[![Release](https://img.shields.io/github/v/release/altafyafai/GKI_KernelSU-Next_SUSFS?label=Release&style=flat-square&logo=github&logoColor=white&color=2ea44f)](https://github.com/altafyafai/GKI_KernelSU-Next_SUSFS/releases)
[![Telegram](https://img.shields.io/static/v1?label=Telegram&message=Channel&color=0088cc)](https://t.me/ReSukiSUKernelBuilds)
[![KernelSU-Next](https://img.shields.io/badge/KernelSU--Next-Supported-5AA300?style=flat-square)](https://github.com/KernelSU-Next/KernelSU-Next)
[![SUSFS](https://img.shields.io/badge/SUSFS-Integrated-E67E22?style=flat-square)](https://gitlab.com/simonpunk/susfs4ksu)

---

## ⚠️ Repository Disclaimer

1. This repository is a fork of [zzh20188/GKI_KernelSU_SUSFS](https://github.com/zzh20188/GKI_KernelSU_SUSFS/). Only minor updates and bug fixes have been applied here. For general builds, please consider using the upstream repository.

2. This repository has been migrated to support building kernels with **KernelSU-Next**.

---

## ⚠️ Key Updates

> **Note:** OnePlus ColorOS 14 and 15 are currently not supported; flashing might require a factory reset to boot.

> **KernelSU-Next:** The default variant has been set to **KernelSU-Next**, leveraging the standard `next` branch (or `next-susfs` branch from `pershoot` when SUSFS is active).

> **rekernel (Beta):** Supported rekernel features.

---

## 🧪 Droidspaces Container Support (Experimental)

> **Experimental Feature:** Successful booting is not guaranteed. Make sure to back up your stock Boot image before flashing.
>
> **Tip:** The workflow uses the [Official Patches](https://github.com/ravindu644/Droidspaces-OSS/tree/main/Documentation/resources/kernel-patches/GKI) from [Droidspaces](https://github.com/ravindu644/Droidspaces-OSS). 

[Droidspaces](https://github.com/ravindu644/Droidspaces-OSS) is a lightweight Linux container tool that runs a full Linux environment on Android.

**Support range:** 5.10 / 5.15 / 6.1 / 6.6 / 6.12

**Usage:** When running the workflow manually, select the `Droidspaces` option.

---

## 🧪 Masquerade `/proc/config.gz` (Stock Config)

This is an advanced feature. The build automatically checks if `config/stock_defconfig` exists: if it does, it applies it; if not, it skips it.

**Usage:**
1. Ensure your device is currently running Stock ROM + Stock Kernel.
2. Obtain `/proc/config.gz` from the device.
3. Extract it, rename it to `stock_defconfig`, and commit it to the [`config/`](config/) directory of this repository.

The build process will automatically:
- Copy it to the kernel source: `$KERNEL_ROOT/common/arch/arm64/configs/stock_defconfig`
- Change the rule for `$(obj)/config_data` in `$KERNEL_ROOT/common/kernel/Makefile` to use your stock config instead.
- Make the output `/proc/config.gz` match your stock kernel config.

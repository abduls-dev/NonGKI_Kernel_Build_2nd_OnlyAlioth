<h2 align="center">Non-GKI Kernel Build</h2>

<p align="center">
  English | <a href="README_ru.md">Русский</a> | <a href="README_cn.md">中文说明</a> | <a href="Supported_list.md">Supported List</a> | <a href="https://github.com/JackA1ltman/NonGKI_Kernel_Build_2nd/wiki">Wiki</a> | <a href="https://t.me/+F6v29fKeXrUyYjI1">Telegram Group</a>
</p>
<p align="center">
  <img alt="GitHub Actions Workflow Status" src="https://img.shields.io/github/actions/workflow/status/JackA1ltman/NonGKI_Kernel_Build_2nd/build-release.yml?branch=mainline&style=for-the-badge"> <img alt="GitHub Downloads (all assets, latest release)" src="https://img.shields.io/github/downloads/JackA1ltman/NonGKI_Kernel_Build_2nd/latest/total?style=for-the-badge">
 <img alt="GitHub License" src="https://img.shields.io/github/license/JackA1ltman/NonGKI_Kernel_Build_2nd?style=for-the-badge">
</p>

> [!NOTE]
> **Version 2.0**  
> **Get Sample：[sample](https://github.com/JackA1ltman/NonGKI_Kernel_Build_2nd/tree/sample)**

### Introduction

The initial goal of this project was to provide a relatively stable channel for compiling and updating **KernelSU** and **SUSFS** for a wider range of **Non-GKI** kernels.

It also aims to provide an easier compilation process using **GitHub Actions**, which not only makes it easier for us to maintain but also allows you to use our project to compile your own kernels.

> [!IMPORTANT]
>We are based on the [GPLv3 License](LICENSE)
>
>We permit:
>  - Forking and using for personal compilation.
>  - Staring this project.
>  - Contributing to the project.
>  - Small-scale sharing of compilation results based on open-source and free provision.
>
>We do not permit:
>  - Using this project to provide paid services.
>  - Engaging in commercial activities without consent.

---

### Features

- [x] **Architecture**
  - [x] Unified submodules for updates.
  - [x] Relatively independent variable calls.
  - [x] Variables that don't require additional association.
- [x] **Modules**
  - [x] No need to modify submodules unless there are special requirements.
  - [x] Submodules are easy to understand and learn from.
- [x] **Ease of Use**
  - [x] If you don't need SUSFS, you can compile directly after modifying only a few variables.
  - [x] Easier to fill out and call patches after locally generating SUSFS patch files.
  - [x] Multiple branches ensure it's easy to find example YAML files after forking.
- [x] **System**
  - [x] Supports Ubuntu 20.04 - 24.04.
  - [x] Supports Arch Linux.
  - [x] Supports compilation on x86_64.
  - [ ] Supports compilation on ARM64.
- [x] **Compilation**
  - [x] Supports ARM64 kernels.
  - [ ] Supports ARM (ARMv7-A) kernels. (Aborted support.)

---

### 📊 Poco F3 Kernel Patch Compatibility Matrix

| Patch / Feature | LineageOS (`sm8250`) | E404 (`sm8250`) | Butterfly / Rezadinosaurus (`sm8250`) | Notes |
|---|:---:|:---:|:---:|---|
| **KernelSU** (`kernelsu_fork`) | ✅ All forks | ✅ All forks | ✅ All forks | BakaSU, Next, SukiSU-Nova, xxKSU, rsuntk |
| **SUSFS (v2.4.0)** (`susfs_enable`) | ✅ Supported | ✅ Supported | ❌ **Not Supported** | Patch conflicts with Butterfly tree; use **NoMount** |
| **NoMount** (`nomount_enable`) | ✅ Supported | ✅ Supported | ✅ **Built-in** | `CONFIG_NOMOUNT` is natively built into Butterfly Kernel |
| **KPM (Kernel Patch Module)** (`kpm_enable`) | ✅ Supported | ❌ **Not Supported** | ✅ **Supported** | E404 does not support KPM; Butterfly includes `set_memory.h` |
| **Re:Kernel** (`rekernel_enable`) | ✅ Supported | ✅ Supported | ✅ Supported | Requires cgroup v2 freezer (supported on all 3 kernels) |
| **fgetpriority** (`fgetpriority_enable`) | ✅ Supported | ✅ Supported | ✅ Supported | Hides `getpriority` syscall from detection |
| **VPNHide Next** (`vpnhide_enable`) | ✅ Supported | ✅ Supported | ✅ Supported | Hides VPN interface from apps |
| **Baseband Guard (BBG)** (`bbg_enable`, `bbg_boot`) | ✅ Supported | ✅ Supported | ✅ Supported | Modem protection + optional boot partition write-lock |
| **Droidspaces (LXC/Docker)** (`droidspaces_enable`) | ✅ Supported | ✅ Supported | ✅ Supported | Namespace and cgroup containers |
| **RTL8812AU USB Wi-Fi** (`rtl8812au_enable`) | ✅ Supported | ✅ Supported | ✅ Supported | Built into kernel (built-in 88XXau / Monitor Mode) |
| **Disable LTO/CFI** (`disable_lto_cfi`) | ✅ Supported | ✅ Supported | ✅ Supported | Disables LTO_CLANG / LTO_GCC / CFI |
| **Compiler / Toolchain** | **AOSP Clang** (20.0) | **LLVM/Clang** (22.1.3) | **GNU GCC** (aarch64-linux-gnu) | Butterfly is strictly compiled with GNU GCC |

---

### Acknowledgements

- Thanks to the contributors of the [Version 1.x series](https://github.com/JackA1ltman/NonGKI_Kernel_Build) (in no particular order):
  - [@adontoo](https://github.com/adontoo)
  - [@PeterTea5822](https://github.com/PeterTea5822)
  - [@pkczc](https://github.com/pkczc)
  - [@yu13140](https://github.com/yu13140)
- Thanks to [KernelSU_Action](https://github.com/xiaoleGun/KernelSU_Action) - @xiaoleGun for providing much of the inspiration for this project.
- Thanks to every user who has provided an **Issue**.
- Thanks to the users who provided **Issues** or ideas for this project on **CoolAPK**.

### Copyright
- [KernelSU](https://github.com/tiann/KernelSU) - @tiann
  - [rsuntk](https://github.com/rsuntk/KernelSU) - @rsuntk
    - [rsuntk-SUSFS](https://github.com/cyberc3dr/KernelSU) - @cyberc3dr
  - [xxKSU](https://github.com/backslashxx/KernelSU) - @backslashxx
  - [SukiSU-Nova](https://github.com/SukiSU-Nova/SukiSU-Nova) - @ShirkNeko
    - [BakaSU](https://github.com/Baka-SU/BakaSU) - @BakaSU Development
      - [ReSukiSU_CI](https://github.com/cctv18/ReSukiSU_CI) - @cctv18
  - [Next](https://github.com/KernelSU-Next/KernelSU-Next) - @rifsxd
- [SUSFS](https://gitlab.com/simonpunk/susfs4ksu) - @simonpunk
- [Re:Kernel](https://github.com/Sakion-Team/Re-Kernel) - @Sakion-Team
- [Baseband Guard](https://github.com/vc-teahouse/Baseband-guard) - @秋刀鱼
- [Droidspaces](https://github.com/ravindu644/Droidspaces-OSS) - @ravindu644
- [NoMount](https://github.com/maxsteeel/nomount) - @maxsteeel
- [fgetpriority](https://github.com/aerath-stuff/fgetpriority) - @aerath-stuff
- [VPNHide Next](https://github.com/soranerai/vpnhide_next) - @soranerai
- [RTL8812AU](https://github.com/aircrack-ng/rtl8812au) - @aircrack-ng
- Kernel authors: [LineageOS](https://github.com/LineageOS/android_kernel_xiaomi_sm8250), [@kvsnr113](https://github.com/kvsnr113/xiaomi_sm8250_kernel_e404), [@rezadinosaurus](https://github.com/rezadinosaurus/android_kernel_qcom_sm8250)

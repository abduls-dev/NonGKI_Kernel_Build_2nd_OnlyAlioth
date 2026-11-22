| Device | Location | Codename | Kernel/Author/Name | Branches | Pack Method | KernelSU | SUSFS | Hook | KPM | Re:Kernel | BBG | NoMount | Droidspaces | fgetpriority | VPNHide | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Xiaomi Poco F3 (LineageOS) | All | alioth | [4.19/LineageOS/sm8250](https://github.com/LineageOS/android_kernel_xiaomi_sm8250) | `lineage-24.0`, `lineage-23.2`, `lineage-22.2`, `lineage-21` | AnyKernel3 | BakaSU / Next / xxKSU / rsuntk / SukiSU | ✅ (opt., BakaSU) | Inline / Syscall | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | Stable |
| Xiaomi Poco F3 (E404) | All | alioth | [4.19/kvsnr113/E404](https://github.com/kvsnr113/xiaomi_sm8250_kernel_e404) | `main`, `main-bpf`, `a17`, `staging` + 27 branches (all 31 branches) | AnyKernel3 (kvsnr113) | BakaSU / Next / xxKSU / rsuntk / SukiSU | ✅ (opt., BakaSU) | Inline / Syscall | ❌ (не поддерживается) | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | Untested |
| Xiaomi Poco F3 (Butterfly) | All | alioth | [4.19/rezadinosaurus/sm8250](https://github.com/rezadinosaurus/android_kernel_qcom_sm8250) | `lineage-latte` (AOSP/CLO), `lineage-mocca` (MIUI/HOS) | AnyKernel3 | BakaSU / Next / xxKSU / rsuntk / SukiSU | ❌ (конфликт, исп. NoMount) | Inline / Syscall | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | ✅ (встроен) | ✅ (opt.) | ✅ (opt.) | ✅ (opt.) | Stable |

---

### 📊 Patch Compatibility Matrix / Матрица совместимости патчей

| Патч / Функция (Workflow Option) | LineageOS (`sm8250`) | E404 (`sm8250`) | Butterfly / Rezadinosaurus (`sm8250`) | Примечания / Notes |
|---|:---:|:---:|:---:|---|
| **KernelSU** (`kernelsu_fork`) | ✅ Все форки | ✅ Все форки | ✅ Все форки | BakaSU, Next, SukiSU-Nova, xxKSU, rsuntk |
| **SUSFS (v2.4.0)** (`susfs_enable`) | ✅ Поддерживается | ✅ Поддерживается | ❌ **Не поддерживается** | В Butterfly патч конфликтует с кодом ядра; используйте **NoMount** |
| **NoMount** (`nomount_enable`) | ✅ Поддерживается | ✅ Поддерживается | ✅ **Встроен в ядро** | В Butterfly Kernel `CONFIG_NOMOUNT` встроен автором из коробки |
| **KPM (Kernel Patch Module)** (`kpm_enable`) | ✅ Поддерживается | ❌ **Не поддерживается** | ✅ **Поддерживается** | В E404 структуры KPM не поддерживаются; в Butterfly есть `set_memory.h` |
| **Re:Kernel** (`rekernel_enable`) | ✅ Поддерживается | ✅ Поддерживается | ✅ Поддерживается | Требует cgroup v2 freezer (присутствует во всех 3 ядрах) |
| **fgetpriority** (`fgetpriority_enable`) | ✅ Поддерживается | ✅ Поддерживается | ✅ Поддерживается | Скрытие вызова `getpriority` от детекторов процессов |
| **VPNHide Next** (`vpnhide_enable`) | ✅ Поддерживается | ✅ Поддерживается | ✅ Поддерживается | Сокрытие VPN-интерфейса от приложений |
| **Baseband Guard (BBG)** (`bbg_enable`, `bbg_boot`) | ✅ Поддерживается | ✅ Поддерживается | ✅ Поддерживается | Защита модема + опциональный запрет перезаписи `boot` |
| **Droidspaces (LXC/Docker)** (`droidspaces_enable`) | ✅ Поддерживается | ✅ Поддерживается | ✅ Поддерживается | Пространства имён и cgroup для контейнеров |
| **RTL8812AU USB Wi-Fi** (`rtl8812au_enable`) | ✅ Поддерживается | ✅ Поддерживается | ✅ Поддерживается | Встроен в ядро (built-in 88XXau / Monitor Mode) |
| **Отключение LTO/CFI** (`disable_lto_cfi`) | ✅ Поддерживается | ✅ Поддерживается | ✅ Поддерживается | Отключает LTO_CLANG / LTO_GCC / CFI |
| **Компилятор / Toolchain** | **AOSP Clang** (20.0) | **LLVM/Clang** (22.1.3) | **GNU GCC** (aarch64-linux-gnu) | Butterfly Kernel собирается строго через GNU GCC |

---

**English**:
- This fork exclusively supports **Xiaomi Poco F3 (`alioth`)**. All other upstream device workflows were removed.
- **LineageOS (`sm8250`)**: supports branches `lineage-24.0`, `lineage-23.2`, `lineage-22.2`, and `lineage-21`, compiled with AOSP Clang (`lineage-20.0`).
- **E404 (`sm8250`)**: supports all 31 branches (`main`, `main-bpf`, `a17`, `staging`, `staging2`, `staging3`, `staging-bpf`, `staging-bpf2`, `personal`, `personal-test`, `bbrv3`, `blk-mq`, `bpf`, `calltrace`, `chg`, `chopchop`, `cib`, `cib-rewrite`, `exthm`, `gcc`, `gcc2`, `gcc3`, `hos-stuff`, `kcompressd`, `mglru`, `modpost`, `ntsync`, `pstore`, `sched`, `simple_thermal`, `zstd`), compiled with LLVM/Clang `22.1.3` (`LD=ld.lld LLVM=1 LLVM_IAS=1`) and packed with [kvsnr113/AnyKernel3](https://github.com/kvsnr113/AnyKernel3) (interactive ROM/DTB/battery installer in recovery). Does **not** support KPM.
- **Butterfly Kernel / Rezadinosaurus (`sm8250`)**: supports `lineage-latte` (for AOSP / CLO ROMs) and `lineage-mocca` (for MIUI / HyperOS ROMs), compiled with modern **GNU GCC** (`aarch64-linux-gnu`), defconfig `vendor/alioth_defconfig`, packed with AnyKernel3. Features built-in `CONFIG_NOMOUNT`, supports KPM, does **not** support SUSFS.
- Available in two workflows: **EN** ([`build-release.yml`](.github/workflows/build-release.yml)) and **RU** ([`build-release-ru.yml`](.github/workflows/build-release-ru.yml)), with interactive `workflow_dispatch` toggles.

**Русский**:
- Этот форк поддерживает только **Xiaomi Poco F3 (`alioth`)** — все остальные устройства из оригинального репозитория удалены.
- **LineageOS (`sm8250`)**: ветки `lineage-24.0`, `lineage-23.2`, `lineage-22.2`, `lineage-21`, сборка через AOSP Clang (`lineage-20.0`).
- **E404 (`sm8250`)**: поддерживаются все 31 ветка, сборка через LLVM/Clang `22.1.3` и упаковка через [kvsnr113/AnyKernel3](https://github.com/kvsnr113/AnyKernel3) (интерактивный выбор ROM, частот DTB и батареи в рекавери). **KPM не поддерживается**.
- **Butterfly Kernel / Rezadinosaurus (`sm8250`)**: ветки `lineage-latte` (для AOSP/CLO прошивок) и `lineage-mocca` (для MIUI/HyperOS прошивок), сборка через **GNU GCC** (`aarch64-linux-gnu`), дефконфиг `vendor/alioth_defconfig`, упаковка в AnyKernel3. **NoMount встроен в ядро**, поддерживается KPM, **SUSFS не поддерживается** (конфликт патча).
- Доступно всего **2 сценария**: на английском ([`build-release.yml`](.github/workflows/build-release.yml)) и русском ([`build-release-ru.yml`](.github/workflows/build-release-ru.yml)) языках с интерактивными параметрами при запуске.

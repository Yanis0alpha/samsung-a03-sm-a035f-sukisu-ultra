# samsung-a03-sm-a035f-sukisu-ultra
# Samsung Galaxy A03 (SM-A035F) — SukiSU Ultra Kernel

Custom Samsung Galaxy A03 kernel build with **SukiSU Ultra** support for **SM-A035F**  
SoC: **Unisoc T616**  
Base kernel: **4.14.199**  
Android: **13**

## Current status

- ✅ Kernel boots
- ✅ `su` works
- ✅ `ksud` works
- ✅ `su -c id` works
- ✅ Module installation works
- ✅ `kernel_umount` supported
- ✅ `su_compat` supported
- ⚠️ `selinux_hide` not supported on this kernel branch
- ⚠️ Experimental / WIP

## Versions

- Kernel root implementation: **SukiSU Ultra build 40798**
- Manager tested: **SukiSU Ultra Manager 40796**
- Branch used: **builtin**
- Base commit used for userspace compatibility: **b59aca0a**

## Device information

- Device: **Samsung Galaxy A03**
- Model: **SM-A035F**
- SoC: **Unisoc T616**
- Kernel version: **4.14.199**

## Important notes

This device expects the kernel image format:

- ✅ `Image`
- ❌ `Image.gz`

Using `Image.gz` directly in the repacked `boot.img` caused boot issues.

## Flashing

Samsung device flashing is done through **Odin**, not fastboot.

Typical workflow:

1. Extract stock `boot.img`
2. Unpack boot image
3. Replace stock kernel with compiled `Image`
4. Repack boot image
5. Convert to `boot.img.lz4`
6. Pack into `.tar`
7. Flash with **Odin** in **AP**

## Tested commands

```sh
su -c id
/data/adb/ksud debug version
/data/adb/ksud feature list

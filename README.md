# RetroMagic RP2350 MicroPython Custom Firmware Builder

[English](#english) | [中文说明](#chinese)

---

<a id="english"></a>
## 🚀 Overview

This repository provides an automated, industrial-grade daily build pipeline for **MicroPython** targeting **RP2350** boards. 

### 🔥 The Problem It Solves
When running official upstream MicroPython on RP2350 boards equipped with some special SPI/QSPI Flash chips (such as Zetta/澜智 PUYA/普冉 etc.), the default aggressive XIP/SSI clock configurations can cause bus faults, leading to hard locks or complete boot failure (device fails to enumerate on USB).

### ✨ Key Features
* **Auto-Sync with Upstream**: Automatically syncs with the official MicroPython master branch daily via GitHub Actions.
* **Hardened Flash Stability**: Forces ** 6-divider ** QSPI clock configuration (`PICO_FLASH_SPI_CLKDIV=6`) and enables `PICO_EMBED_XIP_SETUP=1` to ensure rock-solid boot compatibility across various Flash vendors.
* **Architecture Safety Check**: Automated bytecode family ID validation (`0xe48bff57` for ARM Cortex-M33) embedded in the pipeline to prevent wrong builds.
* **Auto-Release**: Publishes pre-compiled `.uf2` binaries directly to GitHub Releases with commit hash tags.

---

## 📥 Download

Head over to the [Releases page](../../releases) of this repository to download the latest compiled `RetroMagic_RP2350_*.uf2` firmware and flash it to your development board!

*(If you find this project helpful, feel free to give it a Star ⭐ or use this firmware directly to solve your Flash compatibility issues!)*

---

<a id="chinese"></a>
## 🚀 概述

本仓库提供针对 **RP2350** 硬件的 **MicroPython** 官方版本解决兼容性问题 修复非PICO2原厂开发板兼容性问题 自动和官方版本同步。

### 🔥 解决的痛点
在使用官方原版 MicroPython 运行于搭载某些特殊 SPI/QSPI Flash（如 Zetta/澜智 PUYA/普冉 等等）的 RP2350 板卡时，原版过激的 XIP/SSI 时钟和总线配置极易导致底层时序错乱，表现为**一刷就死机、甚至连 USB 端口都无法枚举**的变软砖现象。

### ✨ 核心特性
* **每日自动同步官方**：通过 GitHub Actions 定时巡检官方 MicroPython 主干更新，自动拉取最新源码编译。
* **硬核防变砖护甲**：强制 ** 6分频 ** QSPI 时钟 并启用安全引导，让RP2350系列MCU搭配各种Flash芯片 告别死锁。
* **双重架构安全校验**：流水线内嵌 UF2 固件 Family ID 自动化校验（ARM Cortex-M33 架构的 `0xe48bff57`），确保输出固件 100% 可用。
* **自动发布 Release**：编译成功后自动挂载到 GitHub Releases，对应不同容量FLASH版本，方便随时下载。

---

## 📥 快速下载 | Download

直接前往本仓库的 [Releases 页面](../../releases) 获取最新编译好的 `RetroMagic_RP2350_*.uf2` 固件刷入开发板即可！

---
*(如果你对这个项目感兴趣，欢迎点个 Star ⭐，或者在遇到 Flash 兼容性问题时直接取用此固件！)*

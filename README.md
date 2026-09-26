# RetroMagic RP2350A MicroPython Custom Firmware Builder

[English](#english) | [中文说明](#chinese)

---

<a id="english"></a>
## 🚀 Overview

This repository provides an automated, industrial-grade daily build pipeline for **MicroPython** targeting **RP2350A** boards. 

### 🔥 The Problem It Solves
When running official upstream MicroPython on RP2350 boards equipped with certain non-standard or domestic SPI/QSPI Flash chips (such as Zetta/澜智 ZD25Q32DEIGR), the default aggressive XIP/SSI clock configurations can cause bus faults, leading to hard locks or complete boot failure (device fails to enumerate on USB).

### ✨ Key Features
* **Auto-Sync with Upstream**: Automatically syncs with the official MicroPython master branch daily via GitHub Actions.
* **Hardened Flash Stability**: Forces **6-divider ($25\text{ MHz}$)** QSPI clock configuration (`PICO_FLASH_SPI_CLKDIV=6`) and enables `PICO_EMBED_XIP_SETUP=1` to ensure rock-solid boot compatibility across various Flash vendors.
* **Architecture Safety Check**: Automated bytecode family ID validation (`0xe48bff57` for ARM Cortex-M33) embedded in the pipeline to prevent wrong builds.
* **Auto-Release**: Publishes pre-compiled `.uf2` binaries directly to GitHub Releases with commit hash tags.

---

## 📥 Download

Head over to the [Releases page](../../releases) of this repository to download the latest compiled `RetroMagic_RP2350A_*.uf2` firmware and flash it to your development board!

*(If you find this project helpful, feel free to give it a Star ⭐ or use this firmware directly to solve your Flash compatibility issues!)*

---

<a id="chinese"></a>
## 🚀 概述

本仓库提供针对 **RP2350A** 硬件的 **MicroPython** 官方同步及工业级加固固件的自动化每日构建流水线。

### 🔥 解决的痛点
在使用官方原版 MicroPython 运行于搭载部分国产或非标 SPI/QSPI Flash（如 Zetta/澜智 ZD25Q32DEIGR 等等）的 RP2350 板卡时，原版过激的 XIP/SSI 时钟和总线配置极易导致底层时序错乱，表现为**一刷就死机、甚至连 USB 端口都无法枚举**的变软砖现象。

### ✨ 核心特性
* **每日自动同步官方**：通过 GitHub Actions 定时巡检官方 MicroPython 主干更新，自动拉取最新源码编译。
* **硬核防变砖护甲**：强制锁死 **6 分频 ($25\text{ MHz}$)** QSPI 时钟（`PICO_FLASH_SPI_CLKDIV=6`）并启用安全引导策略，完美兼容各类敏感 Flash 芯片，告别死锁。
* **双重架构安全校验**：流水线内嵌 UF2 固件 Family ID 自动化校验（ARM Cortex-M33 架构的 `0xe48bff57`），确保输出固件 100% 可用。
* **自动发布 Release**：编译成功后自动挂载到 GitHub Releases，带上对应的官方 Commit 标识，方便随时下载。

---

## 📥 快速下载 | Download

直接前往本仓库的 [Releases 页面](../../releases) 获取最新编译好的 `RetroMagic_RP2350A_*.uf2` 固件刷入开发板即可！

---
*(如果你对这个项目感兴趣，欢迎点个 Star ⭐，或者在遇到 Flash 兼容性问题时直接取用此固件！)*

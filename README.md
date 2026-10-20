# Btai-AR: Open-Source Optical Waveguide AR Smart Glasses (Btai 1)

> 🎬 **Highly Recommended: Watch the Video Demo First!**  
> [📺 Bilibili Video — Feature Demo & Introduction](Link available on LCEDA Open Source Homepage)  
> 🔗 The LCEDA homepage also features an [Open Source] smart glasses case from the same series.

## 📖 Project Overview

As tech giants like Meta, Alibaba, and Huawei rush into the smart glasses industry, this project guides you through **building a pair of optical waveguide AR glasses from scratch** that rivals commercial products — **Btai 1**.

Unlike most open-source personal projects featuring non-foldable designs, Btai 1 is engineered to match real-world eyewear standards:
- ✅ **Foldable Structure**
- ✅ **Metal Hinges** (Adjustable tension)
- ✅ **3D Printed Housing** (Customizable color schemes)
- ✅ **Weight: ~40g** (On par with leading commercial products)

> 📷 Note: All photos are raw smartphone shots, unedited and AI-free.

## 🌈 Core Technical Principles

### Optical Waveguide Display Chain
The lens itself does not emit light; it solely handles "transmission + image projection." The complete chain is as follows:
`Light Engine Imaging → Coupling into Lens → Total Internal Reflection (TIR) Propagation → Coupling Output to Eye`

- **Lens**: Zhuhai Mojie Tech Single-Green Resin Diffractive Optical Waveguide Lens
- **Light Engine**: Shanghai Xianyao Hummingbird Single-Green Light Engine JBD013 (MicroLED + Optical Lens)
- ⚠️ Note: Optical waveguides can only transmit specific fixed colors of light.

## 🔩 Hardware Selection

### Mechanical Components

| Component | Specification / Description | Notes |
| :--- | :--- | :--- |
| Nose Pads | Two options available; V2 uses the second type | ~¥3 |
| Hinges | Standard metal eyeglass hinges | ~¥3; superior to 3D-printed alternatives |
| Battery | 701438 Li-ion Battery (300mAh) | Magnetic detachable design; higher capacity than most market products |
| Buttons | Smartphone side buttons | Can also be custom 3D printed |
| Speakers | 1306 / 1508 | One per side; current open-source version uses 1306 |
| Camera | Sony IMX219 (8MP) | ~¥30 |
| Motor | 1906 X-axis Linear Motor | For haptic feedback |

### 🧠 Core Chipset Solution

| Chip | Manufacturer | Role | Description |
| :--- | :--- | :--- | :--- |
| **V821_WBX** | Allwinner | Main Controller | Designed specifically for smart glasses; mass production in 2025 |
| **KLM Series** | Samsung | eMMC Storage | 4GB minimum; universal package |
| **JL7016G8** | Jieli | Audio Co-processor | Professional headphone chip with robust open-source SDK support |

## 🏗️ Hardware Architecture & Design

### Schematic Highlights
- **Main Controller Peripherals**: Ceramic antenna, 40MHz crystal oscillator, differential microphone, 3 power rails (0.9V/1.5V/3.3V)
- **Camera Interface**: 2-Lane MIPI + 1 clock lane; requires length matching and impedance control
- **MicroLED Driver**: 3 power rails + 2.0V negative voltage drive
- **Audio Channel Switching**: Dual-chip solution (Allwinner + Jieli) integrated via dedicated channel selector chip
- **Power Management**: Supports boost-then-buck topology to resolve low-dropout reverse current issues

### PCB & FPC Design
- **Main Board**: 6-layer stacked PCB (2+4 stackup), connected via BTB connectors
- **STM32 Alternative Version**: STM32H750IBK6 variant provided for educational purposes
- **Temple Board**: 1.0mm thick 2-layer PCB, 6mm width, 0201 package components
- **FPC Cables**: Includes signal cable, optical waveguide cable, main power cable, touch module cable, etc.
- **V2.0 Monocular Version**: Optimized monocular optical waveguide cable; eligible for free prototyping

### 🖨️ 3D Enclosure Modeling
- Complex surface modeling accommodating hinges, light engine, camera, and other critical structures
- Right temple tail houses the battery compartment; left temple tail houses the mainboard
- Compatible with clip-on prescription lenses for myopia correction

## 💾 Firmware & Development

### Firmware Flashing
- **Allwinner V821**: Use ADB push or PhoenixSuit; hold download button while connecting to PC to enter download mode
- **Jieli JL7016G8**: Use Jieli toolchain and CodeBlocks for flashing

### SDK Resources
- 📚 [Allwinner V821 Development Tutorial](Allwinner Official Website)
- 📦 [Jieli JL701N Open-Source SDK](Jieli Official Website)

## 📱 Companion Android App

Developed using **Flutter**, currently optimized for Android platform.

### Feature Modules
- 🏠 **Home**: Device management, network provisioning, glasses info
- 📲 **Apps**: Launch/manage downloaded applications
- 🛒 **App Store**: Download mini-programs/software/AI agents to glasses
- 👤 **Profile**: Account management, developer onboarding, community posts

### On-Device Features
- Menu system, AI conversation, real-time translation, phone connectivity
- Mini-games, cultivation dashboard, and other extended applications

## ⚠️ FAQ

**Q: Can people with myopia wear these?**  
A: Yes. Uses the industry-standard clip-on prescription lens solution.

**Q: Are they comfortable for extended wear?**  
A: Weighing ~40g, they are acceptable for regular glasses wearers; non-wearers may need an adjustment period.

## 📂 Project Files Inventory

### PCB Files
- AR1_FPCV1.1, jbd_TestV1.0, Main_Power_FPC_1V1.1
- Left/Right Temple Boards, Left Temple Mainboard Top/Bottom Layers
- Battery Magnetic Protection Board, Touch/Button Flex Cables, etc.

### 3D Models
- Battery Compartment Cover, Slide Button, Frame Front/Rim
- Left/Right Temples & Covers, Temple Tail Battery Housing

### Firmware Attachments
- `v1.1_firmware_Btai1_glasses_JL7016G8_isd.fw`
- `v1.1_firmware_Btai1_glasses_v821l2-wxx__nor.img`

## ⚖️ Intellectual Property Disclaimer

This is an open-source hardware project. All related intellectual property rights belong to the creator. It is intended solely for learning, exchange, and research purposes. **Commercial use is strictly prohibited.** Do not use for commercial sales or any profit-driven activities.

> ⚠️ **Replication Notice**: Please independently verify circuit feasibility and suitability. Replication is at your own risk. The platform assumes no liability for any damages arising from circuit design issues in this open-source project.

---

🔗 **Project Repository**: https://github.com/kemomi/Btai-AR

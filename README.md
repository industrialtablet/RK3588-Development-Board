# RK3588-Documents
This repository is the documentation for RK3588 products, written by RSD Team of HYY Technology Co.,Ltd.

# RK3588 Mainboard (SBC)
RK3588 Mainboard is a series of Rockchip RK3588 based SBC(Single Board Computer) by HYY. It can run Linux <Debian11, Ubuntu20.04>, Android12,  chromium-os and other distributions.
- [RK3588 Mainboard (SBC)](SBC.md)
- [RK3588 SBC Firmware Upgrade](RK3588_Update_Firmware.md)
# RK3588 mini-pc
- [RK3588 mini-pc](mini-pc.md)
- [RK3588 mini-pc Firmware Upgrade](RK3588_Update_Firmware.md)
# RK3588 Block Diagram
![RK3588 Block Diagram](imgs/RK3588-Block-Diagram.png?raw=true)

# RK3588 Specifications(Addtional details)
- CPU – 4x Cortex-A76 @ up to 2.4/2.6 GHz and 4x Cortex-A55 cores @ 1.8 GHz in dynamIQ configuration
- GPU
    - Arm Mali-G610 MP4 “Odin” GPU with support for OpenGLES 1.1, 2.0, and 3.2, OpenCL up to 2.2 and Vulkan1.2
    - 2D graphics engine up to 8192×8192 source, 4096×4096 destination
- AI Accelerator – 6 TOPS NPU 3.0 (Neural Processing Unit)
- VPU
    - Video decoding
        - 8Kp60 H.265, VP9, AVS2, 8Kp30 H.264 AVC/MVC
        - 4Kp60 AV1
        - 1080p60 MPEG-2/-1, VC-1, VP8
    - Real-time 8Kp30 encoding with H.265/H.264; multi-channel encoding supported at lower resolutions
- Memory I/F – LPDDR4/LPDDR4x/LPDDR5 up to 32GB
- Storage – eMMC 5.1, SD/MMC, SATA 3.0 (multiplexed with PCIe 2.0), FSPI (Flexible SPI)
- Video Output
    - Dual HDMI 2.1 / eDP 1.3 up to 8Kp60
    - Dual DisplayPort 1.4a up to 8Kp30 (multiplexed with USB 3.0)
    - Dual MIPI DSI output up to 4Kp60
    - Bt.1120 video output up to 1080p60
    - Optional dual LVDS up to 1080p60 via RK628 chip.
    - Up to four independent displays (up to 1x 8Kp60, 2x 4Kp60, 1x 1080p60)
- Video Input/Camera
    - 48MP (2x 24MP) ISP with HDR and 3D NR support; multi-camera input
    - 2x MIPI DC (4-lane DPHY v2.0 or 3-lane CPHY V1.1)
    - 4x 2-lane MIPI CSI
    - DVP camera interface
    - HDMI Rx 2.0 interface up to 4Kp60 with HDCP 2.3 support
- Audio
    - 2x 8-channel I2S, 2x 2-channel I2S
    - 2x SPDIF
    - 2x 8-channel PDM (for mic arrays)
    - 2-channel digital audio codec (16-bit DAC)
    - VAD engine
- Networking – Dual Gigabit Ethernet
- USB – 2x USB 3.1 Gen 1 up to 5 Gbps (multiplexed with DisplayPort), 1x USB 3.1 Gen 1 (multiplexed with Combo “PIPE PHY2”), 2x USB 2.0 OTG
- PCIe – PCIe 3.0 up to 8 Gbps (1x 4-lane, or 2x 2-lane, or 4x 1-lane, or 1x 2-lane + 2x 1-lane
- 3x Combo PIPE PHY interfaces
    - Combo PIPE PHY0/1 – SATA III or PCIe2.1 up to 5 Gbps
    - Combo PIPE PHY2  – SATA III, PCIe 2.1, or USB 3.0
- Low-speed I/O – 5x SPI, 9x I2C, 10x UART, GPIOs, 12-bit ADC (SARADC)
- Package – FCBGA1088L; 21.45 x 21.45mm
- Manufacturing process – 8nm LP
# Common Documents
- [01 HYY Rockchip RK3588 Datasheet.pdf](./RK3588_Documents/01_HYY_Rockchip_RK3588_Datasheet.pdf?raw=true)
- [02 HYY Rockchip RK806 Datasheet.pdf](./RK3588_Documents/02_HYY_Rockchip_RK806_Datasheet.pdf?raw=true)
- [03 HYY Rockchip RK3588 RKDevTool manual.pdf](./RK3588_Documents/03_HYY_RKDevTool_manual.pdf?raw=true)
- [04 HYY Rockchip RK3588 SBC Specifications.pdf](./RK3588_Documents/04_HYY_RK3588_SBC_Specifications.pdf?raw=true)
- [05 HYY Rockchip RK3588 8K Mini PC Specifications.pdf](./05_HYY_Rockchip_RK3588_8K_Mini_PC_Specifications?raw=true)
- [06 HYY Rockchip RK3588 8K industrial computer Specifications.pdf](./06_HYY_RK3588_8K_industrial_computer_specs?raw=true)
- [07 HYY Digital Signage Catalog.pdf](./RK3588_Documents/06_HYY_Digital_Signage_Catalog.pdf?raw=true)
# Firmware upgrade tools and driver
- [AndroidTool_Release_v2.35](./AndroidTool/AndroidTool_Release_v2.35.zip)
- [AndroidTool_Release_v2.54](./AndroidTool/AndroidTool_Release_v2.54.zip)
- [DriverAssitant_v5.1.1](./AndroidTool/DriverAssitant_v5.1.1.zip)
# Contacts
- Website: www.we-signage.com
- https://we-signage.en.made-in-china.com/
- E-mail: dennis@we-signage.com
- MP/Whatsapp/Wechat: + 86 13349909990
- Skype: solled686

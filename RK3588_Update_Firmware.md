# 1. Boot mode description

## 1.1. Preface

The RK3588 is installed with the Android operating system by default. If users want to run other operating systems, they need to use the corresponding firmware to program to the mainboard.

RK3588 has a flexible startup mode. Generally, the RK3588 SBC will not turn brick unless the hardware is damaged.

If the accident appeared in the process of upgrading, bootloader damage, leading to unable to upgrade again, while still can enter mode to Maskrom repair.

## 1.2. How to get the Firmwares and tools

* For all firmware and tools in this document, please send Email for download link : dennis@we-signage.com

## 1.3. Upgrade method

RK3588 supports firmware update through the following methods:

* Update firmware using USB cable
  Use the USB cable to connect the mainboard to the computer, and use the upgrade tool to program the firmware to the mainboard.

## 1.4. Boot media

* eMMC interface
* SDMMC interface

In addition, RK3588 supports downloading system codes from the Type-C data cable interface.

## 1.5. Boot mode

RK3588 has three startup modes:

* Normal mode
* Loader mode
* MaskRom mode

### 1.5.1. Normal mode

Normal mode is the Normal startup process. Each component loads in turn and enters the system normally.

### 1.5.2. Loader mode

In Loader mode, the bootloader will enter the upgrade state, waiting for the host command for firmware upgrade, etc. To enter the Loader mode, the bootloader must detect that the key has been pressed and the USB is connected.

The method to put the device into upgrade mode is as follows:

One way is to disconnect the power adapter

* Type-C data cable connects the device and the host.
* Press and hold the RECOVERY button on the device and hold it.
* Plug in the power
* After about two seconds, release the RECOVERY key.

Another way is to connect the power adapter

* The Type-C data cable connects the device and the host.
* Press and hold the RECOVERY button on the device and hold it.
* Briefly press the RESET button.
* After about two seconds, release the RECOVERY key.

# 2. Upgrade the firmware via USB cable

## 2.1. Introduction

This article describes how to upgrade the firmware file on the host to the flash memory of the development board through the Type-C data cable. When upgrading, you need to choose the appropriate upgrade mode according to the host operating system and firmware type.

## 2.2. Preparatory Tools

* RK3588 development board
* Firmware
* host computer
* Type-C data cable

There are two types of firmware files:

* A single unified firmware
  The unified firmware is a single file packaged and merged by all files such as the partition table, bootloader, uboot, kernel, system and so on. The firmware officially released by our  a unified firmware format. Upgrading the unified firmware will update the data and partition table of all partitions on the motherboard, and erase all data on the motherboard.
* Multiple partition images
  That is, files with independent functions, such as partition table, bootloader, and kernel, are generated during the development phase. The independent partition image can only update the specified partition, while keeping other partition data from being destroyed, it will be very convenient to debug during the development process.
* Through the unified firmware unpacking / packing tool, the unified firmware can be unpacked into multiple partition images, or multiple partition images can be merged into a unified firmware.

## 2.3. Windows

* Tool: **Androidtool_xxx (version number)**
* Driver:**DriverAssitant_vxxx(version number)**

### 2.3.1. Install RK USB drive

Download Release_DriverAssistant.zip, extract, and then run the DriverInstall.exe inside . In order for all devices to use the updated driver, first select Driver install (驱动安装)，If you need to uninstall the driver, please click Driver Uninstall（驱动卸载）

![](https://wiki.t-firefly.com/en/Core-3588J/_images/upgrade_firmware_install_RK_USB.png)

### 2.3.2. Connected devices

we can put the device into upgrade mode by hardware as follows:

* Disconnect the power adapter first.
* Type-C data cable connects one end to the host and the other end to the development board.
* Then connect the device Type-C to PC USB,and also connect the DC Power 12V to the device.
* And press amd hold the recover button nearby the USB3.0 port; And then press one time the reset button nearby the USB2.0 port; and then you can see the message"found a LOADER device"

![OTG](https://github.com/pengyixing/RK3588-Development-Board/blob/main/imgs/RK3588_recover_button_reset_button_otg-interface.jpg)

put the device into upgrade mode by software as follows.

Type-C data cable is connected, use the command in the serial debugging terminal or adb shell : reboot loader

The host should prompt for new hardware and configure the driver. Open Device manager and you will see the new Device  appear as shown below. If not, you need to go back to the previous step and **reinstall the driver.**

![](https://github.com/pengyixing/RK3588-Development-Board/blob/main/imgs/Rockusb_Device.png)

### 2.3.3. Upgrade the firmware

First you need to download the firmware . AndroidTool defaults to display in Chinese. We need to change it to English. Open  with an text editor (like notepad). The starting lines are:

```
#Language Selection: Selected=1(Chinese); Selected=2(English)
[Language]
Kinds=2
Selected=1
LangPath=Language\
```

Change to, and save. From now on, AndroidTool will display in English.Now, run AndroidTool.exe: (Note: If using Windows 7/8, you’ll need to right click it, select to run it as Administrator)

![Found_one_loader_device](https://github.com/pengyixing/RK3588-Development-Board/blob/main/imgs/Found_one_loader_device.png)

#### 2.3.3.1. Upgrade unified firmware - update.img

The steps to update the unified firmware are as follows:

1. Switch to the “upgrade firmware” page.
2. Press the “firmware” button to open the firmware file to be upgraded. The upgrade tool displays detailed firmware information.
3. Press the “upgrade” button to start the upgrade.
4. If the upgrade fails, you can try to erase the Flash by pressing the EraseFlash button first, and then upgrade.

**Note: if the firmware loadder you wrote is inconsistent with the original one, please execute before upgrading the firmware.**

![Download_Image](https://github.com/pengyixing/RK3588-Development-Board/blob/main/imgs/Download_Image.jpg)

#### 2.3.3.2. Upgrade Partition image

The steps to upgrade the partition image are as follows:

1. Switch to the “download image” page.
2. Check the partition to be burned, and select multiple.
3. Make sure the path of the image file is correct. If necessary, click the blank table cell on the right side of the path to select it again.
4. Click “Run” button to start the upgrade, and the device will restart automatically after the upgrade.

## 2.4. Linux

There is no need to install device driver under Linux. Please refer to the Windows section to connect the device.

* Tool : **upgrade_tool_xxx (version number)**
* Tool : **[Linux_adb_fastboot]**

### 2.4.1. Upgrade_tool

Download Linux_Upgrade_Tool, And install it into the system as follows for easy invocation:

```
unzip Linux_Upgrade_Tool_xxxx.zip
cd Linux_UpgradeTool_xxxx
sudo mv upgrade_tool /usr/local/bin
sudo chown root:root /usr/local/bin/upgrade_tool
sudo chmod a+x /usr/local/bin/upgrade_tool
```

### 2.4.2. Upgrade unified firmware -  *update.img* ：

```
sudo upgrade_tool uf update.img
```

If the upgrade fails, try erasing before upgrading.

```
# erase flash : Using the ef parameter requires the loader file or the corresponding update.img to be specified.
# update.img :The ubuntu firmware you need to upgrade.
sudo upgrade_tool ef update.img
# upgrade again
sudo upgrade_tool uf update.img
```

**pgrade Partition image**

```
sudo upgrade_tool di -b /path/to/boot.img
sudo upgrade_tool di -r /path/to/recovery.img
sudo upgrade_tool di -m /path/to/misc.img
sudo upgrade_tool di -u /path/to/uboot.img
sudo upgrade_tool di -dtbo /path/to/dtbo.img
sudo upgrade_tool di -p paramater   #upgrade parameter
sudo upgrade_tool ul bootloader.bin #upgrade bootloader
```

If the upgrade fails due to flash problems, you can try low-level formatting and erase nand flash:

```
sudo upgrade_tool lf update.img	# low-level formatting
sudo upgrade_tool ef update.img	# erase
```

### 2.4.3. fastboot

Download [Linux_adb_fastboot], And according to the following method to install into the system, easy to call：

```
sudo mv adb /usr/local/bin
sudo chown root:root /usr/local/bin/adb
sudo chmod a+x /usr/local/bin/adb
```

```
sudo mv fastboot /usr/local/bin
sudo chown root:root /usr/local/bin/fastboot
sudo chmod a+x /usr/local/bin/fastboot
```

**fastboot Burn dynamic partitions**

```
adb reboot fastboot # enter bootloader
sudo fastboot flash vendor vendor.img
sudo fastboot flash system system.img
sudo fastboot reboot # After the burn is successful, restart
```

## 2.5. FAQs

### 2.5.1 Analysis of programming failure

If Download Boot Fail occurs during the programming process, or an error occurs during the programming process, as shown in the figure below, it is usually caused by the poor connection of the USB cable, the inferior cable, or the insufficient drive capability of the USB port of the computer. Troubleshoot the computer USB port.

# Common Documents
- [01 HYY Rockchip RK3588 Datasheet.pdf](./RK3588_Documents/01_HYY_Rockchip_RK3588_Datasheet.pdf?raw=true)
- [02 HYY Rockchip RK806 Datasheet.pdf](./RK3588_Documents/02_HYY_Rockchip_RK806_Datasheet.pdf?raw=true)
- [03 HYY Rockchip RK3588 RKDevTool manual.pdf](./RK3588_Documents/03_HYY_RKDevTool_manual.pdf?raw=true)
- [04 HYY Rockchip RK3588 SBC Specifications.pdf](./RK3588_Documents/04_HYY_RK3588_SBC_Specifications.pdf?raw=true)
- [05 HYY Rockchip RK3588 8K Mini PC Specifications.pdf](./RK3588_Documents/05_HYY_RK3588_8K_Mini_PC_specs.pdf?raw=true)
- [06 HYY Digital Signage Catalog.pdf](./RK3588_Documents/06_HYY_Digital_Signage_Catalog.pdf?raw=true)

# Contacts

- Website: www.we-signage.com
- https://we-signage.en.made-in-china.com/
- E-mail: dennis@we-signage.com
- MP/Whatsapp/Wechat: + 86 13349909990
- Skype: solled686

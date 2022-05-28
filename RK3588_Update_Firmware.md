# 1. Boot mode description

## 1.1. Preface

The RK3588 is installed with the Android operating system by default. If users want to run other operating systems, they need to use the corresponding firmware to program to the mainboard.

RK3588 has a flexible startup mode. Generally, theRK3588development board will not turn brick unless the hardware is damaged.

If the accident appeared in the process of upgrading, bootloader damage, leading to unable to upgrade again, while still can enter `<span class="pre">MaskRom</span>` mode to repair.

## 1.2. How to get the Firmwares

* [Firmware download link](https://en.t-firefly.com/doc/download/140.html)

## 1.3. Upgrade method

RK3588 supports firmware update through the following two methods:

* Update firmware using USB cable
  Use the USB cable to connect the mainboard to the computer, and use the upgrade tool to program the firmware to the mainboard.
* Use MicroSD card.
  Use the upgrade card creation tool to make the MicroSD card as an upgrade card, insert the upgrade card into the mainboard, power on, and the machine will automatically perform the upgrade.

## 1.4. boot media

* eMMC interface
* SDMMC interface

In addition, RK3588supports downloading system codes from the Type-C data cable interface.

## 1.5. Boot mode

RK3588 has three startup modes:

* Normal mode
* Loader mode
* MaskRom mode

### 1.5.1. Normal mode

Normal mode is the Normal startup process. Each component loads in turn and enters the system normally. 

### 1.5.2. Loader mode

In Loader mode, the bootloader will enter the upgrade state, waiting for the host command for firmware upgrade, etc. To enter the Loader mode, the bootloader must detect that the `<span class="pre">RECOVERY</span>` key has been pressed and the USB is connected.

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

The RECOVERY button and RESET button are shown below:

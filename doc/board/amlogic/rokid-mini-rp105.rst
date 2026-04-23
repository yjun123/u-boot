.. SPDX-License-Identifier: GPL-2.0+

U-Boot for Rokid Mini RP105 (A113X)
===================================

Rokid Mini RP105 is a smart speaker (voice remote control) by Rokid
(Lingban), featuring the following specifications:
 - Amlogic A113X (ARM Cortex-A53) quad-core up to 1.5GHz
 - No video output interface
 - 256 MB DDR3 RAM
 - 512 MB NAND Flash
 - 1 x USB Type-C port(USB 2.0)
 - WiFi / Bluetooth: AMPAK AP6212 (Broadcom BCM43430A1),supporting
   IEEE 802.11b/g/n, Bluetooth 4.0
 - 12-channel circular RGB LED plus a central RGB LED
 - 8 capacitive touch zones
 - 4-microphone array
 - Built-in single speaker
 - 3.5mm line-out interface

U-Boot Compilation
------------------

.. code-block:: bash

    $ export CROSS_COMPILE=aarch64-none-elf-
    $ make rokid_mini_rp105_defconfig
    $ make

U-Boot Signing with Pre-Built FIP repo
--------------------------------------

.. code-block:: bash

    $ git clone https://github.com/LibreELEC/amlogic-boot-fip --depth=1
    $ cd amlogic-boot-fip
    $ mkdir my-output-dir
    $ ./build-fip.sh rokid-mini-rp105 /path/to/u-boot/u-boot.bin my-output-dir

The device has no eMMC support and no SD card interface. 
It can be flashed to NAND and booted via aml-update.

.. code-block:: bash

    $ DEV=/dev/boot_device
    $ aml-update partition bootloader fip/u-boot.bin

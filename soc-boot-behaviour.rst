Embedded SoC Boot from eMMC/SD behaviour rollup
===============================================

This page is a rollup of various SoCs boot behaviour. Many SoCs can load firmware from an SD, eMMC, or USB storage device, but the behaviour may be hard coded in masked ROM and be incompatible with standard MBR or GUID partitioning, requiring special care if the storage is used to load both firmware and the target OS.

Raspberry Pi
------------

Masked ROM looks for first MBR partition formatted as FAT and loads ``bootcode.bin``. ``bootcode.bin`` loads and runs ``start.elf``, which in turn loads ``config.txt``, ``cmdline.txt``, and an executable (defaults to ``kernel*.img``).

Supposedly newer Raspberry Pis can handle GUID Partition Tables, but haven't found any information as to which.

https://github.com/raspberrypi/noobs/wiki/Standalone-partitioning-explained

Dragonboard (db410)
-------------------

GUID Partition Table with firmware loaded from specific partitions: ``hyp``, ``rpm``, ``sbl1``, ``tz``, ``aboot``, and ``cdt``.

HiKey
-----
GUID Partition Table on eMMC. Native partitioning on UFS. Firmware loaded from specific partitions: ``xloader``, ``fastboot``, ``nvme``, ``fw_lpm3``, ``trustfirmware``.

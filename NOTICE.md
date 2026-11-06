# Notice: third-party material

badge27 is not affiliated with, or endorsed by, OpenEPaperLink, Solum, Nordic Semiconductor or Arm.
"Solum" and "Nordic" are named only to say which hardware the project works with.

## OpenEPaperLink (CC BY-NC-SA 4.0)

Parts of this project are based on information from the OpenEPaperLink project
(https://github.com/OpenEPaperLink/OpenEPaperLink; firmware for nRF52811 tags: Tag_FW_nRF52811),
licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International license
(https://creativecommons.org/licenses/by-nc-sa/4.0/). The full text is in the file LICENSE.

Derived from OpenEPaperLink: the pin assignments of the Newton M3 tag, the command sequence used to
initialise the 2.7" e-paper controller, the layout of the factory data (UICR) of the tag, and the table of
tag type codes shown by the control page.

Changed: the firmware was written anew for a different architecture (Nordic SoftDevice, Bluetooth upload of
slides from a phone, slides stored in the external flash). Pin assignments and the behaviour of the buttons,
LEDs and external flash were checked by measurements on real tags.

Because of the NonCommercial and ShareAlike terms, the firmware file and the control page in this repository
may be used and shared only for non-commercial purposes and only under the same license, with credit to
the authors above.

## What the firmware file contains

The firmware file (application and SoftDevice, ready to flash) contains:

1. The application code. It is modified from the Nordic nRF5 SDK example ble_app_uart and uses hardware data
   derived from OpenEPaperLink (see above).
2. Source files of the Nordic nRF5 SDK 17.1.0 (BLE services and helpers, timers, clocks, power management, board
   support and system files). Most of them are under the nRF5 SDK license (5 clauses, text in
   licenses/Nordic-5-clause.txt); each file states its license in its header.
3. The Nordic SoftDevice S112 7.2.0, as an unmodified binary, under the SoftDevice license of Nordic (the same
   5-clause text, licenses/Nordic-5-clause.txt). The build only merges it with the application.
4. The start-up file gcc_startup_nrf52811.S and the CMSIS core header core_cm4.h:
   Copyright (c) 2009-2020 Arm Limited, Apache License 2.0 (licenses/Apache-2.0.txt); the start-up file was
   modified by Nordic Semiconductor ASA.
5. Functions of the C library newlib-nano (memcpy, memmove, memset, memcmp, strlen, strncmp, exit, atexit) and
   libnosys (_exit), and the GCC start-up objects (crt0, crtbegin, crti, crtn, crtend). newlib is under
   BSD-style licenses of its authors; the GCC objects come with the GCC Runtime Library Exception.

No code from the "external" folder of the nRF5 SDK (SEGGER RTT and similar) and no Garmin files are in the
firmware. This list was taken from the linker map of the build.

The software with the Nordic license must only be used with a Nordic Semiconductor ASA integrated circuit;
the binaries of Nordic must not be reverse engineered, decompiled, modified or disassembled; the name of Nordic
may not be used to endorse products derived from it.

## Source code

The firmware source code is not published. The SDK and the SoftDevice are not part of this repository.

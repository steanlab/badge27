# Notice: third-party material

badge27 is not affiliated with, or endorsed by, OpenEPaperLink, Solum or Nordic Semiconductor.
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

## Nordic Semiconductor (SoftDevice S112 7.2.0, nRF5 SDK 17.1.0)

Copyright (c) 2007 - 2021, Nordic Semiconductor ASA. All rights reserved.
The firmware file contains the unmodified SoftDevice S112 binary and code built with the nRF5 SDK, under the
5-clause Nordic license: the software must only be used with a Nordic Semiconductor ASA integrated circuit;
binaries must not be reverse engineered, decompiled, modified or disassembled; the name of Nordic may not be
used to endorse products derived from it. The SDK and the SoftDevice are not part of this repository.
Parts of the SDK come under their own licenses (for example ARM CMSIS: BSD 3-clause), see
documentation/licenses.txt in the nRF5 SDK.

## Source code

The firmware source code is not published.

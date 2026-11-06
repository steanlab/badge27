# badge27

An e-ink name badge that you change from your phone. A Bluetooth control page and firmware files for the
Solum Newton M3 2.7" electronic shelf label (nRF52811, black / white / red).

**Control page:** https://steanlab.github.io/badge27/  (Chrome on Android or a computer; installable as an app, works offline after the first visit)

> **Status:** works on the tag listed below, not a finished product. Flashing needs an SWD programmer and
> soldering, and it replaces the original firmware of the tag. Use at your own risk, no warranty.

## What it does

- Keeps many slides (pictures of 200 x 300 px in black, white and red) in the external flash of the tag.
- Shows one slide at a time; the picture stays on the e-paper without power.
- Change slides with the two buttons, with a tap of a phone on the NFC area, automatically every N minutes,
  in order or at random.
- Upload and manage slides from the phone over Bluetooth with the control page (no app to install).
- Protection: the screen is not refreshed when the battery is low; a hardware watchdog restarts a stuck tag.

## Supported tags

| Tag | Chip | Panel | External flash | Status |
|---|---|---|---|---|
| Solum EL027H3WRA (2.7", Newton M3) | nRF52811 | 300 x 200 px, black/white/red | 512 KB | **tested** |
| Solum EL022F3WRA (2.2") | nRF52811 | 296 x 160 px | 1 MB | probed only, firmware not adapted |

No other tag is supported.

## What you need

- the tag with an unlocked debug port (some tags come locked: unlocking erases the factory data, see below),
- an SWD programmer (for example the Raspberry Pi Debug Probe, CMSIS-DAP) and [OpenOCD](https://openocd.org/),
- soldered wires to the SWD pads of the tag (SWDIO, SWCLK, GND, 3V3); the pads depend on the tag model,
- a phone with Chrome (Android) or a computer with Chrome or Edge. iPhone: Safari has no Web Bluetooth;
  a browser with Web Bluetooth such as Bluefy may work (not tested).

## Flashing

1. **Back up the tag first** (flash and the factory data in the UICR; do not skip this):
`openocd -f interface/cmsis-dap.cfg -f target/nrf52.cfg -c “adapter speed 1000” -c “init” -c “halt” -c “dump_image backup_flash.bin 0x0 0x30000” -c “dump_image backup_uicr.bin 0x10001000 0x1000” -c “shutdown”`
2. Download the latest `.hex` file from [Releases](../../releases) and check it against `SHA256SUMS.txt`.
3. Flash it:
`openocd -f interface/cmsis-dap.cfg -f target/nrf52.cfg -c “adapter speed 1000” -c “init” -c “halt” -c “program badge27-firmware-vX.Y.hex verify reset” -c “shutdown”`
Never use "mass erase": it also erases the factory data (UICR) of the tag.
4. After the start the LED flashes blue, then green once.

The original firmware is replaced. There is no over-the-air update: a new version is flashed the same way.

## Using the tag

| What | How |
|---|---|
| Next / previous slide | button 1 / button 2 (short press) |
| Open the upload window | hold button 2 for 1.5 s (blue flash, then a green pulse every 2 s) |
| Next slide by NFC | touch the tag with a phone (white flash); can be switched off on the page |
| Window closes | 2 minutes after it was opened, 30 s after the phone disconnects, or at once with "Finish" |

| LED | Meaning |
|---|---|
| green pulse | upload window open, waiting for the phone |
| blue steady | phone connected |
| red flash | slide changed by a button |
| white flash | slide changed by an NFC tap |
| 5 red flashes | battery low: the screen is not refreshed any more |
| 3 short red flashes | there are no slides |

## The control page

1. Hold button 2 of the tag for 1.5 s.
2. Open the page, press **Connect**, choose "Badge27".
3. Choose pictures and press **Upload**. A slide takes about 3 to 9 seconds to upload; a screen refresh takes about 25 seconds.
4. Other functions: show a slide, next / previous, order (in order or random), auto change, clear all slides,
   text slides "About" and "Hardware" (author, battery, chip, flash, panel), a calibration slide for the tone curve.

Pictures are converted in the browser (three inks, error diffusion). The slide format is compressed, so a tag with
512 KB of flash holds roughly 35 colour photos or about 60 black-and-white pictures.

## Limits

- One tag model; the picture size (200 x 300 px) is fixed.
- No over-the-air firmware update; battery life is not measured yet.
- NFC is used only to change slides; writing content into the NFC chip is not implemented.
- iPhone not tested.

## Credits and licenses

The control page, the documentation and the firmware file are shared under
[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/): non-commercial use, credit to the authors,
same license for derived work. The project builds on the work of the
[OpenEPaperLink](https://github.com/OpenEPaperLink/OpenEPaperLink) community. The firmware file contains the Nordic
SoftDevice under Nordic's license. Details: [NOTICE.md](NOTICE.md) and [LICENSE](LICENSE).

## Contact

Questions and requests (including consultations): open an issue in this repository.

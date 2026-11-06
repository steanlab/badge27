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

# VENTUNO Q — First Contact & Setup (living document)

All commands below are verbatim from `kb/evidence/2026-10-25-user-manual-official.txt` (official User Manual, rev. 2026-09-10) unless marked otherwise.

## Access paths to the board (MPU Linux shell)
1. **SBC mode** — monitor (HDMI/DSI) + USB keyboard/mouse + USB-C hub; terminal on-board.
2. **ADB over USB-C** — `sudo apt-get install android-sdk-platform-tools` on your PC, then `adb shell`.
3. **SSH** — board must be on the LAN first (via App Lab Wi-Fi config or `adb` + `sudo nmtui`); get IP with `hostname -I`; then `ssh arduino@<ip>`.
- Recommended order: finish App Lab first-configuration first (sets board password + Wi-Fi), then ADB/SSH.
- Default user: `arduino`. Password: chosen by YOU during First Setup (not vendor default).

## Our 3 units — inventory (fill in as boards arrive/are set up)
| Unit | Hostname/label | IP (LAN) | Firmware image date | Status |
|---|---|---|---|---|
| 1 | | | | not yet set up |
| 2 | | | | not yet set up |
| 3 | | | | not yet set up |

## First-setup checklist (per board)
- [ ] Power: USB-C 5V≤3A jack NOT required — included 65W PSU via barrel adapter works (evidence: manual L73)
- [ ] Complete Arduino App Lab First Setup (sets password + Wi-Fi)
- [ ] `hostname -I` → record IP in table above
- [ ] `sudo apt update && sudo apt upgrade -y`
- [ ] Note the preloaded image's build date (`cat /etc/arduino-release` or App Lab UI — NEEDS VALIDATION: exact path not yet confirmed)
- [ ] MCU side: `arduino-cli` or IDE 2.0+ flashing works (verify per-board)

## Useful one-liners from the manual
- CSI camera capture: `sudo apt install gstreamer1.0-plugins-qcom` then `gst-launch-1.0 ... qtiqmmfsrc camera=0 ...` (full pipelines in evidence, camera section)
- CAN bus: preloaded firmware handles CAN via the MCU — no user sketch needed; bring up with the ip-link commands in the CAN section of the evidence file
- User button: test via `gpiod` (line 469 of evidence)

## Corrections to marketing copy found in the manual
- CPU: "octa-core Kryo Gen 6 CPU subsystem (up to 2.35 GHz)" — earlier board-page capture said A623 @877 MHz (that number is the **GPU/VPU** clock, not CPU). Board page capture was less precise; manual is authoritative here.
- ISP: manual names both "Spectra 692" (cameras section) and "Spectra 690" (overview) — treat exact ISP SKU as NEEDS VALIDATION.

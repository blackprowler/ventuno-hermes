# VENTUNO Q — Board Reference (living document)

Sources (captured 2026-10-25): `kb/evidence/2026-10-25-board-page-official.txt` (docs.arduino.cc/hardware/ventuno-q), `kb/evidence/2026-10-25-store-page-official.txt` (store.arduino.cc product page). All facts below are backed by those captures.

## Identity
- Name: Arduino VENTUNO Q — "edge AI computer", UNO form factor, 160×100×25.8 mm
- SKU ABX00181, barcode 7630049205949
- Price at capture: €419,55 (VAT incl.), pre-order, free 65W USB-C PSU + cable promo
- We own 3 units (purchased 2026-10)

## Dual-Brain architecture
| Brain | Chip | Specs |
|---|---|---|
| AI (MPU) | Qualcomm Dragonwing IQ8 **QCS8275** | Octa-core Kryo Gen 6 (Cortex-A623 @877 MHz per cluster note on docs page — exact core split NEEDS VALIDATION), Adreno 623 GPU/VPU, Hexagon Tensor AI NPU up to **40 dense TOPS**, Spectra 692/690 ISP |
| Action (MCU) | ST **STM32H5F5** | Cortex-M33 @250 MHz, 4 MB flash, 1.5 MB RAM, FPU-class peripherals; runs **Arduino Core on Zephyr RTOS**, sub-ms deterministic control (motors, CAN-FD, PWM, GPIO) |

- MPU↔MCU communicate via built-in **RPC (Arduino Bridge)** library.
- MPU OS: **Ubuntu Linux** shipped (Debian support "coming soon" at capture — verify actual image on our units).

## Memory & storage
- 16 GB LPDDR5 (2×8 GB), 64 GB industrial eMMC
- M.2 slot for NVMe Gen.4 expansion
- Docker and apt preinstalled on the image

## Connectivity & I/O (from official spec table)
- Wi-Fi 6 (2.4/5/6 GHz) + Bluetooth 5.3, onboard antennas; 1× 2.5 GbE RJ45
- USB: 1× USB-C (host/device + power role switch + DP Alt Mode video), 2× USB 3.0 Type-A, 2× more USB 3.0 on JOMEGA
- Camera: USB camera + 3× MIPI-CSI onboard (muxed with 2× MIPI-CSI on JMEDIA)
- Video: HDMI muxed with MIPI-DSI (JMEDIA); DP Alt Mode via USB-C
- Audio: mic-in/headphone/line-out on JMISC header
- CAN: 1× CAN-FD PHY on screw terminal + 3× CAN-FD (no PHY) on JOMEGA + 1× on UNO shield headers
- Interfaces: I2C/I3C, SPI, PWM, UART, 4× RGB LEDs, 8×13 blue LED matrix, Qwiic (3V3/I2C), user + reset buttons, JTAG on JOMEGA, JCTL debug header

## Power
- USB-C 5 VDC ≤3 A; OR 5.5×2.1 mm jack 12–24 VDC; OR screw terminal 7–24 VDC (same range on JOMEGA)
- Commercial temp range: −10 °C to +60 °C

## Preloaded AI stack (App Lab)
- LLM/VLM: Qwen 3 4B; Qwen 2.5 7B & 3 4B VLM; Gemma 4 E2B/E4B
- Speech: Whisper ASR; Melo + Piper TTS
- Vision: YoloX-small detection, MediaPipe gesture/anomaly/kws
- Paths to models: ready library (AI Hub-optimized) · GGUF from HF/AI Hub via llama.cpp Brick · custom models via Edge Impulse
- 3 dev modes: standalone (monitor+kb+m), PC-connected (USB-C/network to App Lab on PC), headless-networked

## Production path
- Same IQ8 architecture available as certified SOMs from Dragonwing partners; App Lab software/models carry forward.

## Notes for us
- Marketing vs spec: "40 dense TOPS" and core details come from vendor copy; treat perf numbers as NEEDS VALIDATION on our units.
- Docs tutorials section listed "Tutorials (32)" on the board page — worth mining over time (community-watch style).
- UNO Q (€59.90 2GB / €82.90 4GB, QRB2210 + STM32U585) is the little sibling in `kb/evidence/2026-10-25-uno-q-board-page-official.txt` — different board, don't confuse.

# GLOSSARY — Ventuno Q

Any note introducing a new term adds it here first. Shaky definitions get a NEEDS VALIDATION flag inline.

| Term | Meaning | How we use it here |
|---|---|---|
| VENTUNO Q | Arduino's edge-AI dual-brain board: Qualcomm Dragonwing IQ8 (QCS8275) MPU + STM32H5F5 MCU, SKU ABX00181 | The board this whole repo is about |
| Dual-Brain / dual-architecture | One board pairing a Linux MPU ("AI brain") with an RTOS MCU ("action brain") | Core mental model for all experiments |
| MPU | Microprocessor (the Linux-side SoC, QCS8275) | "MPU-side" = Linux/Python/container work |
| MCU | Microcontroller (STM32H5F5, Cortex-M33 @250 MHz, runs Arduino Core on Zephyr RTOS) | "MCU-side" = sketches, real-time control |
| RPC bridge / Arduino Bridge | Built-in library connecting MPU ↔ MCU so a sketch and a Linux app talk as one app | How we cross the brain boundary without sockets-by-hand |
| Arduino App Lab | Arduino's new IDE/launcher uniting sketches + Python + AI models as "Apps"; preloaded on the board | Default dev workflow on the board |
| Brick | Pre-built plug-in feature/module in App Lab (e.g., llama.cpp Brick, Whisper ASR) | Building blocks for Apps |
| App | Self-contained self-contained example in App Lab (sketch + scripts + models) | Unit of runnable work on the board |
| QCS8275 / IQ8 | Qualcomm Dragonwing IQ8 octa-core Kryo Gen 6 SoC with Hexagon NPU (40 dense TOPS) | MPU silicon |
| Hexagon NPU / HTP | Qualcomm's AI accelerator on the SoC | Where quantized models actually run |
| Qualcomm AI Hub | Model zoo with IQ8-optimized models (Qwen, Gemma, Whisper, YoloX, MediaPipe…) | Source of ready models |
| Edge Impulse Studio | Studio to train/quantize custom models for the IQ8 NPU | Bring-your-own-model path |
| Zephyr RTOS | RTOS the MCU runs Arduino Core on | MCU runtime layer |
| Modulino / Qwiic | Arduino's plug-and-play sensor nodes / I2C connector ecosystem | Sensor expansion without soldering |
| JMEDIA / JMISC / JOMEGA / JCTL | The board's high-speed/expansion headers (camera/DSI; audio; misc+CAN+JTAG; remote debug) | Referenced by exact name in wiring notes |
| UNO Shield headers | Classic UNO-form-factor expansion headers on the board | Legacy shield compatibility |
| DP Alt Mode | DisplayPort-over-USB-C video output | HDMI/monitor path via USB-C |

---
layout: page
title: Custom Drone Project Log
permalink: /custom-drone/
---

#  Custom Quadcopter Drone with Modular PCB
**Status:** Stage 1 - Electronic Circuit Architecture

---

## Chronological Engineering Logs

###  Log 01: Schematic Mapping & Component Selection (Current)
* **Goal:** Establish a high-efficiency, dual-stage power delivery system capable of stepping down an 11.1V (3S LiPo) battery voltage to a pristine 3.3V rail, selecting a high-refresh-rate processor, and establishing low-noise sensor buses.
* **Component Milestones:** 
  * **Processing Core:** Selected the **STM32F405RGT6** ARM Cortex-M4 MCU. Its 168 MHz clock speed, hardware FPU, and rich DMA-backed SPI arrays make it highly optimized for fast PID flight control loop processing.
  * **Primary Power Stage:** Selected the **TPS62933** high-efficiency buck converter to efficiently step the high 11.1V battery voltage down to an intermediate 5.0V system rail.
  * **Secondary Power Stage:** Selected the **LT1962-3.3** ultra-low-noise, low-dropout (LDO) linear regulator. Fed by the 5V buck rail, it acts as a ripple filter to deliver an exceptionally clean 3.3V pool directly to the MCU's analog domains and sensitive tracking sensors.
  * **Telemetry Payload:** Replaced the older MPU6050 with the low-noise **BMI270 6-DoF IMU** for gyro/accel tracking, and the **BMP280 Barometer** for stable relative altitude hold tracking.
* **Engineering Hurdles:** Balancing trace widths and mitigating switching EMI. The traces routing raw battery power to the electronic speed controllers (ESCs) and drone motors must be significantly thicker (or built as broad polygon pours) to handle severe transient current loads without overheating. Simultaneously, the switching node of the TPS62933 buck converter must be heavily isolated from the LT1962 LDO and the telemetry sensors to prevent electrical noise from causing sensor drift.
* **Bus Architecture:** Upgraded from standard I²C to a high-speed **SPI bus** layout (e.g., `SPI1`). The BMI270 and BMP280 share the standard hardware SPI lines (`SCK`, `MISO`, `MOSI`) but utilize dedicated chip-select lines (`CS_IMU`, `CS_BARO`) driven by GPIO outputs. This minimizes communication overhead and avoids the bus-stalling vulnerabilities inherent to I²C blocks under heavy vibratory flight conditions.

###  Log 02: Footprint Planning & Multi-layer Strategy (Upcoming)
* **Goal:** Design the physical layer stack-up and map components to minimize electromagnetic interference (EMI) and cross-talk.
* **Strategy:** Implement a 4-layer PCB design. Dedicate Layer 1 to high-speed data signals and sensor placement, Layer 2 to a solid Ground (GND) Plane for return path shielding, Layer 3 to a Power Plane split for 5V and 3.3V power routing, and Layer 4 for heavy battery-to-motor power routing. Special focus will be given to minimizing the loop area of the TPS62933 switching circuit and placing 0.1µF decoupling capacitors immediately adjacent to every sensor VDD pin.

###  Log 03: Manufacturing, Soldering, & Power Validation (Upcoming)
* **Goal:** Assemble the bare prototype boards and conduct a stepped power-on validation test prior to micro-controller testing.
* **Strategy:** Solder the power tree (TPS62933 buck circuit first, followed by the LT1962 LDO) and test output voltages with a digital multimeter under a simulated dummy load. Verify that the 3.3V line remains rock-solid and free of high-frequency AC ripple on an oscilloscope before soldering the STM32F405 processor or surface-mount sensor ICs to eliminate the risk of over-voltage damage.

---

[ Back to Home Page](../)

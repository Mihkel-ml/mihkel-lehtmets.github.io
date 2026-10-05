---
layout: page
title: Custom Drone Project Log
permalink: /custom-drone/
---

#  Custom Quadcopter Drone with Modular PCB
**Status:** Stage 1 - Electronic Circuit Architecture 🛠_

---

## Chronological Engineering Logs

###  Log 01: Schematic Mapping & Component Selection (Current)
* **Goal:** Establish a baseline power delivery system capable of safely shifting 11.1V battery voltages down to 3.3V for the microprocessor.
* **Component Milestones:** Selected an ultra-low-dropout (LDO) voltage regulator to maintain a clean voltage pool for the flight processor. Mapped the pinout mapping for an MPU6050 IMU accelerometer chip over an $I^2C$ communication block.
* **Engineering Hurdles:** Balancing trace widths. The traces routing power to the drone motors must be significantly thicker than data lines to prevent the copper layout from overheating under heavy electrical load.

###  Log 02: Footprint Planning & Multi-layer Strategy (Upcoming)
* **

###  Log 03: Manufacturing, Soldering, & Power Validation (Upcoming)
* **

---

[ Back to Home Page](../)

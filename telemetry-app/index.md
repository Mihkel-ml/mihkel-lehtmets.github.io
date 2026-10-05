---
layout: page
title: Telemetry App Project Log
permalink: /telemetry-app/
---

#  Native Desktop Telemetry Dashboard
**Status:** Software Framework Incomplete_

This project is a native desktop application designed to communicate directly with my custom robotics and drone microprocessors over a physical USB interface.

##  Software Architecture
* **GUI Engine:** PyQt6 rendering a hardware-accelerated user canvas.
* **Graphing Subsystem:** PyQtGraph processing real-time array rolling datasets at 20 frames per second.
* **Data Transport:** PySerial managing bare-metal string streaming over custom desktop COM ports.

[ Back to Home Page](../)

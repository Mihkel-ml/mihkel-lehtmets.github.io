---
layout: page
title: Robotic Arm Project Log
permalink: /robotic-arm/
---

#  Multi-Axis Robotic Arm with Inverse Kinematics
**Status:** In Active Development 

This sub-page serves as the central engineering repository and build log for my 4-axis desktop robotic arm. The core objective of this project is to bridge spatial geometry with physical actuation.

---

##  Development Timeline & Logs

### Log 01: Kinematic Calculations & Framework Setup
* **Current Focus:** Drafting inverse kinematics (IK) scripts in C++.
* **Objective:** Instead of defining static servo degree coordinates, the MCU must map standard Cartesian $(X, Y, Z)$ spatial variables automatically into individual joint angles.
* **Next Steps:** Finalize the mathematical formulas and verify joint limits inside a test simulation before moving code onto physical hardware.

---

##  Project Architecture
* **Microcontroller Platform:** Arduino-compatible hardware environment
* **Actuation Matrix:** High-torque servo motor arrays
* **Mechanical Structure:** 3D Printed custom component enclosures

[ Back to Home Page](../)

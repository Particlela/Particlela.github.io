---
layout: archive
title: "Project"
permalink: /project/
author_profile: true
---

***

## **Oct 2024 - Present | RoboMaster Series-Elastic Leg Infantry Robot Control System**

<div style="text-align: center;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/Infantry.jpg" style="width: 80%; height: auto;" alt="Infantry Robot">
</div>

A full-stack embedded control system built on the STM32H7 platform for the RoboMaster series-elastic leg wheeled balancing infantry robot, based on a five-bar linkage leg mechanism and designed for high-dynamic locomotion requirements. At the core control layer, a **variable-gain LQR balance control strategy** is adopted, where a 10-state LQR controller is designed with its gain matrix and feedforward terms expressed as bivariate cubic polynomial functions of the left and right virtual leg lengths, enabling online real-time interpolation to ensure stable balancing across varying leg configurations. At the decision and behavior scheduling level, the system runs a **priority-based hierarchical state machine** covering multiple working states including Dead, Recovery, Mature, Flight, Jump, Onestep, Twostep, and Creep modes, supporting the orderly switching and execution of complex maneuvers such as obstacle jumping and single/double-step climbing. In terms of energy, the system integrates a supercapacitor and a buffer capacitor to form a two-stage energy buffer, and introduces a **quadratic-model-based power limiter** that dynamically scales velocity and yaw-axis angular velocity commands based on the real-time power limit from the referee system and remaining energy status, balancing maneuverability and system safety within limited power budget, ultimately forming a complete robot control loop integrating balance control, behavior management, and energy scheduling.

<video width="100%" controls muted>
  <source src="{{ site.url }}{{ site.baseurl }}/videos/InfantryJumpSlope.mp4" type="video/mp4">
</video>

<div style="clear: both;"></div>

***

## **Aug 2025 - Present | Series-Elastic Leg Sentry Robot Control System**

![Sentry Robot]({{ site.url }}{{ site.baseurl }}/images/Sentry.jpg)

Built upon the infantry balancing robot framework, the system is further upgraded to an autonomous navigation-oriented sentry robot, sharing the same series-elastic leg hardware platform and low-level control architecture, but shifting the control focus from manual operation to autonomous decision-making and high-level battlefield maneuvering. To achieve unmanned operation, the system adds a **chassis navigation command interface** for receiving motion reference commands from the upper-level NUC, enabling the sentry to completely eliminate dependence on remote control or keyboard/mouse input and independently execute navigation tasks. The sentry robot not only inherits the infantry's high-dynamic balancing capability but also possesses complete intelligence for autonomous planning and execution of complex maneuvers in unknown environments.

<video width="100%" controls>
  <source src="{{ site.url }}{{ site.baseurl }}/videos/Sentry.mp4" type="video/mp4">
</video>

<div style="clear: both;"></div>

***

## **June 2026 - Present | Bidirectional Four-Switch Buck-Boost Buffer Capacitor Control System (FSBB)**

<div style="display: flex; justify-content: center; gap: 2%; margin: 1em 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/buffercap1.png" style="width: 39%; height: auto;" alt="Buffer Capacitor Control">
  <img src="{{ site.url }}{{ site.baseurl }}/images/buffercap2.png" style="width: 39%; height: auto;" alt="Buffer Capacitor Hardware">
</div>

Based on the STM32G4 MCU, this system designs and implements a high-bandwidth buffer-capacitor energy management controller for RoboMaster mobile robots. The main power stage adopts a bidirectional four-switch Buck-Boost converter topology, capable of dynamically absorbing and releasing energy to effectively suppress instantaneous bus voltage drops during high-dynamic maneuvers. At the control level, the system runs a **state-machine-based multi-loop control strategy**, integrating voltage-ratio feedforward compensation with three independent PI loops—namely the constant-power charging loop, capacitor voltage regulation loop, and bus voltage support loop—enabling the controller to smoothly switch between charging, voltage regulation, and discharging modes based on bus conditions. Meanwhile, multi-channel ADC and DMA are used for high-speed acquisition of input voltage, capacitor voltage, input current, output current, and capacitor current, with precision calibration and complementary filtering to provide high-accuracy, low-latency real-time state feedback for each closed loop. In terms of safety mechanisms, the system integrates power ramp-up, over-voltage/under-voltage/over-current threshold protection, and automatic shutdown/recovery logic on CAN communication timeout or abnormal operating conditions, ensuring reliable hardware operation in complex electrical environments. The achieved key performance specifications are: capacitor voltage operating range 11 V–28 V, maximum charging power 190 W, maximum output/supplement power 1200 W, capacitor current limit 70 A, input voltage range 15 V–28 V, fully meeting the stringent requirements for instantaneous power compensation in highly maneuverable robots.

<div style="clear: both;"></div>

***

## **Oct 2024 - Present | HW-Components: Universal Robot Control Library**

As a core contributor, I architected and maintained the embedded communication layer of HW-Components, a reusable robot control library targeting RoboMaster and general mobile robotic platforms.

- **Multi-Protocol Ranging Sensor Communication**: Implemented unidirectional and bidirectional data exchange between the STM32 MCU and various ranging modules (ultrasonic, ToF, infrared, etc.), providing flexible perception interfaces for different robotic configurations.
- **Referee System Serial Link**: Maintained and optimized the UART-based communication protocol with the RoboMaster referee system, ensuring reliable reception of match-critical data such as robot status, hit points, firing permissions, and power limits.
- **Energy Management over CAN**: Developed bidirectional CAN communication with the supercapacitor and buffer-capacitor subsystems, enabling real-time power monitoring, energy buffering control, and dynamic power allocation.
- **Lever-Arm Compensation**: Implemented lever-arm compensation to correct kinematic errors caused by the physical offset between the IMU mounting position and the robot's center of rotation, improving state-estimation accuracy during rapid attitude changes.

<div style="clear: both;"></div>

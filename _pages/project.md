---
layout: archive
title: "Project"
permalink: /project/
author_profile: true
---

***

## **Oct 2024 - Present | RoboMaster Series-Elastic Leg Infantry Robot Control System**

![Infantry Robot]({{ site.url }}{{ site.baseurl }}/images/Infantry.jpg)

Developed the full-stack embedded control system for a series-elastic leg wheeled balancing infantry robot based on the STM32H7 platform. The robot uses a five-bar linkage leg mechanism and is designed for high-dynamic locomotion in the RoboMaster competition.

- **Variable-Gain LQR Balance Control**: Designed a 10-state LQR controller whose gain and feedforward matrices are interpolated online through bivariate cubic polynomials as functions of the two virtual leg lengths, ensuring stable balancing across varying leg configurations.
- **Hierarchical State Machine**: Implemented a priority-based state machine covering Dead, Recovery, Mature, Flight, Jump, Onestep, Twostep, and Creep modes, enabling complex maneuvers such as jumping over obstacles and climbing single or double steps.
- **Energy and Power Management**: Integrated supercapacitor and buffer-capacitor subsystems and implemented a quadratic-model-based power limiter that dynamically scales velocity and yaw commands according to the referee-system power cap and remaining energy.

<video width="100%" controls>
  <source src="{{ site.url }}{{ site.baseurl }}/videos/InfantryJumpSlope.mp4" type="video/mp4">
</video>

<div style="clear: both;"></div>

***

## **Aug 2025 - Present | Series-Elastic Leg Sentry Robot Control System**

![Sentry Robot]({{ site.url }}{{ site.baseurl }}/images/Sentry.jpg)

Built upon the infantry balancing robot framework to develop an autonomous navigation-oriented sentry robot. While sharing the same series-elastic leg hardware and low-level control architecture with the infantry robot, the sentry system emphasizes full autonomy and high-level battlefield maneuvering.

- **Autonomous Navigation Interface**: Added a chassis navigation command interface that receives motion references from an upper-level NUC, enabling the sentry to operate without manual remote control or keyboard input.
- **Crossstep Mode for Terrain Crossing**: Extended the LQR state machine with a new Crossstep mode for crossing ditches and kerbs, including dedicated reference generation, state transitions, and obstacle-distance-triggered activation.
- **Automated Jumping Strategy**: Replaced the mostly manual jump trigger with an autonomous jumping policy that uses standing-time threshold and obstacle proximity as conditions; supported multiple jump patterns including step jumping, reverse-slope jumping, and bank jumping for different terrain features.

<video width="100%" controls>
  <source src="{{ site.url }}{{ site.baseurl }}/videos/Sentry.mp4" type="video/mp4">
</video>

<div style="clear: both;"></div>

***

## **June 2026 - Present | Bidirectional Four-Switch Buck-Boost Buffer Capacitor Control System (FSBB)**

![Buffer Capacitor Control]({{ site.url }}{{ site.baseurl }}/images/buffercap1.png)

Designed and implemented a high-bandwidth buffer-capacitor energy management controller for RoboMaster mobile robots. The system is built around an STM32G4 MCU and uses a bidirectional four-switch Buck-Boost converter to absorb and release energy dynamically, mitigating bus-voltage sags during high-current transients.

- **Multi-Loop Control Strategy**: Implemented a state-machine-based controller with feedforward voltage-ratio compensation and three PI loops—constant-power charging loop, capacitor voltage-regulation loop, and bus-voltage support loop—allowing the system to charge, clamp, and discharge according to bus conditions.
- **High-Speed State Estimation**: Sampled input voltage, capacitor voltage, input current, output current, and capacitor current through multi-channel ADC with DMA; applied calibration and complementary filtering to improve measurement accuracy for closed-loop control.
- **Soft Start and Protection Logic**: Designed power ramp-up, over-voltage / under-voltage / over-current thresholds, and automatic shutdown/recovery on CAN timeout or abnormal operating conditions to ensure hardware safety.
- **Key Specifications**: Capacitor voltage range 9 V–26 V, maximum charging power 190 W, maximum output/supplement power 1200 W, capacitor current limit 50 A, input voltage operating range 15 V–28 V.

![Buffer Capacitor Hardware]({{ site.url }}{{ site.baseurl }}/images/buffercap2.png)

<div style="clear: both;"></div>

***

## **Oct 2024 - Present | HW-Components: Universal Robot Control Library**

As a core contributor, I architected and maintained the embedded communication layer of HW-Components, a reusable robot control library targeting RoboMaster and general mobile robotic platforms.

- **Multi-Protocol Ranging Sensor Communication**: Implemented unidirectional and bidirectional data exchange between the STM32 MCU and various ranging modules (ultrasonic, ToF, infrared, etc.), providing flexible perception interfaces for different robotic configurations.
- **Referee System Serial Link**: Maintained and optimized the UART-based communication protocol with the RoboMaster referee system, ensuring reliable reception of match-critical data such as robot status, hit points, firing permissions, and power limits.
- **Energy Management over CAN**: Developed bidirectional CAN communication with the supercapacitor and buffer-capacitor subsystems, enabling real-time power monitoring, energy buffering control, and dynamic power allocation.
- **Lever-Arm Compensation**: Implemented lever-arm compensation to correct kinematic errors caused by the physical offset between the IMU mounting position and the robot's center of rotation, improving state-estimation accuracy during rapid attitude changes.

<div style="clear: both;"></div>

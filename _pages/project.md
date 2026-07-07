---
layout: archive
title: "Project"
permalink: /project/
author_profile: true
---
---

## **Oct 2024 - Present | RoboMaster Series-Elastic Leg Infantry Robot Control System**

Developed the full-stack embedded control system for a series-elastic leg wheeled balancing infantry robot based on the STM32H7 platform. The robot uses a five-bar linkage leg mechanism and is designed for high-dynamic locomotion in the RoboMaster competition.

* **Leg Kinematics and Dynamics**: Implemented closed-form forward/inverse kinematics and Jacobian-based velocity/force mapping for the five-bar linkage, converting between joint-space motor coordinates and operational-space virtual leg length/angle for control and ground-force estimation.

* **Variable-Gain LQR Balance Control**: Designed a 10-state LQR controller whose gain and feedforward matrices are interpolated online through bivariate cubic polynomials as functions of the two virtual leg lengths, ensuring stable balancing across varying leg configurations.

* **Multi-Source State Estimation**: Fused BMI088 IMU data with wheel encoders and joint encoders; implemented a 2-state Kalman filter for forward velocity estimation, including prediction during flight phases when wheel odometry is unreliable.

* **Spring Force Compensation**: Modeled the parallel spring force-displacement characteristic with a cubic polynomial and mapped it into compensating joint torques, improving support-force estimation accuracy.

* **Hierarchical State Machine**: Implemented a priority-based state machine covering Dead, Recovery, Mature, Flight, Jump, Onestep, Twostep, and Creep modes, with automatic recovery and safety fall detection.

* **Energy and Power Management**: Integrated supercapacitor and buffer-capacitor subsystems; implemented a quadratic-model-based power limiter that dynamically scales velocity and yaw commands according to the referee-system power cap and remaining energy.

* **Communication Architecture**: Coordinated multiple FDCAN and UART buses for wheel motors, joint motors, supercapacitor, gimbal board, referee system, remote controller, and dual ranging modules.

<div style="clear: both;"></div>

---

## **Aug 2025 - Present | Series-Elastic Leg Sentry Robot Control System**

Built upon the infantry balancing robot framework to develop an autonomous navigation-oriented sentry robot. While sharing the same series-elastic leg hardware and low-level control architecture with the infantry robot, the sentry system emphasizes full autonomy and high-level battlefield maneuvering.

* **Autonomous Navigation Interface**: Added a chassis navigation command interface (`ChassisCommand` / `GlobalPathData`) that receives motion references from an upper-level NUC, enabling the sentry to operate without manual遥控 or keyboard input.

* **Crossstep Mode for Terrain Crossing**: Extended the LQR state machine with a new Crossstep mode for crossing ditches and kerbs, including dedicated reference generation, state transitions, and obstacle-distance-triggered activation.

* **Automated Jumping Strategy**: Replaced the mostly manual jump trigger with an autonomous jumping policy that uses standing-time threshold and obstacle proximity as conditions; supported multiple jump patterns including JumpStep, JumpSlope, and JumpBank for different terrain features.

* **Rich Navigation Semantics**: Implemented a mode vocabulary covering patrol, gyro-rotation, single/double-step climbing, slope jumping, high-platform jumping, and bank crossing, allowing the navigation layer to command complex maneuvers through a single mode field.

* **Long-Duration Autonomous Operation**: Reused the dual-capacitor energy management and power-limiting strategy, tuning it for the sentry's continuous autonomous patrol and defensive tasks.

<div style="clear: both;"></div>

---

## **June 2026 - Present | Bidirectional Four-Switch Buck-Boost Buffer Capacitor Control System**

Designed and implemented a high-bandwidth buffer-capacitor energy management controller for RoboMaster mobile robots. The system is built around an STM32G4 MCU and uses a bidirectional four-switch Buck-Boost converter to absorb and release energy dynamically, mitigating bus-voltage sags during high-current transients.

* **Power-Stage Control**: Generated four complementary PWM channels with dead-time insertion using the STM32G4 HRTIM, driving a synchronous Buck-Boost stage to achieve seamless transitions between buck and boost operating modes.

* **Multi-Loop Control Strategy**: Implemented a state-machine-based controller with feedforward voltage-ratio compensation and three PI loops—constant-power charging loop, capacitor voltage-regulation loop, and bus-voltage support loop—allowing the system to charge, clamp, and discharge according to bus conditions.

* **High-Speed State Estimation**: Sampled input voltage, capacitor voltage, input current, output current, and capacitor current through multi-channel ADC with DMA; applied calibration and complementary filtering to improve measurement accuracy for closed-loop control.

* **CAN-Based Supervisory Interface**: Established bidirectional FDCAN communication with the robot chassis (RX 0x113 / TX 0x114), receiving battery-power setpoints and transmitting capacitor state including voltage, current, and remaining energy percentage.

* **Soft Start and Protection Logic**: Designed power ramp-up, over-voltage / under-voltage / over-current thresholds, and automatic shutdown/recovery on CAN timeout or abnormal operating conditions to ensure hardware safety.

* **Key Specifications**: Capacitor voltage range 9 V–26 V, maximum charging power 190 W, capacitor current limit 50 A, input voltage operating range 15 V–28 V.

<div style="clear: both;"></div>

---

## **Oct 2024 - Present | HW-Components: Universal Robot Control Library**

As a Core Contributor, I architected and maintained the embedded communication layer of HW-Components, a reusable robot control library targeting RoboMaster and general mobile robotic platforms. My main contributions include:

* **Multi-Protocol Ranging Sensor Communication**: Implemented unidirectional and bidirectional data exchange between the STM32 MCU and various ranging modules (ultrasonic, ToF, infrared, etc.), providing flexible perception interfaces for different robotic configurations.

* **Referee System Serial Link**: Maintained and optimized the UART-based communication protocol with the RoboMaster referee system, ensuring reliable reception of match-critical data such as robot status, hit points, firing permissions, and power limits within the strict timing windows required by the competition rules.

* **Energy Management over CAN**: Developed bidirectional CAN communication with the supercapacitor and buffer-capacitor subsystems, enabling real-time power monitoring, energy buffering control, and dynamic power allocation to support high-current demands during agile maneuvers.

* **Lever-Arm Compensation**: Implemented lever-arm compensation to correct kinematic errors caused by the physical offset between the IMU mounting position and the robot's center of rotation, improving state-estimation accuracy during rapid attitude changes.

<div style="clear: both;"></div>

---
layout: archive
title: "项目"
permalink: /zh/project/
author_profile: true
---
---

## **2024.10 - 至今 | RoboMaster 串联腿步兵机器人控制系统**

<div style="text-align: center;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/Infantry.jpg" style="width: 80%; height: auto;" alt="步兵机器人">
</div>

基于 STM32H7 平台，为 RoboMaster 串联腿轮式平衡步兵机器人开发全栈嵌入式控制系统。机器人采用五连杆串联腿机构，面向高动态机动设计。

* **变增益 LQR 平衡控制**：设计 10 维状态 LQR 控制器，其增益矩阵与前馈项通过双变量三次多项式在线插值得到，插值变量为左右虚拟腿长，保证不同腿构型下的稳定平衡。
* **分层状态机**：实现基于优先级仲裁的状态机，覆盖死亡、恢复、正常、飞行、跳跃、上单级台阶、上多级台阶、爬行模式等模式，支持跳跃越障、单/双级上台阶等复杂机动。
* **能量与功率管理**：集成超级电容与缓冲电容两级能量缓冲；基于二次功率模型实现功率限制器，根据裁判系统功率上限与剩余能量动态缩放速度和 Yaw 指令。

<video width="100%" controls muted>
  <source src="{{ site.url }}{{ site.baseurl }}/videos/InfantryJumpSlope.mp4" type="video/mp4">
</video>

<div style="clear: both;"></div>

---

## **2025.8 - 至今 | 串联腿哨兵机器人控制系统**

![哨兵机器人]({{ site.url }}{{ site.baseurl }}/images/Sentry.jpg)

在步兵平衡机器人框架基础上，升级为面向全自主导航的哨兵机器人。哨兵与步兵共享相同的串联腿硬件平台与底层控制架构，但更强调自主决策与高层战场机动。

* **自主导航接口**：新增底盘导航指令接口，接收上层 NUC 下发的运动参考指令，使哨兵无需依赖遥控或键鼠即可运行。
* **磕台阶越障模式**：扩展 LQR 状态机，新增磕台阶越障模式，包含专用参考轨迹生成、状态迁移逻辑以及基于障碍物距离的触发条件。
* **自动跳跃策略**：将原本手动的跳跃触发改为自主策略，基于稳定站立时间阈值与障碍物距离自动触发；支持跳台阶、反飞坡、跳坎等多种跳跃模式以应对不同地形。

<video width="100%" controls muted>
  <source src="{{ site.url }}{{ site.baseurl }}/videos/Sentry.mp4" type="video/mp4">
</video>

<div style="clear: both;"></div>

---

## **2026.6 - 至今 | 双向四开关 Buck-Boost 缓冲电容控制系统 (FSBB)**

<div style="display: flex; justify-content: center; gap: 2%; margin: 1em 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/buffercap1.png" style="width: 39%; height: auto;" alt="缓冲电容控制">
  <img src="{{ site.url }}{{ site.baseurl }}/images/buffercap2.png" style="width: 39%; height: auto;" alt="缓冲电容硬件">
</div>

为 RoboMaster 移动机器人设计并实现了一套高带宽的缓冲电容能量管理控制器。系统以 STM32G4 单片机为核心，采用双向四开关 Buck-Boost 变换器拓扑，动态吸收与释放能量，抑制高动态机动时母线电压的瞬时跌落。

* **多环控制策略**：设计基于状态机的控制器，结合电压比前馈补偿与三个 PI 闭环（恒功率充电环、电容电压调节环、母线电压支撑环），使系统能够根据母线工况自动完成充电、稳压与放电。
* **高速状态估计**：通过多通道 ADC 与 DMA 采集输入电压、电容电压、输入电流、输出电流及电容电流，并进行标定与互补滤波，为闭环控制提供高精度的测量信息。
* **软启动与保护逻辑**：设计功率斜坡启动、过压 / 欠压 / 过流阈值保护，以及在 CAN 超时或异常工况下自动关断与恢复的逻辑，保障硬件运行安全。
* **主要指标**：电容电压工作范围 9 V–26 V，最大充电功率 190 W，最大输出/补充功率 1200 W，电容电流限制 50 A，输入电压工作范围 15 V–28 V。

<div style="clear: both;"></div>

---

## **2024.10 - 至今 | HW-Components：通用机器人控制库**

作为 HW-Components 通用机器人控制库的核心贡献者，我主要负责嵌入式通信层的设计与维护，目标平台覆盖 RoboMaster 及通用移动机器人。

* **多协议测距传感器通信**：实现 STM32 单片机与超声波、ToF、红外等多种测距模块之间的单向/双向数据交互，为不同机器人构型提供可扩展的感知接口。
* **裁判系统串口链路**：维护并优化基于 UART 的 RoboMaster 裁判系统通信协议，确保机器人状态、血量、射击权限、功率限制等关键赛事数据稳定接收。
* **CAN 总线能量管理**：实现单片机与超级电容及缓冲电容子系统的双向 CAN 通信，支持实时功率监测、能量缓冲控制与动态功率分配。
* **杆臂补偿**：实现杆臂补偿算法，修正因 IMU 安装位置与机器人旋转中心存在物理偏移而产生的运动学误差，提升机器人在快速姿态变化过程中的状态估计精度。

<div style="clear: both;"></div>

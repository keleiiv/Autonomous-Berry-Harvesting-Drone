# Autonomous Drone System Architecture

This document maps out the system signals and hardware interface pipelines planned for the aerial harvesting platform.

## Spatial Signal Pipeline

```text
[ Onboard Camera Stream ]
           │
           ▼
[ Companion Computer (Raspberry Pi) ] ── (Runs OpenCV & Ripeness Bounding Loops)
           │
           ▼ (Visual Servoing Error Trajectory Calculation)
[ Pixhawk Flight Controller ] ── (Executes Waypoint Corrective Navigation)
           │
           ▼ (MAVLink Command Signal)
[ Low-Level Actuator / ESP32 ] ── (Triggers Soft Gripper via PWM Signals)
```

## Communication Protocols
* **High-to-Low Level:** MAVLink protocols executed over standard hardware UART.
* **Actuation Strings:** PWM (Pulse Width Modulation) lines driving under-actuated servo mechanical assemblies.

# Autonomous Rover Summer Prototype

## Overview

This project aims to design and build a functional autonomous rover prototype during a 6-week summer development period.

The prototype will serve as a proof of concept for future expansion into a RoboCup Rescue style autonomous search and rescue rover.

### Core Capabilities

The rover should be able to:

* Operate under manual control for testing and debugging
* Sense and interpret surroundings using LiDAR and onboard sensors
* Estimate position and movement using wheel encoders and odometry
* Build maps of unknown environments
* Perform basic autonomous navigation
* Detect hazards and stop safely in emergency situations

---

## Project Goals & Milestones

### Phase 1 — Basic Mobility

**Objective:** Achieve safe physical movement.

Tasks:

* [ ] Manual motor control
* [ ] Forward / backward / turning
* [ ] Emergency stop system
* [ ] Power distribution setup

---

### Phase 2 — Low-Level Feedback

**Objective:** Estimate rover motion.

Tasks:

* [ ] Wheel encoder integration
* [ ] Odometry estimation
* [ ] Serial communication between Teensy and Jetson

---

### Phase 3 — Sensor Integration

**Objective:** Perceive the environment.

Tasks:

* [ ] LiDAR integration
* [ ] IMU integration
* [ ] Publish sensor data in ROS2

---

### Phase 4 — ROS2 Bringup

**Objective:** Connect subsystems in ROS2.

Tasks:

* [ ] Publish `/scan`
* [ ] Publish `/odom`
* [ ] Publish `/tf`
* [ ] Subscribe to `/cmd_vel`

---

### Phase 5 — Mapping & Autonomy

**Objective:** Enable autonomous operation.

Tasks:

* [ ] SLAM / mapping
* [ ] Obstacle avoidance
* [ ] Waypoint navigation
* [ ] Optional Nav2 integration

---

### Phase 6 — Safety & Reliability

**Objective:** Improve robustness and operational safety.

Tasks:

* [ ] Watchdog system
* [ ] Safety monitor node
* [ ] Fault detection
* [ ] Stop on danger behavior

---

## Planned System Architecture

```text
Laptop / Operator
│
├── SSH
├── RViz
├── Teleop
└── Logging
│
▼
Jetson Orin Nano (ROS2)
│
├── Sensor Layer
│   ├── LiDAR Driver           → /scan
│   ├── IMU Driver             → /imu
│   └── Camera Driver (opt.)   → /image
│
├── State Estimation Layer
│   ├── Encoder Odometry       → /odom
│   ├── TF Tree                → /tf
│   └── SLAM Toolbox           → /map
│
├── Autonomy Layer
│   ├── Obstacle Avoidance
│   ├── Waypoint Navigation
│   └── Nav2 (optional)
│
├── Safety Layer
│   ├── Emergency Stop Monitor
│   ├── Watchdog
│   └── Stop-on-danger Logic
│
└── Hardware Interface Layer
    └── USB Serial
            │
            ▼
      Teensy / Arduino
      │
      ├── Motor PWM / Direction Control
      ├── Encoder Reading
      ├── Emergency Stop Input
      ├── Watchdog Timeout
      └── Status / Encoder Feedback
            │
            ▼
       Motor Driver
            │
            ▼
          Motors
```

---

## Technology Stack

### Hardware

* NVIDIA Jetson Orin Nano
* Teensy 4.1
* LiDAR
* IMU
* Wheel encoders
* Motor driver
* Battery / power system

### Software

* Ubuntu Linux
* Open Robotics ROS2
* Python
* C++
* Teensyduino

---

## Future Development

Potential future additions:

* Camera based perception
* GPS integration
* Autonomous exploration
* Victim detection for RoboCup Rescue
* Multi sensor fusion

---

## References / Inspiration

Projects and frameworks that may be useful:

* Open Robotics Navigation2
* Clearpath Robotics Husky / Jackal
* NVIDIA Jetson ROS projects

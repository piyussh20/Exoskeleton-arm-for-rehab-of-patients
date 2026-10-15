# Exoskeleton-arm-for-rehab-of-patients
# 2-DOF Upper-Limb Rehabilitation Exoskeleton (EMG + IMU Controlled)

A low-cost, wearable 2-degree-of-freedom exoskeleton for upper-limb rehabilitation. It assists **shoulder flexion-extension** and **elbow flexion-extension**, and uses **EMG + IMU sensor fusion** to confirm that a movement is genuinely intended by the user before the motors assist.

**Estimated build cost: ≈ ₹9,000**, compared with ₹19–28 lakh (≈ $20,000–30,000) for commercial alternatives in the US market.

---

## Motivation

Stroke, sports injuries, and age-related muscle weakness often limit shoulder and elbow function. Conventional physiotherapy is labor-intensive and depends on therapist availability, while commercial robotic rehabilitation devices are very expensive. This project aims to provide an affordable, intent-driven assistive device.

## Target Users

- Patients undergoing physiotherapy (post-stroke or post-surgery)
- Sports players recovering from upper-limb injuries
- Elderly individuals with reduced muscular strength

## Key Features

- 2 DOF: shoulder and elbow flexion-extension
- EMG + IMU sensor fusion for confirming user movement intent
- Closed-loop PID motor control for smooth, controlled assistance
- Gear-reduced actuation for slow, high-torque, rehabilitation-safe motion
- Low-cost, commodity components

## Hardware

| Component | Details |
|---|---|
| Microcontroller | Teensy 4.1 |
| Actuators | 2 × 12V DC geared motors (50RPM) |
| Gear train | Bevel and Spur gears, 16T / 25T / 50T |
| IMU | BNO055 (9-axis absolute orientation) |
| EMG sensors | 2 × (biceps brachii, shoulder/deltoid) |
| Motor drivers | 2 × H-bridge modules |
| Joint feedback | Potentiometers |

**Gear configuration:** shoulder 16T → 50T (3.125:1), elbow 25T → 50T (2:1).

## How It Works

1. The EMG sensors detect muscle activation (onset) at the biceps and shoulder.
2. The BNO055 IMU measures limb orientation and angular velocity.
3. The Teensy 4.1 fuses both signals: assistance is triggered only when **EMG activation and IMU motion agree**, which reduces false triggers from noise or involuntary movement.
4. A PID controller drives the corresponding motor through the gear train toward the target joint angle, using joint-angle feedback to close the loop.

```
EMG x2 ─┐
        ├─► Teensy 4.1 ─► Motor Driver ─► DC Motor ─► Gear Train ─► Joint
IMU ────┘   (filtering,        ▲                                      │
             fusion, PID)      └────────── Angle feedback ◄───────────┘
```


component


Teensy 4.1 
BNO055 IMU 
EMG sensors (×2) candy module
DC geared motors (×2) 
Motor drivers (×2) 
Gears + hardware 
Frame / rods / mounts 
Battery, wiring, enclosure 





## Safety Note

This is a research prototype and **not a certified medical device**. It should not be used on patients without proper ethical approval and clinical supervision.

## Future Work

- Machine-learning-based intent classification
- Additional DOFs (abduction/adduction, rotation)
- Pilot trials with physiotherapy patients, injured athletes, and elderly users
- Weight reduction 
## Authors
Raviraj Surve
Abhishek Nair
Piyush Vaidya
Gargee Phansekar

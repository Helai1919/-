# STM32 Fixed-Path Motion Example

This repository contains a minimal STM32 HAL example that drives a differential robot along a fixed rectangular path using waypoint tracking.

## Highlights
- Waypoint list defines a closed-loop rectangle.
- Simple proportional linear and angular control to reach each waypoint.
- PWM outputs on TIM3 CH1/CH2 for motor control (replace with your board-specific setup).
- Stub functions for odometry and GPIO/clock configuration so the control loop remains compilable.

## Usage
1. Generate your board-specific initialization code with STM32CubeMX (clock, GPIO, timers, motor directions, encoders) and merge it into `main.c` where indicated.
2. Implement `update_odometry()` using your encoder and IMU data to update `current_pose`.
3. Build and flash the firmware; the robot will move through the waypoints and stop at the end of the path.

## Path Definition
The path is defined in `path[]` inside `main.c` as `(x, y, yaw)` waypoints in meters and radians. Adjust the coordinates, gains, and tolerances to suit your platform.

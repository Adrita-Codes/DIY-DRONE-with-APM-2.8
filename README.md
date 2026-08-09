# DIY-DRONE-with-APM-2.8
Configured and calibrated a manual quadcopter utilizing the open-source ArduCopter C++ firmware stack, mapping physical 2.4GHz RC transmitter inputs to internal flight stability loops via PWM/PPM signal decoding.


# Manual RC Quadcopter Drone via ArduCopter

An engineering-grade quadcopter drone system utilizing the open-source ArduCopter autopilot software framework. This project demonstrates high-reliability firmware configuration, real-time manual radio control, and hardware-to-software signal decoding.

## Hardware System Architecture & Schematic
Below is the verified system architecture diagram outlining the multi-channel signal routing and isolated power distribution layers of the quadcopter:


### Circuit Architecture Breakdown:
* **Signal Decoupling & Inputs:** A FlySky **FS-iA6B** 6-channel receiver decodes 2.4GHz RF signals, routing individual PWM channels (CH1-CH4 for Roll, Pitch, Throttle, and Yaw) directly into the hardware input stage of the **APM 2.8** Flight Controller.
* **Actuator Control Matrix:** The flight stabilization firmware commands four Electronic Speed Controllers (**ESCs**) via dedicated hardware output lines (1–4) to drive the brushless motors synchronously based on pilot commands.
* **Isolated Power Rail Design:** Powered by a 12.6V 3S LiPo battery managed by a dedicated Power Module. The layout splits into a clean +5V step-down logic level rail to power the flight controller safely, while routing high-current +12.6V lines directly to the ESC power buses to prevent voltage drops.

## Tech Stack & Components
* **Flight Software:** ArduCopter Firmware Stack (C++ based Open-Source Software)
* **Ground Control Station:** Mission Planner GUI (for calibration and testing)
* **Hardware Brain:** APM 2.8 Flight Controller
* **Radio Hardware:** FlySky FS-iA6B 2.4GHz Receiver & Transmitter
* **Protocols:** PWM (Pulse-Width Modulation) / PPM (Pulse-Position Modulation) channel processing

## Calibration Instructions
1. Flash the ArduCopter firmware onto the APM 2.8 board using Mission Planner.
2. Complete mandatory hardware calibrations: **Compass**, **Accelerometer**, and **Radio Calibration**.
3. Perform ESC calibration to ensure all brushless motors spin synchronously to manual transmitter throttle inputs.

## ⚠️ Safety Disclaimer
This drone was calibrated and tested in a controlled environment. Propellers were completely removed during all initial software calibration, bench testing, and radio mapping to ensure absolute safety.

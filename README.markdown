# DIY 3D Scanner

## Project Overview
This project provides a step-by-step guide to building an affordable and accessible 3D scanner using off-the-shelf components and open-source software. The scanner uses an Arduino Uno R3 to control NEMA17 stepper motors for object rotation and sensor elevation, a VL53L0X laser range finder for distance measurements, and a Micro SD card module to store scan data. The goal is to democratize 3D scanning technology for creators, educators, and hobbyists.

## Components
- Arduino Uno R3
- NEMA17 4.2 Kg-cm Stepper Motor (2)
- A4988 Stepper Motor Driver Module (2)
- VL53L0X Laser Range Finder Distance Sensor Module
- Micro SD card Reader Module
- GT2 20 Teeth Aluminium Timing Pulley
- GT2 Open Loop Timing Belt
- Radial Ball Bearing 4mm Dia

## Hardware Setup
1. **Wiring**:
   - MOTOR1 (object rotation): IN1 (Pin 9), IN2 (Pin 10), IN3 (Pin 11)
   - MOTOR2 (elevation): IN1 (Pin 2), IN2 (Pin 3), IN3 (Pin 4), IN4 (Pin 5)
   - VL53L0X: Connect via I2C (SDA, SCL to Arduino I2C pins)
   - SD Card: CS (Pin 10, note conflict with MOTOR1_IN2; use a different pin if needed), MOSI (Pin 11), MISO (Pin 12), SCK (Pin 13)
2. **Mechanical Assembly**: Mount the stepper motors with a GT2 belt and pulley system to rotate the object and adjust sensor height.

## Software Requirements
- Arduino IDE
- Libraries: `Adafruit_VL53L0X`, `AccelStepper`, `SPI`, `SD`

## Installation
1. Install the required libraries via the Arduino Library Manager.
2. Connect the Arduino to your computer.
3. Open `3D_Scanner.ino`, verify, and upload the code.

## Usage
1. Power the Arduino and attached hardware.
2. The scanner will rotate the object, adjust elevation every 9.5 degrees, and measure distances with the VL53L0X.
3. Data (angle, z-height, x, y, distance) is saved to `scan.txt` on the SD card.
4. Retrieve the SD card and process `scan.txt` to generate a 3D model (e.g., using point cloud software).

## Notes
- **Pin Conflict**: Pin 10 is used for both SD_CS and MOTOR1_IN2. Adjust the SD_CS_PIN definition in the code to a free pin (e.g., 8) and rewire accordingly.
- **Calibration**: Adjust `ANGLE_INCREMENT` and `STEPS_PER_REV` based on your mechanical setup.
- **Images**: Add diagrams (e.g., `image1.png` to `image46.svg` from the PowerPoint) to the repository for clarity.

## Contributing
Feel free to fork this repository, submit issues, or pull requests to improve the project.
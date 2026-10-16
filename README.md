# MiniTank Swarm RL

Three small tank-style robots learning to work as a swarm through **reinforcement learning (RL)**, with **implicit coordination**: no robot sends commands to the others. Each one learns its behavior in simulation from its own sensors, and the coordination comes out of training.

Each robot runs on an **ESP32-S3** and senses through a **camera**, a **microphone** and a **gyroscope**.

---

## Contents

- [Resources](#resources)
- [Robot hardware](#robot-hardware)
- [Project log](#project-log)
- [Open questions](#open-questions)
- [Next steps](#next-steps)

---

## Resources

| Resource | What it is |
|---|---|
| *Reinforcement Learning for Robotics* (DigiKey × Shawn Hymel, YouTube) | Six-part series on the sim-to-real pipeline: build the robot in the MuJoCo physics simulator, train it there with RL, then run the trained behavior on the real robot. Part 1 imports a robot CAD model into MuJoCo. |
| [MKCOZMO-CONTROLLER](https://github.com/nturmose21/MKCOZMO-CONTROLLER) | Cozmo-style ESP32-S3 robot this project builds from |
| [MK2-Czmo](https://github.com/nturmose21/MK2-Czmo) | Earlier Wi-Fi version of the same robot (ESP32-C3), for reference |

---

## Robot hardware

### Swarm robot (planned)

| Part | Decision |
|---|---|
| Controller | ESP32-S3 |
| Chassis | Tank-style (adapted from the Cozmo build) |
| Sensors | Camera, microphone, gyroscope |
| Count | 3 robots |

### Starting point: MKCozmo (ESP32-S3)

Cozmo-inspired mini robot: two continuous-rotation servos, animated OLED eyes, Bluetooth Xbox controller via Bluepad32.

| Part | Details |
|---|---|
| Controller | ESP32-S3 (tested on Seeed XIAO ESP32-S3) |
| Drive | 2× continuous-rotation servos, 50 Hz PWM, 500–2400 µs, neutral 1500 µs |
| Display | SSD1306 128×64 OLED, I²C `0x3C`, eyes at ~30 fps |
| Power | LiPo / USB; 5 V servo rail, 3.3 V logic |
| Input | Xbox Series controller over Bluetooth (Bluepad32) |

| Signal | ESP32-S3 pin |
|---|---|
| Left servo | D6 |
| Right servo | D7 |
| OLED SDA | D8 |
| OLED SCL | D9 |

Libraries: Bluepad32 4.x, ESP32Servo, Adafruit SSD1306, Adafruit GFX. Partition scheme: **Huge APP**.

---

## Project log

### 2026-10-15 — Kickoff

- Set the goal: a 3-robot swarm with implicit coordination, trained with RL
- Chose the DigiKey × Shawn Hymel RL series as the learning path, starting with Part 1 (CAD model → MuJoCo)
- Documented the existing Cozmo builds as the hardware starting point
- Decided each robot carries a camera, microphone and gyroscope
- Chose **ESP32-S3** as the controller for all three robots
- Decided to adapt the Cozmo build into a **tank-style** chassis

---

## Open questions

- Which exact camera/mic and gyroscope modules?
- The tutorial trains a self-balancing bot; how do its steps carry over to a tank?
- What task does the swarm learn first, and what reward defines success?

## Next steps

- Work through Part 1: get a robot CAD model into MuJoCo
- Design the tank chassis
- Pick sensor modules

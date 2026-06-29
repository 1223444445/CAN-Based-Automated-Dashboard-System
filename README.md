# 🚗 CAN-Based Automotive Dashboard System

A distributed embedded system developed using **PIC18F4580 microcontrollers** that demonstrates real-time communication between multiple **Electronic Control Units (ECUs)** using the **Controller Area Network (CAN)** protocol.

---

# 📋 Table of Contents

* About the Project
* Hardware Used
* Features
* System Architecture
* ECU Responsibilities
* Project Structure
* Communication Protocol
* CAN Communication Flow
* How to Build and Run
* Sample Output
* Skills Demonstrated
* Author
* License

---

# 📖 About the Project

Modern vehicles use multiple **Electronic Control Units (ECUs)** to monitor and control different vehicle functions. These ECUs communicate over a **Controller Area Network (CAN)** to exchange information in real time.

This project simulates the same architecture using **three PIC18F4580-based ECUs** connected through a CAN bus. Each ECU performs a dedicated function and shares information with the other ECUs.

* **Model 1 (ECU 1)** monitors **Vehicle Speed** and **Gear Position**.
* **Model 2 (ECU 2)** monitors **Engine RPM** and **Indicator Status**.
* **Model 3 (ECU 3)** acts as the **Central Dashboard**, receiving CAN messages from the other ECUs and displaying all vehicle parameters on a single LCD.

The project demonstrates modular embedded software development, CAN communication, and real-time data exchange between multiple controllers.

---

# 🔧 Hardware Used

| Component     | Description                 |
| ------------- | --------------------------- |
| PIC18F4580    | Microcontroller             |
| MCP2551       | CAN Bus Transceiver         |
| 16x2 CLCD     | Dashboard Display           |
| Potentiometer | Speed Simulation (ADC)      |
| Push Buttons  | Gear Selection              |
| LEDs          | Indicator Status Simulation |
| CAN Bus       | Communication between ECUs  |

---

# ✨ Features

* Multi-ECU CAN communication
* Real-time vehicle parameter monitoring
* Vehicle speed display
* Gear position display
* Engine RPM display
* Indicator status display
* Distributed ECU architecture
* Central dashboard displaying all vehicle information
* Modular Embedded C implementation
* Real-time CAN message transmission and reception

---

# 🏗️ System Architecture

```text
                 +-------------------------+
                 |        MODEL 1          |
                 |-------------------------|
                 | Vehicle Speed           |
                 | Gear Position           |
                 | CAN Transmitter         |
                 | CLCD Display            |
                 +-----------+-------------+
                             |
                             |
======================== CAN BUS ========================
                             |
                             |
                 +-----------+-------------+
                 |        MODEL 2          |
                 |-------------------------|
                 | Engine RPM              |
                 | Indicator Status        |
                 | CAN Transmitter         |
                 | CLCD Display            |
                 +-----------+-------------+
                             |
                             |
======================== CAN BUS ========================
                             |
                             |
                 +-----------v-------------+
                 |        MODEL 3          |
                 |-------------------------|
                 | CAN Receiver            |
                 | Central Dashboard       |
                 | Displays:               |
                 | • Speed                 |
                 | • Gear                  |
                 | • RPM                   |
                 | • Indicator             |
                 +-------------------------+
```

---

# 🚘 ECU Responsibilities

## 🚙 Model 1 – Vehicle Speed & Gear ECU

### Responsibilities

* Reads vehicle speed using the ADC.
* Detects the current gear position.
* Displays Speed and Gear Position on the CLCD.
* Packages Speed and Gear information into CAN messages.
* Transmits CAN frames to the CAN bus.

### Display

```text
+----------------+
|SPD : 072 km/h  |
|GEAR: G3        |
+----------------+
```

---

## 🚗 Model 2 – Engine RPM & Indicator ECU

### Responsibilities

* Monitors Engine RPM.
* Monitors Left/Right Indicator status.
* Displays RPM and Indicator information.
* Packages RPM and Indicator data into CAN messages.
* Transmits CAN frames over the CAN bus.

### Display

```text
+----------------+
|RPM : 3200      |
|IND : LEFT      |
+----------------+
```

---

## 🚘 Model 3 – Central Dashboard ECU

### Responsibilities

* Receives CAN messages from Model 1.
* Receives CAN messages from Model 2.
* Decodes received CAN frames.
* Displays all vehicle parameters on a single dashboard.

### Display

```text
+----------------+
|SPD:072 RPM3200 |
|G3      LEFT    |
+----------------+
```

---

# 📁 Project Structure

```text
CAN-Based-Automotive-Dashboard-System/
│
├── Model_1/
│   ├── adc.c
│   ├── adc.h
│   ├── can.c
│   ├── can.h
│   ├── clcd.c
│   ├── clcd.h
│   ├── digital_keypad.c
│   ├── digital_keypad.h
│   ├── ecu1_main.c
│   ├── ecu1_main.h
│   ├── ecu1_sensor.c
│   ├── ecu1_sensor.h
│   ├── msg_id.h
│   └── msg_id1.h
│
├── Model_2/
│   ├── adc.c
│   ├── adc.h
│   ├── can.c
│   ├── can.h
│   ├── clcd.c
│   ├── clcd.h
│   ├── digital_keypad.c
│   ├── digital_keypad.h
│   ├── ecu2_main.c
│   ├── ecu2_main.h
│   ├── ecu2_sensor.c
│   ├── ecu2_sensor.h
│   ├── msg_id.h
│   └── msg_id1.h
│
├── Model_3/
│   ├── adc.c
│   ├── adc.h
│   ├── can.c
│   ├── can.h
│   ├── clcd.c
│   ├── clcd.h
│   ├── digital_keypad.c
│   ├── digital_keypad.h
│   ├── main.c
│   ├── message_handler.c
│   ├── message_handler.h
│   ├── timer0.c
│   ├── timer0.h
│   ├── msg_id.h
│   └── msg_id1.h
│
└── README.md
```

---

# 📡 Communication Protocol

| Protocol           | Purpose                              |
| ------------------ | ------------------------------------ |
| CAN                | Communication between the three ECUs |
| ADC                | Vehicle Speed Acquisition            |
| Parallel Interface | CLCD Display                         |
| GPIO               | Push Buttons and LEDs                |

---

# 🔄 CAN Communication Flow

```text
Vehicle Inputs
      │
      ▼
+------------------+
|     MODEL 1      |
| Speed + Gear     |
+------------------+
         │
         │ CAN Message
         ▼
========================
       CAN BUS
========================
         ▲
         │ CAN Message
+------------------+
|     MODEL 2      |
| RPM + Indicator  |
+------------------+
         │
         ▼
========================
       CAN BUS
========================
         │
         ▼
+------------------+
|     MODEL 3      |
| Central Dashboard|
+------------------+

Displays:
• Vehicle Speed
• Gear Position
• Engine RPM
• Indicator Status
```

---

# 🛠️ How to Build and Run

## Prerequisites

* MPLAB X IDE
* XC8 Compiler
* PIC18F4580 Development Board
* MCP2551 CAN Transceiver

## Steps

1. Clone the repository.
2. Open the required model project in MPLAB X IDE.
3. Build the project using the XC8 compiler.
4. Generate the HEX file.
5. Program the PIC18F4580.
6. Connect all three ECUs through the CAN bus.
7. Power the system.
8. Observe real-time communication between the ECUs.

---

# 📺 Sample Output

### Model 1

```text
+----------------+
|SPD : 072 km/h  |
|GEAR : G3       |
+----------------+
```

### Model 2

```text
+----------------+
|RPM : 3200      |
|IND : RIGHT     |
+----------------+
```

### Model 3

```text
+----------------+
|SPD:072 RPM3200 |
|G3     RIGHT    |
+----------------+
```

---

# 💡 Skills Demonstrated

* Embedded C Programming
* PIC18F4580 Microcontroller Programming
* CAN Protocol Implementation
* Multi-ECU Communication
* Interrupt Handling
* ADC Interfacing
* CLCD Interfacing
* Embedded Driver Development
* Real-Time Embedded Systems
* Modular Firmware Design

---

# 👨‍💻 Author

**Name:** Abinand V Nair

**Program:** Emertxe Embedded Systems Training

**Date:** March 2026

---

# 📄 License

This project was developed as part of the **Emertxe Information Technologies Embedded Systems Training Program**.

⭐ If you found this project helpful, consider giving it a **Star ⭐** on GitHub.

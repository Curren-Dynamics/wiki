# ESCuino-X2 Hardware Overview

**ESCuino-X2** is a compact, dual brushed motor controller with an integrated ATmega328P microcontroller. Designed to be both Arduino-compatible and rugged enough for high-current applications, this board brings together essential embedded features for robotics, R/C vehicles, and DIY electronics.

---

## 🧠 Microcontroller

### ATmega328P-PN
- 8-bit AVR MCU running at 16 MHz
- 32 KB Flash / 2 KB SRAM / 1 KB EEPROM
- Arduino Uno R3 pinout and bootloader compatible
- Operates at 5V, with AVCC decoupled and filtered
- Exposes UART, SPI, I²C, PWM, and ADC pins on 0.1" headers

---

## ⚡ Power Regulation

### MAX17502FATB+T
- High-efficiency, synchronous step-down converter
- Input range: 4.5V to 60V
- Output: 5V regulated (used to power MCU and logic)
- Internal compensation and soft-start
- Integrated MOSFET, 500kHz switching frequency

**Use case:** Powers logic and USB devices from battery voltage.

---

## 🔌 USB-UART Interface

### CP2102-GMR
- USB to UART bridge
- Full-speed USB 2.0
- Supports onboard serial flashing of the ATmega328P
- Works with Arduino IDE via standard USB CDC drivers

**Connector:** USB-C (HYCW445-USBC16-730B)

---

## 🔧 Motor Drivers

### DRV8245HQPWPRQ1 ×2
Two independent H-bridge motor drivers (one per motor):

- Supply voltage (VM): 4.5V – 37V
- Max continuous output current: **6.5A RMS**
- Peak output current: up to 10–14A (depending on cooling and duty cycle)
- Integrated power FETs (no external FETs needed)
- Control: PH/EN or PWM/PWM modes
- Current sensing via IPROPI pin (proportional to output current)
- Built-in protections: overcurrent, undervoltage, thermal shutdown, short-circuit

**Note:** Each motor channel can safely sustain ~6.5A continuous with proper PCB heat dissipation. Higher peak currents are possible for brief durations.

---

## 🔋 Power & Connectors

- **Power input range (VIN):** 4.5V – 35V
- **Input capacitors:** 390μF bulk + 100nF ceramic decoupling
- **Connectors:**  
  - VM and GND via PM254V screw terminals  
  - Motor A and Motor B outputs via separate headers  
  - USB-C for power and UART

---

## 📟 Indicators

- Power LED (Green)
- TX/RX LEDs (White) for USB serial activity

---

## 🧩 GPIO & Expansion

Exposed I/O on 2.54mm headers:

| Header | Function                         |
|--------|----------------------------------|
| P1     | Digital I/O (D2–D9)              |
| P2     | Analog I/O (A0–A5) + UART        |
| P3     | SPI, I²C, reset, and power lines |
| H4     | Motor control pins (PH, EN, DRVOFF, IPROPI, NSLEEP) per driver |

---

## ⚠️ Protections

- **TVS Diode (D3):** SMAJ36A for transient voltage suppression on VIN
- **Input filtering:** Several MLCCs and RC snubbers
- **USB ESD protection:** TPD2EUSB30ADRTR for DP/DM lines

---

## 📐 Crystal

- **X1:** 16 MHz crystal for ATmega328P with 22pF load capacitors

---

## 📎 BOM Summary (Core ICs)

| Ref | Part                         | Function                    |
|-----|------------------------------|-----------------------------|
| U9  | ATmega328P-PN                | MCU                         |
| U3  | MAX17502FATB+T               | 5V Buck Regulator           |
| U5  | CP2102-GMR                   | USB-UART Bridge             |
| U10 | DRV8245HQPWPRQ1              | Motor Driver A              |
| U11 | DRV8245HQPWPRQ1              | Motor Driver B              |

---

## 🛠 Notes for Designers

- **Grounding:** PGND and logic GND are clearly separated; star grounding is recommended at the power input.
- **VIN filtering:** Bulk and high-frequency caps present, but layout should be reviewed for thermal/via optimization.
- **Modularity:** Can serve as both an ESC and a general-purpose Arduino-compatible controller with motor drivers.

---

Built in the Ozarks. Open to the world.
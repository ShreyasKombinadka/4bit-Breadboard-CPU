# 4-Bit Breadboard CPU — Register File Module

This is the register file module of a custom 4-bit breadboard CPU built entirely from scratch using discrete components. The project focuses on low-level hardware design, emphasizing foundational digital electronics without microcontrollers or EEPROMs.

## 🧠 Overview

The module implements a 4-bit register file containing:
- **Register A** – General-purpose
- **Register B** – General-purpose
- **Register OP** – Special-purpose (cannot read from the bus, only from user input)

Control of all operations is done via a **hardwired ROM-like logic unit**, built using:
- A decoder
- Diodes and resistors
- Tri-state buffers
- Demultiplexers

Each 4-bit instruction triggers a unique 7-bit control word.

---

## ⚙️ Features

- Built with D flip-flops and tri-state buffers
- Load and move operations between registers and bus
- Manual user input loading
- Unified clock and reset gating via master enable signal
- Custom control ROM maps instructions (0000–1111) to specific operations

### Instruction Set

| Opcode | Operation                        |
|--------|----------------------------------|
| 0000   | NOP                              |
| 0001   | Load user input → RegA           |
| 0010   | Load user input → RegB           |
| 0011   | Load user input → RegOP          |
| 0100   | Load BUS → RegA                  |
| 0101   | Load BUS → RegB                  |
| 0110   | Output RegA → BUS                |
| 0111   | Output RegB → BUS                |
| 1000   | Output RegOP → BUS               |
| 1001   | Move RegA → RegB                 |
| 1010   | Move RegB → RegA                 |
| 1011   | Move RegOP → RegA                |
| 1100   | Move RegOP → RegB                |
| 1111   | Disable / Clear all Registers    |

---

## 🧩 Structure

- **Registers**: D flip-flops store 4-bit values
- **Control**: Each register is controlled via demux and tri-state buffers
- **Bus Interaction**: Registers can read from / write to the bus based on control logic
- **Clocking**: Clock signal is gated with enable lines for precise control
- **Reset**: Unified reset clears all registers

---

## 🔧 Tools & Components

- 74-series logic ICs
- Manual DIP switches for input
- Pushbuttons for clock and load
- Breadboard-based layout (no PCBs or MCUs)
- All modules manually designed and interconnected

---

## 🔜 Upcoming

This register file is part of a larger CPU project including:
- Arithmetic Logic Unit (ALU)
- Program counter and memory
- Control ROM (AR ROM and later ARM ROM)

Stay tuned for updates as each module is built, tested, and documented.

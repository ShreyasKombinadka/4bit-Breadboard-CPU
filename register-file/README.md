# 4-Bit Breadboard CPU — Register File Module

This is the register file module of CPU built entirely from discrete components. The project focuses on low-level hardware design, emphasizing foundational digital electronics without microcontrollers or EEPROMs.

## Overview

The module implements a 4-bit register file containing:
- **Register A** – General-purpose
- **Register B** – General-purpose
- **Register OP** – Special-purpose (cannot read from the bus, only from user Immediate value)

Control of all operations is done via a **hardwired Diode ROM unit**, built using:
- A decoder
- Diodes and resistors
- Buffer

Each 4-bit instruction triggers a unique 7-bit control word.

---

## Features

- Built with D flip-flops and tri-state buffers
- Load and move operations between registers are done through a shared bus
- Immediate values can be loaded throough dedicated instructions
- Unified clock and reset gating via master enable signal
- Control ROM maps instructions (0000–1111) to specific operations

---

![Detailed Register File Setup](./Copy%20of%20Detailed%20image.jpg)

---
### Instruction Set

| Opcode | Operation          |
|--------|--------------------|
| 0000   | NOP                |
| 0001   | LDI → A            |
| 0010   | LDI → B            |
| 0011   | LDI → OP           |
| 0100   | BUS → A            |
| 0101   | BUS → B            |
| 0110   | A → BUS            |
| 0111   | B → BUS            |
| 1000   | OP → BUS           |
| 1001   | A → B              |
| 1010   | B → A              |
| 1011   | OP → A             |
| 1100   | OP → B             |
| 1111   | Clear              |

---

## Structure

- **Registers**: D flip-flops store 4-bit values
- **Control**: Each register is controlled via demux and tri-state buffers
- **Bus Interaction**: Registers can read from / write to the bus based on control logic
- **Clocking**: Clock signal is gated with enable lines for precise control of each individual reg operations
- **Reset**: Unified reset clears all registers

---

## Tools & Components

- 74-series logic ICs
- Manual DIP switches for instruction input
- Breadboard-based layout (no PCBs or MCUs)
- All modules manually designed and interconnected

---

## Upcoming
- Arithmetic Logic Unit (ALU)
- Main control ROM
- - Program counter and memory

Stay tuned for updates as each module is built, tested, and documented.

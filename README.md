# 16-bit Pipelined RISC Processor (Logisim Evolution)

This repository contains the full implementation of a 16-bit RISC pipelined processor designed and simulated using [Logisim-Evolution](https://github.com/logisim-evolution/logisim-evolution). The project was developed as part of the COE301 - Computer Architecture & Assembly Language course (Term 242, Spring 2025).

## 🧠 Overview

The processor implements a reduced instruction set computing (RISC) architecture with the following features:
- 16-bit word size
- 7 general-purpose registers (R1-R7), R0 hardwired to 0
- 1 program counter (PC)
- 3 instruction formats: R-type, I-type, and J-type
- Custom ISA with 24+ instructions including arithmetic, logic, memory, and control flow
- Separate instruction and data memory
- 5-stage pipelined datapath: IF, ID, EX, MEM, WB
- Hazard detection and forwarding logic
- Support for jump and link (JAL), procedure return (JR), and reverse operations (REVA, REVL, REVH)

## 🛠️ Files

| File | Description |
|------|-------------|
| `projv3.circ` | Logisim-Evolution circuit file containing the full processor implementation |
| `COE301-PROJ-T242(2).pdf` | Project specification detailing ISA, instructions, datapath, and control logic |
| `README.md` | This file |
| `test_programs/` | (To be added) Sample programs and test cases used for simulation |

## 🧱 Instruction Set Architecture (ISA)

The processor supports:
- **R-type instructions**: ADD, SUB, SLT, AND, OR, XOR, NOR, SLL, SRL, SRA, ROR, REVA, REVL, REVH
- **I-type instructions**: ADDI, ANDI, ORI, XORI, LW, SW, BEQ, BNE
- **J-type instructions**: J, JAL, LUI

All instructions are 16 bits long. Immediate fields are sign-extended or zero-extended depending on the opcode.

## 🔁 Pipeline Details

The processor uses a standard 5-stage pipeline:
1. **Instruction Fetch (IF)**
2. **Instruction Decode/Register Fetch (ID)**
3. **Execution/Effective Address Calculation (EX)**
4. **Memory Access (MEM)**
5. **Write Back (WB)**

### Features:
- **Hazard detection unit** to insert pipeline stalls where needed (e.g., LW-use hazard)
- **Forwarding unit** to reduce stalls and improve performance
- **1-cycle penalty** for taken branches and jumps
- **PC-relative addressing** for branching instructions

## 🧪 Testing

The design was tested through:
- Unit testing of ALU, control logic, register file, and memory
- Instruction-level testing for each supported opcode
- A complete sample program to sum the contents of an array via a function call using JAL and JR

### Example Test Program:
- Initializes an array with constants
- Passes the array base and size to a function
- Function calculates and returns the sum

## 🚀 How to Run

1. Download and install [Logisim-Evolution](https://github.com/logisim-evolution/logisim-evolution/releases).
2. Open `projv3.circ` in Logisim.
3. Load your test program into the instruction memory starting at address `0x0000`.
4. Run the simulation step-by-step or continuously and observe register/memory updates.

## 📚 Documentation

For complete design specifications, control signal tables, encoding formats, and implementation details, refer to the attached PDF file:
- [`COE301-PROJ-T242(2).pdf`](./COE301-PROJ-T242(2).pdf)

## 👥 Authors & Teamwork

This project was collaboratively developed by a student team for the COE301 course. Contributions included shared work on:
- Datapath and ALU design
- Pipeline implementation and control
- Hazard detection/forwarding logic
- Test program creation and debugging

## 📦 License

This project is part of an academic course and is distributed for educational purposes only.

---

### 📝 Note:
Please make regular backups while working in Logisim-Evolution as it may crash unexpectedly.


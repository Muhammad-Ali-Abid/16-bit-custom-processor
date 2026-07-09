# 16-bit Custom Processor in Verilog

A custom **16-bit multi-cycle processor** designed from scratch using **Verilog HDL**. This project demonstrates the implementation of the fundamental building blocks of a processor including the control unit, program counter, instruction memory, data memory, register file, and arithmetic logic unit (ALU).

The processor follows a **five-stage execution cycle**:

```
Fetch → Decode → Execute → Memory → Write Back
```

---

## Features

- Custom 16-bit instruction format
- Multi-cycle architecture
- Finite State Machine (FSM) based Control Unit
- 8 General Purpose Registers
- 8-bit Register Width
- 16 Instruction Memory Locations
- 8 Data Memory Locations
- Arithmetic and Logical Operations
- Load and Store Instructions
- Immediate Operations
- Modular RTL Design

---

## Architecture

```
                +----------------------+
                |   Control Unit (FSM) |
                +----------+-----------+
                           |
      ---------------------------------------------------
      |        |         |          |                  |
    Fetch    Decode    Execute    Memory         Write Back
      |        |          |          |                |
      |        |          |          |                |
+-----------+  |   +-------------+   |    +----------------+
| Program   |  |   |     ALU     |   |    | Register File  |
| Counter   |  |   +-------------+   |    +----------------+
+-----------+  |          |          |             ^
      |        |          |          |             |
      v        |          |          |             |
+----------------------+   |   +---------------+   |
| Instruction Memory   |---+-->| Data Memory   |---+
+----------------------+       +---------------+
```

---

## Modules

### Control Unit
- FSM-based controller
- Generates stage control signals
- Controls processor execution flow

States:
- Idle
- Fetch
- Decode
- Execute
- Memory
- Write Back

---

### Program Counter

Maintains the address of the current instruction and increments during the Fetch stage.

---

### Instruction Memory

Stores program instructions.

Current size:

- 16 instructions
- 16-bit instruction width

Instructions are initialized using:

```verilog
$readmemb("Instruction_memory.txt", mem);
```

---

### Register File

Contains:

- 8 Registers
- 8-bit each

Supports:

- Read RS1
- Read RS2
- Write RD

---

### ALU

Supported operations:

| Opcode | Operation |
|---------|-----------|
|0000|Load|
|0001|Store|
|0010|AND|
|0011|OR|
|0100|XOR|
|0101|Shift Left|
|0110|Shift Right|
|0111|Add Immediate|
|1000|Addition|
|1001|Subtraction|

---

### Data Memory

Stores data for Load and Store instructions.

Memory Size:

- 8 locations
- 8-bit each

---

## Instruction Format

```
 -------------------------------------------------
| RD | Immediate / RS2 | RS1 | Opcode |
 -------------------------------------------------
15 13               7    6 4      3 0
```

Where:

- RD = Destination Register
- RS1 = Source Register 1
- RS2 = Source Register 2
- Immediate = 6-bit immediate value
- Opcode = Instruction Opcode

---

## Execution Flow

```
Start

↓

Fetch instruction

↓

Decode operands

↓

Execute ALU operation

↓

Access Memory (if required)

↓

Write result back

↓

Next Instruction
```

---

## Project Structure

```
src/
│
├── DesignTop.v
├── Control_unit.v
├── program_counter.v
├── instruction_memory.v
├── data_memory.v
├── register_file.v
└── alu.v

memory/
├── Instruction_memory.txt
└── data_memory.txt
```

---

## Tools Used

- Verilog HDL
- Xilinx Vivado
- RTL Simulation

---

## Learning Outcomes

This project helped in understanding:

- Processor Design
- RTL Design
- Verilog HDL
- Finite State Machines
- Register File Design
- ALU Design
- Memory Interface
- Multi-cycle CPU Architecture
- Computer Organization
- Digital Logic Design

---

## Future Improvements

- Pipeline Architecture
- Branch Instructions
- Jump Instructions
- Status Flags (Zero, Carry, Overflow)
- Interrupt Support
- Larger Register File
- Expanded Instruction Set
- FPGA Implementation
- UART Debugging
- Assembly Compiler

---

## Author

**Muhammad Ali**

BS Embedded Systems

Feel free to contribute, open issues, or suggest improvements.

# Custom 32-bit Multi-Cycle CPU Design

## Overview
This project implements a custom 32-bit multi-cycle CPU in Verilog with a comprehensive instruction set. The CPU supports arithmetic, logical, memory access, and conditional branch instructions. It uses a finite state machine (FSM) based control unit to manage instruction fetch, decode, execution, and PC update over multiple clock cycles.

## Features
- **32-bit instruction width** with defined instruction fields (opcode, source/destination registers, immediate mode, etc.)
- Supports a variety of instructions:
  - Arithmetic operations: `mov`, `add`, `sub`, `mul`
  - Logical operations: `and`, `or`, `xor`, `xnor`, `nand`, `nor`, `not`, `ror`
  - Memory operations: load and store from/to data memory
  - Control flow: jump and conditional jumps based on flags (carry, zero, sign, overflow)
  - Halt instruction to stop CPU execution
- Multi-cycle execution controlled by an FSM with defined states:
  - Instruction fetch
  - Instruction decode and execution
  - PC update and branching
  - Halt detection
- General Purpose Register file (32 registers, 16-bit each)
- Special register to hold the upper 16 bits of multiplication results
- Condition flags (carry, zero, overflow, sign) updated after relevant instructions
- Separate program memory (instruction memory) and data memory blocks

## Architecture
- **Instruction Register (IR):** Holds the current instruction being executed
- **General Purpose Registers (GPR):** 32 registers, each 16-bit wide
- **Special Register (SGPR):** Holds the most significant bits of multiplication results
- **Finite State Machine (FSM):** Controls the CPU operation phases
- **Memory:** Separate instruction memory and data memory, each with 16 entries
- **Condition Flags:** Updated dynamically after arithmetic/logical operations for branching decisions

## Instruction Format


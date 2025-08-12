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

31:27	26:22	21:17	16	15:11	10:0 (unused or immediate)
opcode	rdst	rsrc1	imm	rsrc2	immediate / unused


## Usage
- Load the instruction memory from `inst_data.mem` (binary format)
- The CPU executes instructions sequentially or branches based on condition flags
- The CPU halts execution upon receiving the `halt` instruction
- Input data can be supplied via `din` and output read from `dout`

## Files
- `top.v`: Main CPU module including FSM, register file, ALU operations, and memory interfaces
- `inst_data.mem`: Binary file containing machine instructions for the CPU (user-defined)

## Simulation
- Simulate using any Verilog simulator (Icarus Verilog, ModelSim, etc.)
- Clock and reset signals control CPU operation
- Monitor `dout` for data output and internal signals for debugging

## Future Improvements
- Extend instruction set with floating point or SIMD operations
- Add pipeline stages for performance improvements
- Implement interrupt handling and I/O peripherals
- Expand memory size and addressable space

## Author
Bikash Kumar Mishra

## License
This project is released under the MIT License.


# 🔍 RISC-V Search-and-Replace Processor  
**Single-Cycle RISC-V Processor Implementation with Memory Replacement Algorithm**

## 📚 Overview

This project implements a single-cycle RISC-V processor in Verilog and demonstrates its operation by executing a search-and-replace algorithm on a memory array. The algorithm scans a 100-element memory array, identifies all occurrences of a specific target value (`0x14`), replaces them with a new value (`0xFEEDFEED`), and tracks the number of replacements made.

> 🔧 Designed and tested by Group 4 – EE326 (Computer Organization) Project, IIT Mandi

---

## 🧠 Key Features

- 🧮 Implements a **search-and-replace algorithm** using RISC-V instructions
- 🛠️ Custom **single-cycle processor** written in Verilog
- 📦 Instruction & Data memory modules created from scratch
- 🔁 Handles memory reads/writes, control flow, conditional branching
- ✅ Verified through **Icarus Verilog simulation** and waveform analysis

---

## 🧱 System Architecture

- **Memory Layout**
  - `Address 0`: Array size (N = 100)
  - `Addresses 1–100`: Array elements
  - `Address 101`: Target value (`0x14`)
  - `Address 102`: Replacement value (`0xFEEDFEED`)
  - `Address 103`: Replacement counter (result)

- **Register Allocation**
  - `x5`: Loop index  
  - `x6`: Replacement counter  
  - `x7`: Array size  
  - `x8`: Target value  
  - `x9`: Replacement value  
  - `x11`: Memory address offset  

- **Modules Implemented**
  - `Single_Cycle_Top.v`, `Core_Datapath.v`, `Control_Unit.v`, `ALU.v`
  - `Instruction_Memory.v`, `Data_Memory.v`, `Register_File.v`

---

## 💻 Technologies Used

- Verilog HDL  
- Icarus Verilog (Simulation)  
- GTKWave (Waveform viewing)  
- Bash scripting for compilation  
- C for algorithm prototyping  

---

## 📊 Results

| ✅ Action                     | 🧠 Outcome                      |
|------------------------------|-------------------------------|
| Replacements Made            | 7 occurrences of `0x14` found |
| Final Replacement Counter    | Stored at `mem[103] = 0x07`   |
| Execution Cycles (Est.)      | ~1110 (for N = 100)           |
| Instruction Memory Footprint | 84 bytes                      |
| Data Memory Footprint        | 416 bytes                     |

---

## 🧪 How to Run

1. **Simulate in Icarus Verilog**

```bash
iverilog -o riscv_sim testbench.v \
  Single_Cycle_Top.v Core_Datapath.v Control_Unit.v \
  ALU.v Register_File.v Instruction_Memory.v Data_Memory.v
vvp riscv_sim


2. **Expected Output**
Target values replaced by 0xFEEDFEED
mem[103] = 7 (number of replacements)

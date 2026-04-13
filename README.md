# 8T SRAM Based Circuit For Compute In Memory (CIM) Applications

## Overview
This project implements an **8T SRAM based Circuit for Compute In Memory (CIM) Applications** in **45nm CMOS technology**, enabling **Multiply-Accumulate (MAC)** operations and **logic computation directly within memory**.

The design reduces the **Von Neumann bottleneck** by minimizing data transfer between processor and memory, enabling **faster and more energy-efficient computation**.

---

## Key Features

- 8T SRAM cell with **decoupled read/write paths**
- **In-memory MAC computation** using RBL discharge
- **Voltage comparator-based ADC**
- **3-bit Flash ADC thermometer code to binary code encoder**
- Logic operations derived from MAC (AND, OR, XOR, NAND, NOR, XNOR)
- Fully simulated in **Cadence Virtuoso (45nm CMOS)**

---


### Steps:
1. **Precharge Phase**
   - RBL is charged to VDD

2. **Evaluation Phase**
   - RWL activates selected rows
   - Cells storing '1' discharge RBL

3. **MAC Operation**
   - RBL voltage drop ∝ number of active cells

4. **Analog to Digital Conversion**
   - 8 comparators compare RBL with reference voltages

5. **Encoding**
   - Comparator outputs converted to **3-bit digital output**

---

## Architecture

![1x8 CIM Array](8T%20SRAM%20based%20Circuit%20for%20Compute%20In%20Memory%20Application/Images/1x8_CIM_Array.png)

![8T SRAM Cell](8T%20SRAM%20Based%20Circuit%20For%20Compute%20In%20Memory%20Application/Images/8T_SRAM_Cell_schematic.png)


---

## MAC Encoding

| Active Cells | MAC Count | Output (3-bit) |
|-------------|----------|----------------|
| 1 | 1 | 000 |
| 2 | 2 | 001 |
| 3 | 3 | 010 |
| 4 | 4 | 011 |
| 5 | 5 | 100 |
| 6 | 6 | 101 |
| 7 | 7 | 110 |
| 8 | 8 | 111 |

---

## Logic from MAC

| Operation | Condition |
|----------|----------|
| AND | MAC = 2 |
| OR | MAC ≥ 1 |
| XOR | MAC = 1 |
| NAND | NOT(AND) |
| NOR | MAC = 0 |
| XNOR | NOT(XOR) |

---

## Key Components

### 🔹 8T SRAM Cell
- Stable read operation
- Decoupled read/write paths

### 🔹 Comparator Bank
- 8 parallel voltage comparators
- Converts analog RBL to digital levels

### 🔹 Encoder
- Converts comparator output → 3-bit value

### 🔹 Logic Block
- Maps MAC count to logic functions

---

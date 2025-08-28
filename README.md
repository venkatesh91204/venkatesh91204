## Vending Machine Controller – UVM Verification

📌 Project Overview

This project implements the **verification environment for a Vending Machine Controller IP** using **SystemVerilog and UVM (Universal Verification Methodology)**. The DUT supports configurable items, multiple currency inputs, and dispensing logic.

The verification ensures functional correctness, timing accuracy, configurability, and compliance with the design specification.

🛠 Design Specification (DUT Highlights)

* Operates at **100 MHz system clock**
* Supports up to **1024 items**
* Accepts currency denominations: **5, 10, 20, 50, 100 INR**
* **APB-based configuration interface** (50 MHz)
* Dispense logic with **change calculation** and **latency < 10 cycles**
* Handles invalid inputs: unsupported currency, empty stock, invalid item selection

  <img width="292" height="542" alt="image" src="https://github.com/user-attachments/assets/b6facf99-c88a-46e3-9c71-0da1aeab27a5" />


🔎 Verification Strategy

* **Methodology**: UVM (Universal Verification Methodology)
* **Stimulus**: Directed + Constrained Random Sequences
* **Environment Components**:

  * **APB Agent** – Configures item values and stock
  * **Currency Agent** – Injects valid/invalid currency inputs (focus area)
  * **Item Agent** – Generates item selection requests
  * **Dispense Agent** – Passive monitor for dispense outputs
  * **Scoreboard + Reference Model** – Self-checking verification
* **Coverage**: Functional + Code coverage for sign-off

📂 Project Structure

```
.
├── tb_top.sv               # Testbench top module
├── interfaces/             # SystemVerilog interfaces
├── agents/                 
│   ├── currency_agent/      # Driver, Sequencer, Monitor (focus area)
│   ├── item_agent/
│   ├── cfg_agent/
│   └── dispense_agent/
├── sequences/              # Directed + Random sequences
├── scoreboard/             # Scoreboard implementation
├── ref_model/              # Reference model
└── tests/                  # Testcases (currency_test, config_test, etc.)
```

✅ Test Scenarios Implemented

* **Reset tests** – DUT reset behavior
* **Configuration tests** – Item setup, read/write validation, edge cases
* **Operation tests** – Exact payment, overpayment (with change), underpayment, unsupported currency, zero stock, invalid item selection, randomized operations
* **Timing checks** – Latency and one-output-per-transaction validation
* **Stress tests** – Long-term random operations with resets and noise

👨‍💻 Contribution

Worked on the **entire verification environment**, with **major contribution on the Currency Agent**:

* Designed **sequencer, driver, monitor** for currency interface
* Developed directed + random sequences for multiple payment scenarios
* Integrated analysis ports with scoreboard and reference model
* Debugged key UVM issues (virtual interface binding, redundant classes, connectivity)


For Reference EDA playground Link: https://edaplayground.com/x/6rrw



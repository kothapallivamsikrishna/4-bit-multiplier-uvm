# 4-bit Multiplier Verification using UVM

This repository contains the design and verification of a 4-bit combinational multiplier. While the DUT itself uses a simple behavioral model (`assign y = a * b;`), the primary focus of this project is to demonstrate a robust, constrained-random UVM environment for verifying arithmetic logic.

---

### Project Overview

This project showcases the verification of a fundamental arithmetic block. The emphasis is not on a complex multiplier algorithm (like Dadda or Wallace Tree) but on building a reusable and self-checking UVM testbench that can thoroughly validate the DUT's functionality.

-   **DUT**: A 4-bit multiplier taking two 4-bit inputs and producing an 8-bit product.
-   **Verification Environment**: A complete UVM testbench that drives randomized input values and verifies the output against a golden reference model (the `*` operator) within the scoreboard.

---

### Folder Structure

-   `rtl/multiplier_design.v`: Contains the Verilog design for the 4-bit multiplier and its interface.
-   `tb/multiplier_tb.sv`: Contains the complete SystemVerilog/UVM code, including all UVM components and the top-level testbench module.

---

### Key Verification Components

-   **Constrained-Random Stimulus**: The sequence generates random 4-bit values for both operands (`a` and `b`) to ensure a wide range of multiplication scenarios are tested.
-   **Scoreboard with Golden Model**: The scoreboard receives the inputs and the DUT's output from the monitor. It calculates the expected product independently (`expected = a * b`) and compares it against the actual result, flagging any mismatches.

---

### How to Run

To run this simulation, you will need a simulator that supports SystemVerilog and UVM (e.g., Synopsys VCS, Cadence Xcelium, or Mentor Questa/ModelSim).

1.  Compile both `rtl/multiplier_design.v` and `tb/multiplier_tb.sv`.
2.  Ensure the UVM library is included in your compilation command.
3.  Set `tb` as the top-level module for simulation.
4.  Run the simulation. The test will automatically execute and report PASS/FAIL status in the log.

# Minimal Processor in SystemVerilog

## Project Description

This project implements a **minimal processor** on an FPGA using **SystemVerilog**. The circuit includes basic components for control, arithmetic, and memory, allowing functional testing on an FPGA running at 100 MHz.

---

## Main Components

1. **counter_32b** – 32-bit counter
   - Asynchronous reset (`rst_n`)  
   - Clock frequency selection (`sel_fpga`):
     - `sel_fpga = 1` → 1-second clock period (for FPGA testing)  
     - `sel_fpga = 0` → uses the unmodified clock frequency (`clk`)  
   - Base clock frequency `clk` = 100 MHz (pin F14 on FPGA)

2. **counter_3b** – 3-bit counter
   - Asynchronous reset (`rst_n`)

3. **mux2_1b** – 2-to-1 multiplexer, 1-bit wide

4. **mux2_4b** – 2-to-1 multiplexer, 4-bit wide

5. **ALU (Arithmetic Logic Unit)**
   - Performs arithmetic and logic operations based on the opcode  
   - Supports **addition and subtraction** with **Carry flag** generation  
   - **Zero flag** is set if the result is 0  

6. **ROM** – Read-only memory for program instructions

7. **register_2b** – 2-bit register
   - Synchronous reset (`rst_n`)

8. **RAM**
   - Multiport memory for processor registers
   - Allows simultaneous read from two locations
   - Asynchronous read

---

## Functionality

- Executes a set of instructions stored in ROM  
- Intermediate data and operation results are stored in RAM and registers  
- ALU generates **Carry** and **Zero** flags for arithmetic operations  
- The 32-bit counter can be used as a **timer or instruction counter**  
- FPGA test mode can be activated with `sel_fpga` to slow down the clock for observation  

---

## Special Requirements

- Fully implemented in **SystemVerilog**  
- FPGA compatible (Vivado) at 100 MHz  
- Asynchronous and synchronous resets per module specification  
- Multiport RAM for fast register access  
- FPGA test mode with 1 Hz clock for slow observation  

---


---

## How to Run

1. Open the project in **Vivado**  
2. Add the source files from the `src/` folder  
3. Configure constraints (`.xdc`) for the clock pin and LEDs if needed  
4. Compile and simulate using `top_module_tb.sv` to verify functionality  
5. Program the FPGA: set `sel_fpga = 1` for slow observation mode  

---

## License

This project is **open-source** and can be used or modified for educational purposes or experimentation.


## Project Structure


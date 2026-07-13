🧩 Verification of APB-Based Memory RTL

📘 Overview

This project implements a reusable UVM verification environment for an APB-based Memory RTL. The environment includes sequencer, driver, monitor, agent, environment, scoreboard, and functional coverage to verify memory read/write transactions and APB protocol behavior using constrained-random test scenarios.


File Architecture

+---docs
|       block_diagram.png
|       coverage.png
|       tb_architecture.png
|       terminal_output.png
|       uart_data_frame.png
|       wave_form.png
|
+---rtl
|       memory.sv
|       mem_if.sv
|
+---sim
|       Makefile
|
+---tb
|       env.sv
|       test_config.sv
|       mem_sb.sv
|       top.sv
|
+---test
|       tets_pkg.sv
|       tets.sv
|
+---Apb_side
        apb_agent.sv
        apb_config.sv
        apb_drv.sv
        apb_mon.sv
        sequence.sv
        apb_seqr.sv
        apb_xtn.sv

🧠 Memory Overview

The APB-based Memory is a simple memory module that communicates through the Advanced Peripheral Bus (APB) protocol. It supports read and write operations, allowing data to be stored and retrieved using APB control and address signals.

Basic Operation:

Write: Stores data into the specified memory address when the write enable signal is asserted.
Read: Retrieves data from the specified memory address during a read transaction.
APB Interface: Uses APB signals such as PADDR, PWDATA, PRDATA, PSEL, PENABLE, PWRITE, and PREADY for communication.

Applications:
On-chip data storage in SoCs
Register and configuration storage
Embedded system memory interfaces
Peripheral data buffering

Advantages:
Simple and low-complexity interface
Low power consumption
Easy integration with APB-based peripherals
Suitable for low-bandwidth applications

Drawbacks:
Designed for low-speed peripheral access and not suitable for high-performance data transfers.
Supports single data transfers only, with no burst transfer capability.
Limited scalability for applications requiring high memory bandwidth.
Performance depends on APB handshaking, making it slower than high-speed buses such as AHB or AXI.

🧱 Testbench Architecture

The UVM-based verification environment consists of the following components:

APB Agent containing a Sequencer, Driver, and Monitor
Environment (Env) integrating all verification components
Scoreboard for memory data comparison and functional checking
Functional Coverage to measure verification completeness
Constrained-Random Sequences for generating APB read and write transactions
Block Diagram

Testbench Architecture



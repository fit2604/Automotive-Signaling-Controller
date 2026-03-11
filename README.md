# Automotive-Signaling-Controller

This project implements a digital vehicle turn signal and hazard light controller on a Basys3 FPGA board using VHDL. The system uses a synchronous Finite State Machine (FSM) to manage dynamic lighting sequences, simulating modern automotive exterior lighting behavior.

Key Features
Sequential Turn Signals: Three-stage sequential lighting for both left and right directions (LAon -> LALBon -> LALBLCon).
Hazard Mode: A three-stage flashing sequence for emergency signaling (HAZARD1 through HAZARD3).
One-Touch Signaling: Short-pulse signals for quick lane changes (LEFT_UP_SIG, RIGHT_UP_SIG).
Frequency Division: Includes a clock divider to adapt the FPGA's high-frequency clock for human-visible LED transitions.

Technical Specifications
Hardware Platform: Xilinx Artix-7.
Development Environment: Vivado Design Suite v2024.2.
Design Language: VHDL-93.
Target Board: Digilent Basys3

File Structure
project_fit.xpr: The main Vivado project file that integrates all sources and settings.
fsm.vhd: The core RTL design containing the FSM logic and LED output mapping.
constr.xdc: The Xilinx Design Constraints file mapping the internal signals to physical switches, LEDs, and the system clock.
sim.vhd: A comprehensive testbench for functional verification through behavioral simulation.

Hardware I/O
MappingBased on the project's constr.xdc and fsm.vhd, the controls are mapped as follows:

Input(Switch) Function   Output (LEDs)

sw(0)--> Hazard Lights--> Center LEDs

sw(1)--> Left Signal--> LEDs 15 down to 10

sw(2)--> Right Signal--> LEDs 0 up to 5

sw(3)--> Left Quick Signal--> Full Left Bar

sw(4)--> Right Quick Signal--> Full Right Bar

btn(rst)--> System Reset--> All LEDs OFF


CONCLUSION

This design demonstrates a robust application of Hardware Description Language (HDL) in the automotive industry. By utilizing an FSM, the system ensures reliable state transitions and timing, essential for safety-critical vehicle signaling.

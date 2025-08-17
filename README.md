# RTL to GDSII Flow of a RISC-V Processor

This project details the end-to-end execution of a digital ASIC design flow, from Register-Transfer Level (RTL) to GDSII layout, for a RISC-V processor. The entire process was automated and executed using the open-source EDA tool **OpenLane**.

## Project Overview

The project demonstrates a complete digital backend flow, transforming a synthesizable Verilog RTL description of a RISC-V processor into a final, manufacturable chip layout (GDSII). This is a critical step in the ASIC design process, involving a series of complex and interconnected stages.

## Key Stages of the Flow

The project meticulously follows the standard ASIC design flow, with each stage leveraging a specific tool within the OpenLane framework:

### 1. **Synthesis**
The RTL code of the RISC-V processor is synthesized into a gate-level netlist. This process translates the high-level behavioral description into a technology-specific list of standard cells (e.g., AND, OR, flip-flops).

### 2. **Floorplanning**
In this stage, the overall chip layout is defined. The project involved:
-   Specifying the die area.
-   Placing the I/O pins.
-   Allocating space for the core logic.
-   Defining power and ground rings.

### 3. **Placement**
The synthesized standard cells are placed within the core area of the chip. This step is crucial for optimizing the design for timing and power. The goal is to place cells that communicate frequently close to each other to minimize wire length.

### 4. **Clock Tree Synthesis (CTS)**
-   **Tool:** TritonCTS
-   A dedicated clock network is designed and routed across the chip. The primary objective of CTS is to ensure that the clock signal arrives at all sequential elements (flip-flops) at the same time, thereby minimizing clock skew and jitter, which are critical for meeting timing requirements.

### 5. **Routing**
The final connections (wires) between all the standard cells are created. This stage involves:
-   **Global Routing:** Determining the general paths for the interconnections.
-   **Detailed Routing:** Laying down the exact wire tracks on the metal layers, ensuring no short circuits or design rule violations.

### 6. **Static Timing Analysis (STA)**
-   **Tool:** OpenSTA
-   After routing, a comprehensive timing analysis is performed on the design. This step verifies that the circuit meets all the timing constraints, such as setup and hold times, ensuring the chip will function correctly at its target frequency.

### 7. **Layout Generation (GDSII)**
The final, verified layout is generated in GDSII format. This is the industry-standard file format used for transferring chip layouts to a semiconductor foundry for fabrication.

## Tools Used

-   **OpenLane:** An open-source, automated RTL to GDSII flow. It orchestrates a suite of powerful EDA tools.
-   **TritonCTS:** An integrated tool within OpenLane for performing Clock Tree Synthesis.
-   **OpenSTA:** An open-source tool for performing Static Timing Analysis.
-   **Magic:** Used for final layout checks and GDSII generation.

## Conclusion

This project successfully demonstrates a complete digital backend flow, providing hands-on experience with the critical stages of ASIC design using an open-source toolchain. The generated GDSII is a testament to the successful execution of each stage, from floorplanning to final timing closure.

# PicoRV32-based SoC Design

This repository contains the design and implementation of a System-on-Chip (SoC) based on the PicoRV32 RISC-V CPU core. The SoC integrates various IPs, including memory, SPI memory interface, UART, and memory decoding logic. The design was implemented using the OpenLane2 toolchain and targets the SkyWater 130nm process node (PDK: `sky130A`).

## Project Overview

The SoC design includes the following key components:

- **PicoRV32 CPU**: A small, efficient, and open-source RISC-V CPU core.
- **Memory**: On-chip memory for data and instruction storage.
- **SPI Memory Interface**: Interface for external SPI flash memory.
- **Simple UART**: Serial communication interface for debugging and communication.
- **Memory Decoder**: Logic for address decoding and memory mapping.

The design was synthesized, placed, and routed using OpenLane2, and the final GDSII layout was generated for tape-out. Key steps in the design flow included **pin placement** and **macro placement**, which are essential for ensuring proper connectivity and optimal placement of large blocks in the SoC.

## Repository Structure

- `src/`: Contains the Verilog source files for the SoC design.
  - `picosoc.v`: Top-level Verilog module for the SoC.
- `verilog_blackbox/`: Contains blackbox Verilog files for external IPs.
- `lef/`: Contains LEF files for the IPs used in the design.
- `gds/`: Contains GDSII files for the IPs used in the design.
- `config.json`: Configuration file for OpenLane2.
- `macro.cfg`: Macro placement configuration file.
- `pin_order.cfg`: Pin order configuration file for the SoC.
- `picosoc.sdc`: Synopsys Design Constraints (SDC) file for timing constraints.

## Design Specifications

- **Clock Period**: 100 ns
- **Clock Port**: `clk`
- **Die Area**: 2600 μm x 1500 μm
- **Target Density**: 55%
- **Power Nets**: `vccd1` (VDD), `vssd1` (GND)

## Key Features

- **RISC-V ISA**: The SoC is based on the PicoRV32 CPU, which implements the RISC-V instruction set architecture.
- **On-Chip Memory**: Integrated memory for data and instruction storage.
- **SPI Flash Interface**: Support for external SPI flash memory.
- **UART Interface**: Simple UART for serial communication.
- **OpenLane2 Flow**: The design was implemented using the OpenLane2 open-source EDA toolchain.
- **Pin Placement**: Custom pin placement was performed to ensure proper connectivity and signal integrity.
- **Macro Placement**: Critical macros (e.g., CPU, memory, SPI, UART) were manually placed to optimize the layout and meet timing constraints.

## Pin Placement and Macro Placement

### Pin Placement
The pin placement for the SoC was carefully planned to ensure efficient routing and signal integrity. The pin order and configuration are defined in the `pin_order.cfg` file. Key considerations included:
- Grouping related signals (e.g., address, data, control) to minimize routing congestion.
- Placing power and ground pins strategically to ensure proper power distribution.

### Macro Placement
Macro placement is a critical step in SoC design, especially for large blocks like the CPU, memory, and peripherals. The macros were placed manually using the `macro.cfg` file, which specifies the locations of each macro in the die area. Key considerations included:
- Minimizing the distance between interconnected macros to reduce wirelength and improve timing.
- Ensuring that macros are placed in a way that avoids routing congestion and meets density targets.

## Getting Started

### Prerequisites

- OpenLane2 installed and configured.
- SkyWater 130nm PDK (`sky130A`) set up.

### Running the Design

1. Clone this repository:
   ```bash
   git clone https://github.com/devadutt-github/picorv32-soc.git
   cd picorv32-soc

### Results

Openlane GUI view
![picorvSoC](https://github.com/user-attachments/assets/c2f69166-e38f-484f-9910-2a64f062f647)


Klayout GDS view
![picorvSoC_klayout_gds](https://github.com/user-attachments/assets/f1a2a0fa-f93d-4f1b-ae91-10cf193b0843)

### Acknowledgements

This project would not have been possible without the following open-source tools, resources, and guidance:

Mehmet Burak Aykınar: The macro placement and pin configuration strategies were inspired by the article RISC-V Based SoC Design with Open-Source OpenLane IC Design Tool by Mehmet Burak Aykınar.

PicoRV32: The PicoRV32 CPU core, developed by Clifford Wolf, provided the foundation for this SoC design.

OpenLane2: The OpenLane2 toolchain was used for synthesis, placement, and routing.

SkyWater PDK: The SkyWater 130nm open-source PDK enabled the fabrication-ready design of this SoC.

Klayout: Used for GDSII visualization and verification.

We are grateful to the open-source community and the authors of these resources for their contributions and support.



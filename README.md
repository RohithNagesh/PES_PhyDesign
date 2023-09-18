# ADVANCED PHYSICAL DESIGN USING OPENLANE/SKY130
# Course Content
## DAY 1
## Inception of open-source EDA, OpenLANE and Sky130 PDK
+ [Introduction](#introduction)
+ [SoC design and OpenLANE](#soc-design-and-openlane)
+ [Open-source EDA tools](#open-source-eda-tools)
## DAY 2
## Floor planning and introduction to library cells
+ [Chip Floor planning considerations](#chip-floor-planning-considerations)
+ [Library Binding and Placement](#library-binding-and-placement)
+ [Cell design and characterization flows](#cell-design-and-characterization-flows)
+ [General timing characterization parameters](#general-timing-characterization-parameters)
## DAY 3
## Design library cell using Magic Layout and ngspice characterization
+ [Labs for CMOS inverter ngspice simulations](#labs-for-cmos-inverter-ngspice-simulations)
+ [Inception of Layout and CMOS fabrication process](#inception-of-layout-and-cmos-fabrication-process)
+ [Sky130 Tech File Labs](#sky130-tech-file-labs)
## DAY 4
## Pre-layout timing analysis and importance of good clock tree
+ [Timing modelling using delay tables](#timing-modelling-using-delay-tables)
+ [Timing analysis with ideal clocks using openSTA](#timing-analysis-with-ideal-clocks-using-opensta)
+ [Clock tree synthesis TritonCTS and signal integrity](#clock-tree-synthesis-tritoncts-and-signal-integrity)
+ [Timing analysis with real clocks using openSTA](#timing-analysis-with-real-clocks-using-opensta)
## DAY 5
## Final steps for RTL2GDS using tritonRoute and openSTA
+ [Routing and design rule check (DRC)](#routing-and-design-rule-check-/(drc)/)
+ [Power Distribution Network and routing](#power-distribution-network-and-routing)
+ [TritonRoute Features](#tritonroute-features)
***

# Day-1
# Inception of open-source EDA, OpenLANE and Sky130 PDK
## Introduction  
### Introduction to QFN-48 Package, Chip, Pads, Core, Die and IPs

- **Arduino Board:** An Arduino board is a fundamental component of the open-source Arduino electronics platform. It typically includes a microcontroller, digital and analog input/output pins, a USB interface for programming, and power supply options. Arduino boards are versatile tools used for creating electronic projects, and they come in various models with different features. They are popular among both beginners and experienced makers due to their ease of use and a vast online community that provides resources and tutorials for building interactive electronic projects.

- **QFN-48 Package:** QFN-48 is an integrated circuit (IC) package type known as Quad Flat No-Leads 48. It is commonly used in electronics for housing ICs and microcontrollers. The **48** in its name signifies that it has 48 pins or electrical connections on its bottom surface for connecting to a circuit board. This package's popularity stems from its compact size, surface-mount capability, and efficiency in modern electronic assembly processes.

- **Chip:** A chip in electronics is a small semiconductor device typically made of silicon, housing integrated circuits. These chips can have various functions, including microprocessors for computation, memory chips for data storage, and sensors for detecting physical properties. For instance, a microprocessor chip serves as the central processing unit (CPU) or **brain** of a computer, managing instructions and calculations. Chips are essential components in electronic devices, enabling their functionality and powering various technological applications.

- **Pads:** Pads on a semiconductor chip's surface are designated metalized areas with specific patterns, crucial for making electrical connections. They serve as the interface between the chip's internal circuitry and the external world, enabling connectivity with other components like printed circuit boards (PCBs). These pads play a vital role in facilitating the chip's functionality in electronic devices and systems.

- **Die:** A die in semiconductor manufacturing refers to an individual, self-contained integrated circuit (IC) or microchip on a semiconductor wafer. Multiple dies are fabricated on a single wafer simultaneously during manufacturing and are later separated into individual units. These individual dies are then packaged into integrated circuits for use in various electronic devices.

- **Core:** CPU cores are independent processing units within a microchip, chips can contain one or multiple CPU cores, and having multiple cores on a single chip is known as multi-core processing. Multi-core processors allow for parallel task execution, improving overall performance in computing devices.

- **IPs:** IPs (Intellectual Property or IP Blocks) are pre-designed and pre-verified functional components used in semiconductor chip design. They encompass processors, memory controllers, communication interfaces, and specialized hardware accelerators. Semiconductor companies license IPs from third-party providers, saving time and resources. IPs enhance chip reliability and efficiency, allowing companies to focus on customizing unique chip features.

- **Foundry:** A foundry, also known as a semiconductor fabrication plant or fab, is a specialized facility for manufacturing semiconductor devices and integrated circuits (ICs). Foundries are equipped with advanced equipment and cleanroom environments for producing semiconductor components on silicon wafers. They typically work on behalf of semiconductor design companies that send their chip designs to the foundry for mass production. This foundry model allows design companies to concentrate on innovation while leveraging the manufacturing expertise of the foundry for efficient and cost-effective chip production.

- **Macros:** Macros in semiconductor chip design are pre-designed and sizeable logic or functional circuit blocks that offer standardized, reusable, and well-optimized functionality. They are especially valuable for implementing complex and commonly used operations in chip designs. Macros save time and effort for chip designers, ensuring design consistency and efficient implementation of complex functions. They can be customized for specific tasks like data processing, graphics rendering, or signal processing, enabling the integration of high-performance functionality without the need to build everything from the ground up.

### Introduction to RISC-V 

- **ISA(Instruction Set Architecture):** An ISA defines the set of instructions that a microprocessor or CPU understands and can execute. RISC-V provides a set of instructions designed to be simple, efficient, and flexible.

- **RISC-V (Reduced Instruction Set Computing - Five):** RISC-V is an open and royalty-free instruction set architecture for designing microprocessors and CPUs. It emphasizes simplicity, modularity, and versatility, allowing users to create custom processors for a wide range of applications. RISC-V has gained significant industry and academic adoption due to its open nature and growing ecosystem.

### From Software Applications to Hardware 

- **Apps:** Application software, often referred to simply as **applications** or **apps**, is a type of computer software that is designed to perform specific tasks or functions for end-users.
  
- **System software:** System software refers to a category of computer software that acts as an intermediary between the hardware components of a computer system and the user-facing application software. It provides essential services, manages hardware resources, and enables the execution of application programs. System software plays a critical role in maintaining the overall functionality, security, and performance of a computer system.'
- **Operating System:** The operating system is a fundamental piece of software that manages hardware resources and provides various services for both users and application programs. It controls tasks such as memory management, process scheduling, file system management, and user interface interaction. Examples of operating systems include Microsoft Windows, macOS, Linux, and Android.
- **Compiler:** A compiler is a type of software tool that translates high-level programming code written by developers into assembly-level language.
- **Assembler:** An assembler is a software tool that translates assembly language code into machine code or binary code that can be directly executed by a computer's processor.
- **RTL:** RTL serves as an abstraction level in the design process that represents the behavior of a digital circuit in terms of registers and the operations that transfer data between them.
- **Hardware:** Hardware refers to the physical components of a computer system or any electronic device. It encompasses all the tangible parts that make up a computing or electronic device and enable it to perform various tasks.


## SoC design and OpenLANE
### Introduction to all Components of Open-Source Digital ASIC Design   

**PDK**
+ It stands for **Process Design Kit**.
+  It is a collection of files, models, documentation, and tools that are provided by semiconductor foundries to assist integrated circuit (IC) designers in creating and verifying their designs for a specific semiconductor manufacturing process.
+  PDKs are essential for the design and development of semiconductor chips because they provide the necessary information and resources for designers to create circuits that are compatible with the foundry's fabrication process.

**EDA Tools**
+ EDA (Electronic Design Automation) tools are a set of software applications and tools used by electronics engineers and integrated circuit (IC) designers to design, simulate, verify, and analyze electronic circuits and systems.
+ These tools are essential for designing complex electronic devices, ranging from simple integrated circuits to advanced microprocessors and systems-on-chip (SoCs).
<p align="center">
  <img width="500" alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/42cc68bb-4582-4e15-a96f-9b67f0e601e7">
</p>

**130nm**
+ It refers to a semiconductor manufacturing process technology node, which represents the minimum feature size or transistor gate length in that technology.
+ In semiconductor manufacturing, the feature size is a critical metric because it determines the size and performance characteristics of the transistors and other components that make up integrated circuits (ICs).

## Simplified RTL2GDS Flow 

**RTL to GDSII**
<p align="center">
<img width="500" alt="image" src= "https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/9b483c18-0a1e-4121-8a6c-8b6f29e94104">
</p>

+ **Synthesis**
  -  It refers to the process of converting a high-level hardware description into a gate-level representation that can be implemented on a specific hardware technology or semiconductor manufacturing process.
 
+ **Floor and Power Planning**
  - **Chip floor planning** is the process of partitioning the chip die between different system building blocks and place the I/O pads.
  - **Macro floor planning**, also known as block-level floor planning, is a specific aspect of chip floor planning that focuses on the arrangement and organization of large functional blocks or macros within an integrated circuit (IC) design. 
  - **Power planning** also known as power distribution network (PDN) design, focuses on the distribution and management of power and ground connections within the chip. It ensures that all components receive stable power supplies and that power is efficiently distributed throughout the chip.
 
+ **Placment**
  - It refers to the process of determining the physical locations of individual components, such as logic gates, flip-flops, memory cells, and other elements, on the semiconductor die or chip.
  - **Global placement** involves determining approximate positions or locations for major functional blocks, macros, and components on the semiconductor die or chip.
  - **Detailed placement** also known as fine-grained placement, is a critical step in the physical design of integrated circuits (ICs) that follows global placement.
During the detailed placement phase, the positions of individual components, such as logic gates, flip-flops, and memory cells, are determined with high precision within the semiconductor die or chip.

+ **Clock Tree Synthesis**
  - It involves the generation and optimization of a hierarchical tree-like network of clock distribution that ensures synchronized clock signals are delivered efficiently to all flip-flops and other clocked elements within the chip.
  - The primary objectives of clock tree synthesis are to minimize clock skew, reduce clock routing congestion, and meet strict timing requirements.

+ **Routing**
  - It is responsible for establishing the electrical connections (wires or metal traces) that allow signals to flow between different parts of the chip.
  - **Global routing**, also known as channel routing, is the first phase of routing. It determines the general paths for wires that connect different components or blocks on the chip. Global routers aim to minimize the total wirelength while adhering to design rules and constraints.
  - Once the general paths are defined in global routing, detailed routing comes next.
  - **Detailed routing** focuses on individual nets (connections) and determines the specific paths and wires that connect the pins of components or gates. It also resolves any conflicts or overlaps between wires.

+ **Sign-Off**
  - It signifies the point at which a specific design step or aspect has been completed, reviewed, and verified to meet certain criteria or standards.
  - **Physical Verification** sign-off phase covers a range of physical design verification checks, including DRC, LVS, and other manufacturing-oriented checks. It ensures that the design is ready for manufacturing and fabrication.
  - **Timing verification** sign-off specifically focuses on verifying that the chip meets the required timing constraints, such as setup and hold times, clock-to-q delays, and maximum clock frequency. This involves detailed timing analysis and simulation to ensure that the design operates correctly at the specified clock frequencies.

### Introduction to OpenLane and Strive Chipsets 

+ **OpenLane**
  - OpenLANE is an opensource tool or flow used for opensource tape-outs.
  - The OpenLANE flow comprises a variety of tools such as Yosys, ABC, OpenSTA, Fault, OpenROAD app, Netgen and Magic which are used to harden chips and macros, i.e. generate final GDSII from the design RTL. The primary goal of OpenLANE is to produce clean GDSII with no human intervention.
  -  OpenLANE has been tuned to function for the Google-Skywater130 Opensource Process Design Kit.

+ **Strive Chipsets**
<p align="center">
  <img width="250" alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/e03187bf-95fd-4418-85a8-0963320b1dad">
</p>

### Introduction to OpenLane Detailed ASIC Design Flow 

<p align="center">
  <img width="600" alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/7be28c34-a1bf-4921-a864-52952fc28953">
</p>

+ **OpenLane Regression Testing**
 - Regression testing in the context of OpenLane refers to the process of running a set of predefined test cases or scripts on the OpenLane design automation framework to ensure that recent changes or updates to the framework have not introduced new bugs or regressions.

+ **Design for Test(DFT)**
  - Scan Insertion
  - Automatic Test Pattern Generation(ATPG)
  - Test Patterns Compaction
  - Fault Coverage
  - Fault Simulation
  
+ **Physical Implementation** (automated PnR(Place and Route)) (OpenRoad)
  - Floor/Power Planning
  - End Decoupling Capacitors and Tap cells insertion
  - Placement : Global and Detailed
  - Post placmnet optimisation
  - Clock Tree synthesis
  - Routing : Global and Detailed

 + **Logic Equivalence Check** (yosys)
   - Everytime the netlist is modified, verification must be performed.
   - LEC is used to formally confirm that the function did not change after modifying the netlist.
  
+ **Dealing with antenna rules violations**
  - When a metal wire segment is fabricated, it can act as an antenna.
  - Reactive ion etching causes charge to accumulate on the wire.
  - Transistor gates can be damaged during fabrication.
  - Two solutions:
    + Bridging attaches a higher layer intermediary.
    + Add antenna diode cell to leak away charges.
  - We took a preventive approach:
    + Add a fake antenna diode next to every cell input after placement.
    + Run the antenna check(**Magic**) on the routed layout
    + If the checker reports a violation on the cell input pin, replace the fake diode cell by a real one.
   
+ **Static Timing Analysis**
  - Static Timing Analysis (STA) is a critical step in the design and verification of integrated circuits (ICs) and other digital systems.
  - It is used to ensure that a digital design meets its required timing constraints and operates correctly within a given clock frequency.
  - STA is performed during the physical design phase of chip development and is crucial for assessing and optimizing the performance and reliability of digital systems.
 
+ **Physical Verification**
  - **LVS (Layout vs Schematic)** is a process that ensures that the physical layout of a chip or circuit matches its intended logical or schematic representation.
  - **DRC (Design Rules Checking)** is a process that ensures that the layout of a chip or circuit adheres to the specific design rules and constraints defined by the semiconductor manufacturing process. 
  - **Magic** is used for design rules checking and SPICE extraction from Layout.
  - **Magic** and **Netgen** are used for LVS


## Open-Source EDA Tools
### OpenLane Directory Structure 

PDK used in this workshop is Skywater 130nm PDK and OpenLane is built around this PDK.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/d74d57f7-520d-47ea-9771-d9b1cd708e80)

**skywater-pdk** contains all the PDK related files.

**open_pdks** contains all the scripts and files that convert these foundry level PDKS to be compatible with the open-source EDA tools

**sky130A** is made compatible with our open-source environment.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/6007280a-abca-43d3-a80f-d3d716e9ee5c)

**libs.ref** seems specific to technology.

**libs.tech** seems specific to the tool.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/f01b996e-0561-4ca9-b210-ba34e66b2b84)

**sky130_fd_sc_hd** has all the technology files.
### Design Preparation Step 
To invoke OpenLane

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/1be3ac80-5f19-49e2-8d90-fb3be8973885)

Under **Designs** folder, we are going to use **picorv32a**.

**src** files contains verilog and sdc file.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/f5433821-94c2-4729-8027-18dda8d2a583)

We are going to prepare the design `prep -design picorv32a`.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/5eeebfb8-73a0-4597-92bd-a3b5d5d0dc82)

After Design Preparation, we will run the Synthesis:
- `run_synthesis` command use to run the synthesis
- Yosys-Perform RTL Simulation abc-It performs technology mapping and the netlist is created. Open STA-Perform static timing analysis after synthesis.
- This will execute both yosys and abc pass will be done

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/e6d173a7-b604-4197-ac70-87b5cbc59a39)

### Characterize Synthesis Results 
- Number of D Flip-Flops = 1613
- Number of Cells = 14876
clock ratio = 1613/14876=0.1084 or 10.84 percent

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/4c13d10d-befd-4d3c-8c72-4ff6a1aaef50)

# Day-2
# Floor planning and introduction to library cells
## Chip Floor planning considerations
### Utilisation Factor and Aspect Ratio 
**Utilization factor:** Utilization factor is a measure of how efficiently a system or component is being used, often expressed as a ratio or percentage. It is relevant in areas such as lighting design, heat exchangers, and telecommunications.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/6c0d4743-4852-4cae-9064-9d6f3f874a1f)

**Aspect ratio** Aspect ratio is a dimensionless quantity describing the proportion of an object's width to its height. It is used in fields like architecture, aerodynamics, and screen display ratios.


### Pre-placed Cells 
Pre-placed cells (Pcells) are custom-designed components in integrated circuit layouts, manually positioned and connected by designers. They are used for specialized functions that can't be efficiently handled by standard cells alone. Pcells are strategically placed to optimize IC performance, often in mixed-signal designs, and require careful manual placement and routing. While they offer precise control, using Pcells adds complexity to the design process, necessitating a balance between manual control and the use of electronic design automation (EDA) tools to meet specific design constraints.

### De-coupling Capacitors  

Decoupling capacitors, often called decaps, are vital electronic components used to stabilize and filter voltage in electronic circuits, particularly integrated circuits (ICs) and printed circuit boards (PCBs). They prevent voltage fluctuations and high-frequency noise by acting as short-term energy reservoirs and are strategically placed near IC power pins. The choice of capacitor type and capacitance value depends on specific circuit requirements and noise frequencies. Decoupling capacitors play a critical role in ensuring reliable and noise-free operation of sensitive electronic components.

### Power Planning  
+ Power planning refers to the process of strategically managing and distributing electrical power within a circuit or system to ensure reliable and efficient operation.
+ Effective power planning is essential in modern electronics to meet performance, power consumption, and thermal constraints. 

### Pin Placement and Logical Cell Placement Blockage 

**Pin Placment**
+ Pin placement, also known as I/O (Input/Output) placement, is a crucial step in the physical design of an integrated circuit (IC).
+ It involves determining the locations and positions of input and output pins on the chip's package or die.
+ Proper pin placement is essential to ensure that the IC can interface with the external world effectively, meet performance requirements, and adhere to manufacturability constraints.

**Logical Cell Placement Blockage**
+ Logical cell placement blockage, often referred to as blockage constraints or blockage regions, is a concept used in the physical design of integrated circuits (ICs).
+ Blockage constraints are used to restrict or reserve specific areas of the chip's layout for various purposes, such as accommodating specialized circuitry, ensuring signal integrity, or meeting manufacturing requirements.

### Floorplan using OpenLane 
`run_floorplan` command use to run the floorplan

Width of the die=660685/1000=660.685 micron Heigth of the Die=671405/1000=671.405 micron Area=Width*Height=443587.212 square microns

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/44e92867-a621-43aa-84d1-dc903f90ef46)

## Review Floorplan Layout in Magic 
  
 ```
 magic -T /home/rohith_nagesh/ASIC/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/94d8ea42-ed3d-432e-b93c-7f36bd11b9b0)

## Library Binding and Placement
### Netlist Binding and Initial Place Design 

**Netlist Binding**
+ Netlist binding is a crucial step in the process of transforming a high-level design description into a representation that can be physically implemented on a chip or printed circuit board (PCB).
+ This step involves associating the logical components and connections described in the netlist with physical components, such as gates, flip-flops, and interconnections, that will be used in the actual implementation.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/5835a2c1-4ce5-4841-af34-5f7457f53f9e)

## Optimise Placement using Estimated Wire-Length and Capacitance 

+ We need to estimate the wire length and capacitance, and based on that insert repeaters.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/a306271b-a1f5-4927-9a6e-2963e5d932c5)

### Need for Libraries and Characterization 

**Library Characterisation**
+ Library characterization is the process of creating a comprehensive and accurate characterization model for a library of standard cells.
+ These standard cells serve as the fundamental building blocks for designing digital circuits.
+ The goal of library characterization is to provide designers with essential information about how these cells behave under various operating conditions, allowing for accurate timing analysis and optimization.

## Congestion aware Placement using RePLAce 

`run_placement` command use to run the placement
<p align="center">
<img alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/900d1552-cc1b-4fd2-942d-b02fe3d9322f">
</p>


```
magic -T /home/rohith_nagesh/ASIC/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/b0690855-a828-4ab7-b5f8-aeda6e656bbf)

## Cell Design and Characterization Flows
### Inputs for Cell Design Flow 

**Cell Design Flow**
<p align="center">
  <img img width="500" alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/63537911-1b47-4eca-b59a-9275f026d519">
</p>

**Inputs:**
+ PDKs (Process Design Kits):
  - PDKs are essential resources provided by semiconductor foundries.
  - They contain information about the fabrication process, including the available semiconductor technology, transistor models, and design rules.
  - PDKs enable IC designers to create layouts and perform simulations that are compatible with the specific manufacturing process of the foundry.

+ DRC (Design Rule Checking) and LVS (Layout vs. Schematic) Rules:
  - DRC rules are a set of guidelines that ensure that the physical layout of a chip adheres to the foundry's manufacturing process requirements.
  - LVS rules ensure that the electrical characteristics of the layout match the intended schematic design.
  - Both DRC and LVS checks are crucial for identifying and rectifying design errors and ensuring manufacturability and functionality.

+ SPICE Models:
  - SPICE (Simulation Program with Integrated Circuit Emphasis) models are mathematical representations of electronic components (transistors, resistors, capacitors, etc.).
  - They describe how these components behave electrically under different conditions.
  - SPICE models are used for circuit simulation to analyze the performance of an IC design and predict its behavior.

+ Library:
  - A library in IC design contains a collection of pre-designed, standardized components (e.g., logic gates, flip-flops, analog blocks) that can be used to build more complex circuits.
  - Libraries save time and effort by providing readily available building blocks for designing ICs.
  - Libraries often include SPICE models for each component, allowing for accurate simulation.

+ User-Defined Specifications:
  - User-defined specifications are custom requirements and constraints set by the IC designer for a specific design project.
  - These specifications can include performance goals (e.g., speed, power consumption), design constraints (e.g., area, power budget), and unique functionality requirements.
  - User-defined specifications guide the entire IC design process, influencing choices made in terms of circuit design, layout, and simulation.

### Design Steps

- Circuit Design: 
  + Circuit design involves creating the logical and functional representation of digital or analog circuits using hardware description languages (HDLs) like Verilog or VHDL.
  + This step defines the behavior of the circuit without specifying its physical layout.
  + Key tasks include defining circuit functionality, specifying input and output behaviors, selecting components like logic gates or transistors, and optimizing for desired performance metrics.

- Layout Design:
  + Layout design is the process of creating the physical arrangement of components, such as transistors, interconnections, and metal layers, on the silicon substrate to implement the circuit designed in the previous step.
  + Layout designers adhere to design rules and guidelines specific to the semiconductor process technology to ensure manufacturability.
  + Key tasks include transistor placement, routing of metal layers, ensuring signal integrity, and minimizing area while meeting performance requirements.


### Typical Characterization Flow 

+ Characterization involves the comprehensive evaluation and modeling of the circuit's behavior under various conditions, ensuring that it meets design specifications and performance goals.
+ This step generates timing models, power models, and other characterization data to describe how the circuit performs under different operating conditions (e.g., voltage, temperature, process variations).
+ Characterization data is crucial for accurate static timing analysis, power estimation, and integration of the circuit into larger designs.

## General timing characterization parameters
### Timing Threshold Definitions 

**Slew Low Rise Threshold (slew_low_rise_thr):**
+ This parameter defines the minimum input signal slope (rate of change) required to trigger a rising transition in the output signal.
+ It helps characterize how fast an input signal must rise to initiate a change in the output signal from low to high.

**Slew High Rise Threshold (slew_high_rise_thr):**
+ Similar to the slew_low_rise_thr, this parameter defines the minimum input signal slope required to trigger a rising transition in the output signal, but for signals that are already at a high logic level.

**Slew Low Fall Threshold (slew_low_fall_thr):**
+ This parameter defines the minimum input signal slope required to trigger a falling transition in the output signal.
+ It specifies how fast an input signal must fall to initiate a change in the output signal from high to low.

**Slew High Fall Threshold (slew_high_fall_thr):**
+ Like the slew_low_fall_thr, this parameter defines the minimum input signal slope required to trigger a falling transition in the output signal, but for signals that are already at a high logic level.

**Input Rise Threshold (in_rise_thr):**
+ This parameter represents the threshold voltage level at which an input signal is considered to be transitioning from low to high.
+ It is essential for accurate timing analysis and helps determine when inputs trigger changes in the circuit.

**Input Fall Threshold (in_fall_thr):**
+ Similar to in_rise_thr, this parameter represents the threshold voltage level at which an input signal is considered to be transitioning from high to low.

**Output Rise Threshold (out_rise_thr):**
+ This parameter defines the threshold voltage level at which an output signal is considered to be transitioning from low to high.
+ It is used to specify the timing behavior of the circuit's outputs.

**Output Fall Threshold (out_fall_thr):**
+ Similar to out_rise_thr, this parameter defines the threshold voltage level at which an output signal is considered to be transitioning from high to low.


# Day-3
# Design library cell using Magic Layout and ngspice characterization
## Labs for CMOS Inverter Ngspice Simulations
### IO Placer 

+ In order to change the distance between the IO pins:

  ```
  % set ::env(FP_IO_MODE) 2
  % run_floorplan`
  ```
+ We can see that they are no more equidistant.
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/6e79d74e-c775-434a-9412-47e8fbcdd47e)


## SPICE Deck Creation for CMOS Inverter  

**SPICE Deck**
+ Component connectivity
+ Component values
+ Identify nodes
+ Name nodes
<p align="center">
 <alt=image src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/76ade735-ee74-4778-8d23-6c6d25912714">
</p>

**CMOS_INVERTER.cir**
```
*** MODEL DESCRIPTIONS ***
*** NETLIST DESCRIPTION ***
M1 out in vdd vdd pmos W=0.375u L=0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u

cload out 0 10f

Vdd vdd 0 2.5
Vin in 0 2.5
*** SIMULATION Commands ***

.op
.dc Vin 0 2.5 0.05
*** include tsmc_025um_model.mod ***
.LIB "tsmc_025um_models.mod" CMOS_MODELS
.end
```

### SPICE Simulation Lab for CMOS Inverter 

+ Simulation steps
  ```
  cd <folder where the .cir file is present>
  source CMOS_INVERTER.cir
  run
  setplot
  dc1
  display
  plot out vs in
  ```
+ The output should be symmetric ie., the threshold voltage should be at vdd/2.
+ If it isnt, try to increase the PMOS width and run the simulation again.

### Switching Threshold Vm 

+ CMOS as a circuit itself is a very **Robust** device.
+ **Switching threshold** defines the robustness of CMOS.
+ **Vm** is the point where Vin=Vout.
### Lab Steps to Gitclone vsdstdcelldesign
```
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
```
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/f3df0a3f-8702-4da1-aed3-6ce75dee149c)

## Inception of Layout and CMOS fabrication process
**Fabrication of CMOS is a 16 Mask process.**
### Create Active Regions
**Selecting the Substrate**
+ We go for a p-type substrate with
  - resistivity around : 5-50 ohm
  - doping level : 10^15 cm^-3
  - orientation : 100

**Creating Active region for transistors**
+ Grow a layer of SiO2(~40nm) on Psub
+ deposit a layer of ~80nm Si3N4 on SiO2
+ deposit 1um layer of photoresist(used to define regions)
+ photolithography
+ etching out Si3N4 and SiO2 using a suitable solvent
+ Place the obtained structure in oxidation furnace due to which field oxide is grown.This process is called LOCOS ( Local oxidation of silicon).
+ Etching out Si3N4 using hot phosphoric acid

### Formation of n-well and p-well
**n-well and p-well formation**
+ deposit a layer of photoresist
+ apply mask to cover NMOS
+ expose to UV light, wash away the area which is exposed and remove mask
+ deposit Boron using ion implementation at an energy of 200keV
+ repeat the same steps for other half using phosphorous at an energy of 400keV
+ Wells have been created but the depth is low, hence subject it to high temperature furnace which increases the well depth.

### Formation of Gate Terminal
- Deposit a layer of photoresist.
- Apply mask to cover NMOS.
- Expose to UV light, wash away the area which is exposed and remove mask.
- Deposit Boron using ion implementation at an energy of 200keV cause we need boron at the surface.
- Repeat the same steps for other half using arsenic.
- Original oxide etched/stripped using hydroflouric solution.
- Then re-grown again to give high quality oxide (~10nm thin).
- Deposit ~0.4um polysilicon layer.
- Dope N-type (phosphorous/ arsenic) ion implants for low gate resistance.
- Deposit a layer of photoresist and repeat the same steps till removing the mask.

### Lightly Doped Drain Formation
- The doping profile near n-well is P+, P-, N.
- Near p-well is N+, N-, P.
- 2 reasons to do this:
  - hot electron effect
  - short cahnnel effect
- On the surface of SiO2, near N-well, deposit a layer of photoresist, and mask it.
- Expose to UV light, wash away the area which is exposed and remove mask.
- Apply phosphorous to form N- implant on p-well.
- Similarly do it on the other half, but apply boron to form P- implant on n-well.
- LDD needs to be protected, hence deposit 0.1um thick SiO2 on full structure and etch out using plasma anisotropic etching.
- This results in the formation of side-wall spacers.
### Source and Drain Formation
- On the surface of SiO2, near N-well, deposit a layer of photoresist, and mask it.
- Expose to UV light, wash away the area which is exposed and remove mask.
- Deposit arsenic at 75KeV that forms an N+ implant on Pwell.
- Similarly do it on the other half, but apply boron to form P+ implant on n-well.
- Subject it to high temperature furnace that results in required thickness of N+,P+,N-,P- implants.
### Local Interconnect Formation
- Etch thin SiO2 oxide in HF solution.
- Deposit Titanium of wafer surface using sputtering.
- Wafer heated at 650-700 degree celsius in N2 ambient for 60 sec.
- Results in low resistant TiSi2.
- At the other places, TiN is formed which is used only for local communication.
- TiN is etched off using RCA cleaning.
### Higher Level Metal Formation
- Deposit 1um of SiO2 with phosphorous or boron (known as phosphoborosilicate glass) on wafer surface.
- Use CMP (chemical mechanical polishing) technique for planarizing wafer surface.
- TiN and blanket Tungsten layers are deposited and subjected to CMP.
- An aluminum (Al) layer is added and subjected to photolithography and CMP.
- Deposit a layer of Si3N4 that acts as dielectric to protect the chip.
<p align="center">
 <img width=400 alt=image src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/4e37fad3-149d-4705-b7d8-c19fc43158de">
</p>

### Lab Introduction to Sky130 Basic Layers Layout and LEF using Inverter

```
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
magic -T sky130A.tech sky130_inv.mag
```
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/d93ea89d-97c1-4995-b92e-92db39145eba)

Select a region from the layout by placing cursor on that point and pressing `s`, Now go to the console and type `what` to display the information of selected area
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/4646050f-7558-4efb-a903-1895768febad)

### Lab Steps to Create std cell Layout and Extract SPICE Netlist
To check for DRC Errors, select a region (left click for starting point, right click at end point) and see the DRC column at the top that shows how many DRC errors are present.The Details of DRC Errors will be printed on the console.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/70293616-0790-41ee-af3f-182d8f7deafa)

For more information on DRC errors plase refer to: [DRC_Erros](https://skywater-pdk--136.org.readthedocs.build/en/136/)
For more information on how to fix these DRC errors using Magic please refer to: [fix_DRC](http://opencircuitdesign.com/magic/)

### Extracting to SPICE Command
```
extract all
ext2spice cthresh 0 rthresh 0
ext2spice
```

cthresh and rthresh are used to extract all parasatic capacitances.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/7ed1ca91-52ff-4d58-9aeb-1210ed0735fd)

We can see that the spice file is created in the folder.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/b6b9a782-efb0-436f-855c-4667b5ae6871)

### Spice netlist
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/319dae40-aa9d-4ea5-a933-d5c4d61bff37)

## Sky130 Tech File Labs
### Grid size.
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/ae519e2a-e9b3-4929-a100-eb360b049180)

### Modified Spice netlist
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/55c80866-d266-4ada-9e12-1ff0f06bdcb5)

```
ngspice sky130_inv.spice
plot y vs time a
```
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/4040e607-b1ad-4f38-9a0f-f411769f3bd1)

### Introduction to Magic Options and DRC rules
**Magic**
+ Magic is a venerable VLSI layout tool, written in the 1980's at Berkeley by John Ousterhout, now famous primarily for writing the scripting interpreter language Tcl. 
+ Due largely in part to its liberal Berkeley open-source license, magic has remained popular with universities and small companies.
+ The open-source license has allowed VLSI engineers with a bent toward programming to implement clever ideas and help magic stay abreast of fabrication technology.
+ However, it is the well thought-out core algorithms which lend to magic the greatest part of its popularity.
+ Magic is widely cited as being the easiest tool to use for circuit layout, even for people who ultimately rely on commercial tools for their product design flow.

**DRC rules**
+ DRC (Design Rule Check) rules are a set of guidelines and constraints used in the field of semiconductor and integrated circuit (IC) design to ensure that the physical layout of a chip or circuit adheres to the manufacturing process's design rules.
+ These rules are essential for maintaining manufacturability and ensuring that the final ICs can be fabricated without defects.
+ The design rules used by Magic's design rule checker come entirely from the technology file.

# DAY 4
# Pre-layout timing analysis and importance of good clock tree
## Timing modelling using delay tables
### Extraction of LEF 
Place and routing (PnR) is performed using an abstract view of the GDS files generated by Magic. The abstract information will include metal and pin information. The PnR tool will use the abstract view information, formally defined as LEF information, to perform interconnect routing in conjunction to routing guides generated from the PnR flow.

- Technology LEF - Contains layer information, via information, and restricted DRC rules
- Cell LEF - Abstract information of standard cells

From PnR POV, We have to follow certain guidelines to get standard cell set
1. Input and output ports must lie on the intersection of vertical and horizontal tracks
2. Width of the standard cell should be odd multiples of the track pitch and height should be odd multiple of vertical track pitch


Track info can be found at : `/home/rohith_nagesh/ASIC/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd
/tracks.info`

**tracks.info**
```
li1 X 0.23 0.46
li1 Y 0.17 0.34
met1 X 0.17 0.34
met1 Y 0.17 0.34
met2 X 0.23 0.46
met2 Y 0.23 0.46
met3 X 0.34 0.68
met3 Y 0.34 0.68
met4 X 0.46 0.92
met4 Y 0.46 0.92
met5 X 1.70 3.40
met5 Y 1.70 3.40
```
- 1st value indicates the offset and 2nd value indicates the pitch along provided direction
- The 'tracks.info' file is used during the routing stage.
- Routes are the metal traces.
- Since the PNR is an automated flow, we need to specify where all we want the routes to go.
- Now we converge the grid definition in the layout to track definition.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/ea57075a-d20a-4f3c-be3b-e6eed2b12817)
- The next requirement is that the width of the cell should be the odd multiple of xpitch which is '0.46' as seen in the 'tracks.info' file.
- As we can see it encloses two full boxes and two halves of one box, totally making three boxes as indicated by the white line.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/0e0f3008-3b27-41c4-b81b-499eab2065ad)

### Lab steps to convert Magic Layout to Std Cell LEF
+ In the tkcon window, type `save sky130_vsdinv.mag`.
+ This is to make our own .mag file.
+ `lef write` to make .lef file

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/38f2e2a3-504e-43ca-b12f-ba6bb37a0712)

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/004d9182-028e-4fa0-a577-19633782bd63)

**sky130_vsdinv.lef**

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/e7c3261f-1de5-4238-be9b-d1f09a70143f)

### Introduction to Timing Libs and Steps to include New cell in Synthesis
Copy the lef file and the libraries.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/583a0135-f439-4942-9798-f0490212d069)

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/4daa9991-6563-4b52-8e99-728ef2ef218c)

Modify tcl file

**config.tcl**
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/e6d88bcb-74c5-479d-87d1-2c0b565dbfe6)

### OpenLANE interactive window
```
prep -design picorv32a 
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs 
run_synthesis
init_floorplan
run_placement
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/81a10953-2142-46b4-82c9-5cae21a5d22e)

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/4a584eb3-dc8a-437c-a71b-639e6d2bb986)

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/224fb048-7d61-49bd-832e-e7d512845521)

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/a4dce130-61d5-4c2c-9113-8882f3361b91)

We can see that We have plugged in our custom cell in the OpenLANE flow.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/1dae9dfc-7f32-4686-9263-44fbbc8bd833)

VLSI engineers will obtain system specifications in the architecture design phase. These specifications will determine a required frequency of operation. To analyze a circuit's timing performance designers will use static timing analysis tools (STA). When referring to pre clock tree synthesis STA analysis we are mainly concerned with setup timing in regards to a launch clock. STA will report problems such as worst negative slack (WNS) and total negative slack (TNS). These refer to the worst path delay and total path delay in regards to our setup timing restraint. Fixing slack violations can be debugged through performing STA analysis with OpenSTA, which is integrated in the OpenLANE tool. To describe these constraints to tools such as In order to ensure correct operation of these tools two steps must be taken:

Design configuration files (.conf) - Tool configuration files for the specified design

Design Synopsys design constraint (.sdc) files - Industry standard constraints file

### Delay Tables
**Introduction**
+ Delay tables, often referred to as delay models or delay tables in the context of digital integrated circuit design, are data structures that provide information about the propagation delay of digital logic gates or cells under various conditions.
+ These tables are a fundamental component of static timing analysis (STA) and are used to predict the signal arrival times and meet timing constraints in digital designs.

**Purpose of Delay Tables:**
+ Delay tables are used to estimate the time it takes for a signal to propagate through a digital logic gate or cell.
+ This information is crucial for ensuring that signals meet their setup and hold time requirements and for calculating the overall timing behavior of a digital circuit.

**Types of Delay Tables:**
+ There are two main types of delay tables:
   - Library Delay Tables: These tables are part of a standard cell library and provide information about the delays of individual logic gates (AND, OR, XOR, flip-flops, 
    etc.) under various operating conditions (input transitions, voltage, temperature, etc.). Library delay tables are used to estimate the delays associated with 
    different gate types.
   - Interconnect Delay Tables: These tables describe the delay associated with routing signals between logic gates or cells on a chip. They account for wire resistance, 
   capacitance, and other physical properties that affect signal propagation.

**Data in Delay Tables:**
+ Delay tables typically include information such as:
   - Input conditions: Input transition times or slew rates.
   - Process corners: Variations in process technology, including worst-case and best-case scenarios.
   - Operating conditions: Voltage and temperature conditions.
   - Delay values: Delays for signal propagation through the gate or interconnect, often specified for different output loading conditions.

**Timing Analysis:**
+ Delay tables are used by STA tools to perform timing analysis on digital designs.
+ These tools use the delay tables to estimate the critical path delays, setup times, hold times, and other timing parameters.

**Corner Analysis:**
+ Corner analysis involves using delay tables for various process corners (e.g., slow, typical, fast) to account for manufacturing process variations.
+ This ensures that the design meets timing under a range of conditions.

**Clock Domain Crossing (CDC) Analysis:**
+ Delay tables are also used in CDC analysis to analyze signals that cross between different clock domains.
+ Understanding signal arrival times is crucial in preventing metastability issues.

**Optimization:**
+ Designers use delay tables to optimize their designs by selecting gates with appropriate delays to meet performance, power, and area goals.

**Iterative Process:**
+ During the design process, delay tables are used iteratively.
+ Designers may make adjustments to the design and rerun timing analysis to ensure that the design meets its timing constraints.

## Timing analysis with ideal clocks using openSTA
### Configure OpenSTA for Post-Synth Timing Analysis
We must create two files.
  1. **pre_sta.conf** in the openlane directory
  2. **my_base.sdc** in the src directory under the picorv32a directory

**pre_sta.conf**

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/bac94146-3244-4e0c-a169-4b6a76c7a583)

**my_base.sdc** 

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/9b767333-e13e-4c70-ad12-2b08ce575561)

Use the command `sta pre_sta.conf` to run the timing analysis 

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/56477253-1785-4e02-8494-7e5135ac4c5d)

<p align="center">
  There is a slack violation.
</p>

### Optimise synthesis
+ Setting MAX_FANOUT value to 4 reduces the slack violation.
+ `set ::env(SYNTH_MAX_FANOUT) 4`
+ Then `run_synthesis`

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/cc9a0e3e-e86c-4e55-a9ca-9a7536acb0c0)

+ Since we have synthesised the core using our vsdinv cell too and as it got successfully synthesized, it should be visible in layout after `run_placement` stage which is followed after `run_floorplan` stage.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/e1a89d1a-dc46-451e-b21b-120e3cc37f79)

## Clock tree synthesis TritonCTS and signal integrity
### CTS
- Run the command `run_cts` to run CTS
- picorv32a.synthesis_cts.v is created 

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/e41008c1-def4-4f95-9c63-3aac65867ac8)

## Timing analysis with real clocks using openSTA
### Lab steps to analyse Timing with Real CLocks
```
openroad
read_lef /openLANE_flow/designs/picorv32a/runs/18-09_14-09/tmp/merged.lef
read_def /openLANE_flow/designs/picorv32a/runs/18-09_14-09/results/cts/picorv32a.cts.def
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/18-09_14-09/results/synthesis/picorv32a.synthesis_cts.v
read_liberty -max $::env(LIB_SLOWEST)
read_liberty -max $::env(LIB_FASTEST)
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
```
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/ed84d729-2ca8-4023-b556-755a46167905)

```
set_propagated_clock [all_clocks]
report_checks -path_delay min_max -format full_clock_expanded -digits 4
```
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/4802307e-7a38-484d-ba9e-7fa3c831f784)

# DAY 5
# Final steps for RTL2GDS using tritonRoute and openSTA
## Routing and design rule check (DRC)
### Maze routing
Maze routing is a technique used in electronic design to efficiently connect components on a chip's layout. Lee's algorithm, also known as Lee's BFS algorithm, is a popular method for finding the shortest path in a grid-based maze by exploring it layer by layer.

### DRC
- DRC stands for "Design Rule Checking." It is a crucial step in the integrated circuit (IC) design and electronic design automation (EDA) process. DRC involves verifying that the layout of a semiconductor device or IC adheres to the specified design rules and constraints.

- These design rules are a set of guidelines and constraints defined by semiconductor manufacturers and design teams to ensure the proper functioning of the chip and its manufacturability. DRC checks for violations of these rules, which can include criteria related to minimum feature size, spacing between components, wire widths, and other physical and electrical properties.

- By performing DRC, designers can identify and rectify potential issues early in the design process, helping to prevent costly errors and ensuring that the final IC design meets the required specifications and can be successfully manufactured.

## Power Distribution Network and routing
### Power Distribution Network
Once we've created our clock tree network and confirmed the successful post-routing STA checks, the next step is to proceed with generating the power distribution network.

+ The PDN feature within OpenLANE will create:
   - Power ring global to the entire core
   - Power halo local to any preplaced cells
   - Power straps to bring power into the center of the chip
   - Power rails for the standard cells
+ We see that there is a change in the DEF.

### Global and Detailed Routing 
+ OpenLANE uses TritonRoute as the routing engine for physical implementations of designs. Routing consists of two stages:
   - Global Routing - Routing guides are generated for interconnects on our netlist defining what layers, and where on the chip each of the nets will be reputed.
   - Detailed Routing - Metal traces are iteratively laid across the routing guides to physically implement the routing guides.

+ To run routing in OpenLANE:
  `run_routing`
+ If DRC errors persist after routing the user has two options:
  - Re-run routing with higher QoR settings.
  - Manually fix DRC errors specific in tritonRoute.drc file.

## TritonRoute Features

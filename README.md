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
  <img width="500" alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/d85acaf4-3187-4b31-a87c-0e392d572ccd">
</p>

**130nm**
+ It refers to a semiconductor manufacturing process technology node, which represents the minimum feature size or transistor gate length in that technology.
+ In semiconductor manufacturing, the feature size is a critical metric because it determines the size and performance characteristics of the transistors and other components that make up integrated circuits (ICs).

## Simplified RTL2GDS Flow 

**RTL to GDSII**
<p align="center">
<img width="500" alt="image" src= "https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/e8434b0b-5086-4193-85ae-cf8280ad3749">
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
  <img width="239" alt="image" src="https://github.com/Veda1809/pes_pd/assets/142098395/2758ce5f-9301-4876-929e-72d93de298f6">
</p>

### Introduction to OpenLane Detailed ASIC Design Flow 

<p align="center">
  <img width="600" alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/cfe88578-4abc-4de1-833e-134b738f684c">
</p>

<p align="center">
  Fig 3. OpenLane ASIC Flow
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

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/6319ad92-6b2e-4949-afc1-24573f64b01e)

**skywater-pdk** contains all the PDK related files.

**open_pdks** contains all the scripts and files that convert these foundry level PDKS to be compatible with the open-source EDA tools

**sky130A** is made compatible with our open-source environment.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/15e59640-5dac-4d06-8246-6cc7126c2666)

**libs.ref** seems specific to technology.

**libs.tech** seems specific to the tool.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/cc6d7f85-e28b-4512-ad81-cfec7064caea)

**sky130_fd_sc_hd** has all the technology files.
### Design Preparation Step 
To invoke OpenLane

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/3d3b7b70-4235-4551-b1d1-7e2b5d9148c6)

Under **Designs** folder, we are going to use **picorv32a**.

**src** files contains verilog and sdc file.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/a7672428-37d5-4473-a0b2-2333abe85506)

We are going to prepare the design `prep -design picorv32a`.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/70ab006e-f9df-42d9-b373-3e5d9623d1b3)

After Design Preparation, we will run the Synthesis:
- `run_synthesis` command use to run the synthesis
- Yosys-Perform RTL Simulation abc-It performs technology mapping and the netlist is created. Open STA-Perform static timing analysis after synthesis.
- This will execute both yosys and abc pass will be done

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/8644c883-e899-47a2-9515-037d542e8d23)

### Characterize Synthesis Results 
- Number of D Flip-Flops = 1613
- Number of Cells = 14876
clock ratio = 1613/14876=0.1084 or 10.84 percent

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/f95fd189-68f7-49c9-a3ec-81def6bce54a)

# Day-2
# Floor planning and introduction to library cells
## Chip Floor planning considerations
### Utilisation Factor and Aspect Ratio 
**Utilization factor:** Utilization factor is a measure of how efficiently a system or component is being used, often expressed as a ratio or percentage. It is relevant in areas such as lighting design, heat exchangers, and telecommunications.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/fb485a18-965d-4bb3-8cfe-ae6e13bdfb64)

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

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/0adcbc97-87e7-4270-9ae3-c3f74fd083d9)

## Review Floorplan Layout in Magic 
  
 ```
 magic -T /home/rohith_nagesh/ASIC/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/fb3883ea-f214-4984-aea0-e93a702c79db)

## Library Binding and Placement
### Netlist Binding and Initial Place Design 

**Netlist Binding**
+ Netlist binding is a crucial step in the process of transforming a high-level design description into a representation that can be physically implemented on a chip or printed circuit board (PCB).
+ This step involves associating the logical components and connections described in the netlist with physical components, such as gates, flip-flops, and interconnections, that will be used in the actual implementation.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/359638d8-0db4-4fbe-b29c-1e238552ebac)

## Optimise Placement using Estimated Wire-Length and Capacitance 

+ We need to estimate the wire length and capacitance, and based on that insert repeaters.

<p align="center">
  <img alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/ba3d121c-4392-4fb4-a2ad-11bee32c9bb5">
</p>

### Need for Libraries and Characterization 

**Library Characterisation**
+ Library characterization is the process of creating a comprehensive and accurate characterization model for a library of standard cells.
+ These standard cells serve as the fundamental building blocks for designing digital circuits.
+ The goal of library characterization is to provide designers with essential information about how these cells behave under various operating conditions, allowing for accurate timing analysis and optimization.

## Congestion aware Placement using RePLAce 

`run_placement` command use to run the placement
<p align="center">
<img alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/22e258de-b842-4d2f-a949-c3da6b139a4e">
</p>


```
magic -T /home/rohith_nagesh/ASIC/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/67569ed9-206f-42ef-a16c-ebc50c0f7a13)

## Cell Design and Characterization Flows
### Inputs for Cell Design Flow 

**Cell Design Flow**
<p align="center">
  <img img width="500" alt="image" src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/7f8c23a8-12ee-4bdd-8128-f55a235aea11">
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
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/49e8f4cb-46de-43c3-8cc1-f5bb34dd0efa)


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
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/91ae90ad-5a6d-4f2a-a53e-1d345e84e6d6)

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
 <img width=400 alt=image src="https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/c0559acd-7ca0-4342-b8ba-953455ac0592">
</p>

### Lab Introduction to Sky130 Basic Layers Layout and LEF using Inverter

```
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
magic -T sky130A.tech sky130_inv.mag
```
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/1bd18ea2-c8c5-4714-bbdd-5f069d100603)

Select a region from the layout by placing cursor on that point and pressing `s`, Now go to the console and type `what` to display the information of selected area
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/25c5912e-c75d-4cd8-9a33-5a84cbfe2fe5)

### Lab Steps to Create std cell Layout and Extract SPICE Netlist
To check for DRC Errors, select a region (left click for starting point, right click at end point) and see the DRC column at the top that shows how many DRC errors are present.The Details of DRC Errors will be printed on the console.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/2d1fef45-8fa3-45e2-834c-e1eed6b0b16c)

For more information on DRC errors plase refer to: [DRC_Erros](https://skywater-pdk--136.org.readthedocs.build/en/136/)
For more information on how to fix these DRC errors using Magic please refer to: [fix_DRC](http://opencircuitdesign.com/magic/)

### Extracting to SPICE Command
```
extract all
ext2spice cthresh 0 rthresh 0
ext2spice
```

cthresh and rthresh are used to extract all parasatic capacitances.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/d8704d87-d0fa-4ab7-ba99-476d89384fe0)

We can see that the spice file is created in the folder.

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/9b42a949-8482-417e-99f5-9a8ebea101df)

### Spice netlist
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/9823f82f-1953-47a3-8ba3-189652e9aa1b)

## Sky130 Tech File Labs
### Grid size.
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/736ee417-95d5-474a-94b2-02261f032412)

### Modified Spice netlist
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/c5092093-91c0-4282-a918-b733bba6986a)

```
ngspice sky130_inv.spice
plot y vs time a
```
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/0b2eaf20-94b2-4770-a9a1-3384ad9affbf)

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
1st value indicates the offset and 2nd value indicates the pitch along provided direction

### Setting grid values using above file info
![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/80cf8ade-c990-454b-bfb2-eec981a59931)

Layout before setting grid info vs after setting grid info

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/6e316d00-1cd5-48b4-80bf-2dd35c41ebd5)

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/80a786ff-90c7-413d-b7e9-8cb7de9c3cc9)

![image](https://github.com/RohithNagesh/PES_PhyDesign/assets/103078929/b57e40f1-db32-46b4-8148-da280187ed55)

- From the above pic, its confirmed that the pins A and Y are at the intersection of X and Y tracks. So the first condition is met.
- The PR boundary is taking 3 grids on width and 9 grids on height which says that the 2nd condition is also met

### LEF Generation
Since the layout is perfect, we can generate the lef file

#### 1. save the modified layout (with new grid)
   - In console, type ```save sky130_vsdinv.mag```
   - This saves the modified layout in current working directory

#### 2. Open the file and extract LEF
   - Open using ``` magic -T sky130A.tch sky130_vsdinv.mag```
   - in the console opened, type ```lef write``` and a lef file will be generated




## Timing analysis with ideal clocks using openSTA
## Clock tree synthesis TritonCTS and signal integrity
## Timing analysis with real clocks using openSTA

# DAY 5
# Final steps for RTL2GDS using tritonRoute and openSTA
## Routing and design rule check (DRC)
## Power Distribution Network and routing
## TritonRoute Features
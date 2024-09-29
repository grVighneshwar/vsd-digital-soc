# VSD SoC Design

## **Day-1**
**Introduction**
![image](https://github.com/user-attachments/assets/e2ca7418-3bfd-4159-a5a0-b534d25ea2ad)
![image](https://github.com/user-attachments/assets/84ad0bb8-85b1-495a-aeec-22559ffa1d17)
- **Die:**
  
The die is the small, rectangular piece of silicon that contains the actual circuitry of the IC. It is the result of cutting a larger wafer into individual pieces after the fabrication process.
The die contains all the transistors, interconnects, and other components necessary for the chip’s operation.
The die is typically mounted inside a protective package that connects the die to the outside world via pins or pads

- **Core:**
  
A core refers to the processing unit within the chip that performs computations. A modern chip can contain multiple cores (e.g., dual-core, quad-core) to allow for parallel processing.
The core is responsible for executing instructions, processing data, and performing tasks. In a CPU, it includes components like the arithmetic logic unit (ALU) and registers.

- **Pad Ring:**
  
 The pad ring is the outer ring of the die that consists of metal pads used for external connections.
These pads allow for the input/output (I/O) connections between the chip and the external environment, such as power supply, ground, and data signals.

- **IP Block (Intellectual Property Block)**:
  
 An IP block is a reusable design unit, such as a pre-designed module that performs a specific function (e.g., a memory controller, interface, or processor core).
 IP blocks are used to speed up the design process by integrating pre-verified components into the chip.

- **Interconnects:**
  
 Interconnects are the metal wires or traces on the die that connect different transistors, logic gates, and blocks.
 They enable communication and data transfer between various parts of the chip. Interconnects exist across multiple layers of metal, with lower layers used for local connections and higher layers for global connections.

- **Metal Layers:**
  
 Metal layers are the layers of metal (often copper or aluminum) stacked on top of the silicon substrate.
 These layers provide routing paths for signals and power across the chip. Modern chips may have many metal layers for routing complexity.

- **Substrate:**
  
 The substrate is the base layer of the die, typically made of silicon.
 It serves as the foundation on which transistors and other components are fabricated. The substrate has specific doping to form semiconductor properties.

- **Power Grid:**

 The power grid is a network of metal lines distributed across the chip to deliver power (VDD) and ground (VSS) to all components.
 It ensures reliable power distribution across the die to avoid voltage drops and power integrity issues.

- **Cache:**
  
 A cache is a small, high-speed memory block located close to the core.
 It stores frequently accessed data to speed up processing by reducing the need to fetch data from the slower main memory.

- **I/O Ports:**
  
 I/O ports are the interface points on the chip that allow communication between the chip and external devices.
 These ports handle the flow of data in and out of the chip and can include power supply pins, data buses, and clock signals.

 
![image](https://github.com/user-attachments/assets/1de06036-f24a-487f-9c15-ab87783cdbbc)
**1. Application Software (Apps)**

The top layer represents application software or programs that users interact with, such as Mozilla Firefox, MS Word, PowerPoint, Excel, Acrobat Reader, and Oracle VirtualBox.
These applications are written in high-level programming languages like C++, Visual Basic (VB), and Java.
The code written in these languages is user-facing, providing functionality to perform tasks like web browsing, document editing, and virtual machine management.

**2. System Software (Operating System)**

System software, represented by operating systems like Windows, Linux, and macOS, is responsible for managing hardware resources and providing services to application software.
The compiler within the operating system converts high-level programming languages (C++, Java) into machine instructions (e.g., Instr1, Instr2), producing an executable file (e.g., .exe).
The assembler further converts these instructions into binary code (machine code) that the hardware can understand (e.g., 101001101).

**3. Hardware**

At the lowest level, hardware consists of physical components like processors, memory, and peripherals.
The hardware executes the binary instructions provided by the assembler, processing data and performing the required operations.
The image shows a simplified diagram of a chip layout, with connections for input (Din), clock signals (Clk), and output (Dout1–Dout4), representing data and control flows within the hardware.

![image](https://github.com/user-attachments/assets/255523b6-ace9-4caa-9772-4105225e2d5f)

**1. ASIC**

The core of the diagram represents the ASIC, which is the target product — a customized integrated circuit designed for a specific application.

**2. EDA Tools**

EDA (Electronic Design Automation) Tools like Qflow, OpenROAD, and OpenLane are used to automate the design process of ASICs, from RTL (Register Transfer Level) to GDSII (final layout).
These tools handle tasks like synthesis, placement, routing, and verification to create a working ASIC design.

**3. PDK Data**

PDK (Process Design Kit) data refers to the technology-specific files and models needed to design and manufacture ASICs.
In this case, the Skywater 130nm PDK is referenced, provided by Google and Skywater for open-source design, enabling users to fabricate their ASICs at a 130nm technology node.

**4. RTL Designs**

RTL Designs represent the hardware description of the ASIC in languages like Verilog or VHDL.
Open-source repositories like librecores.org, opencores.org, and GitHub are mentioned as sources for these RTL designs, which serve as the blueprint for the logic implemented in the ASIC

![image](https://github.com/user-attachments/assets/78201e97-5b71-46b1-bd53-fcc415533ffd)

**1. RTL (Register Transfer Level):**

The design process starts with RTL, which is the hardware description written in HDL (like Verilog or VHDL). RTL defines the logic of the design.

**2.Synthesis:**

This step converts the RTL into a gate-level netlist, mapping high-level logic to specific gates in the PDK (Process Design Kit). The netlist is technology-specific.

**3.FP+PP (Floorplanning and Power Planning):**

Floorplanning defines the physical layout, i.e., how the blocks will be arranged on the chip.
Power planning ensures that power is distributed efficiently across the design.

**4.Place**

During placement, the gates from the netlist are assigned to specific locations within the defined floorplan.

**5.CTS (Clock Tree Synthesis):**

This step focuses on distributing the clock signal uniformly throughout the design to minimize skew, ensuring synchronous operation.

**6.Route:**

Routing establishes the physical connections between the placed gates according to the netlist. It involves creating metal layers for signal paths.

**7.Sign Off:**

This is the final verification step where the design is checked for timing, power, and manufacturability before the layout is sent for fabrication.

**8.GDSII:**

The final output is a GDSII file, which contains the physical layout and is used for the fabrication of the ASIC.

### **How to open the tool openlane?**

> first open the terminal and change the directory to openlane
```

cd work/tools/openlane_working_dir/openlane

```
> then open the docker look for flow.tcl file
```
./flow.tcl -interactive
```

> This opens the openlane
```
package require openlane 0.9
```

### **Setting up the files for the design**
```
prep -design picorv32a
```
> Merges LEF's
> to run the synthesis
```
run_synthesis
```
#### **Synthesis results**
> creating the runs folder after synthesis

![Untitled](https://github.com/user-attachments/assets/de6b0291-73e5-45c6-ba64-08579f08363a)
![Untitled](https://github.com/user-attachments/assets/d0192cef-6b3c-44ad-bd07-ee256074ffe2)
![Untitled](https://github.com/user-attachments/assets/9989c3b9-c971-466e-8600-8699019d4b14)
![Untitled](https://github.com/user-attachments/assets/32e27963-1aad-4c5a-a337-a88582eef55a)
![Untitled](https://github.com/user-attachments/assets/47c72f8b-1673-42d5-b797-671b06aaefed)

** calculating flop ratio**
flopratio       = no of dflipflop/total no of cells
                = 1613/14876
                = 0.108429685
%of flop ratio  = 10.842 

## **Day-2**

### **Utilization Factor and Aspect ratio**
![image](https://github.com/user-attachments/assets/73c3b921-22f4-4b2f-b37e-ca2100032e5e)
### **Define the locations of preplaced cells**
![image](https://github.com/user-attachments/assets/da46511d-b5a5-44f2-bcf6-e67ea5a34344)
### **Noise margin**
There are three diffrent regions 
- Logic 0 region
- Undefined region
- Logic 1 region
  ![image](https://github.com/user-attachments/assets/decf9f30-1b71-4e63-9a4f-4fde78debd8b)
### **Decoupling capacitors**
In the switching action Decoupling capacitors provide power supply to the circut since its placed near the blocks there's no drop in voltage
![image](https://github.com/user-attachments/assets/e7689c9d-26dc-42b1-a626-b3f57abe14b0)
### **Power planning**
![image](https://github.com/user-attachments/assets/8df94da6-0ff2-4491-a6b6-20e477e9a77a)
### **Pin placement**
Placing the pins based on the design
![image](https://github.com/user-attachments/assets/68f11e46-a18c-4783-9ee5-355c78a7b9e6)
### ** Logical Cell Placement Blockage**
![image](https://github.com/user-attachments/assets/32238319-a369-4c56-bcf6-bae0b22452f1)
### **Steps for Floorplan**
> To run the floorplan in the open lane
```
run_floorplan
```
Floorplan run successfull
![Untitled](https://github.com/user-attachments/assets/37482254-04ea-4317-902b-089240987eb1)
![Untitled](https://github.com/user-attachments/assets/224e8f0e-e290-4957-bea3-961866886902)
** seeing the pin numbers in the logs folder**
![Untitled](https://github.com/user-attachments/assets/18abc057-6af3-4719-b25e-58bdc2f7f3f0)
> In openlane design file core utilization

![image](https://github.com/user-attachments/assets/4a23c4c6-1c09-4f2a-a029-3c23cc8a8886)

> In open lane configuration folder core utilization
![Untitled](https://github.com/user-attachments/assets/9b6a518c-203f-48d6-b4b0-609d570877cf)
> In runs folder core utilization
![Untitled](https://github.com/user-attachments/assets/02851d21-5dbd-4184-9b5e-917d286975c0)

### **Steps to generate layout using magic**
- Go into floorplan folder
```
#path for floorplan folder
/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-09_11-03/results/floorplan
```
- To veiw the layout in the magic window\
  ```
  magic -T /home/vsduser//Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
  ```
- To adjust the layout to the window press the key 'S'
- To make it fit for the window press the key 'V'
- To see the metal layer and to zoom into the layout left click+ right click and then press Z to zoom in to zoom out press the keys S and V
- To see the metal layers select the layer and go to tkcon window and typle the command what it'll automatically shows which metal is used

  ### **Outcomes of the lab**
![Untitled](https://github.com/user-attachments/assets/224728c8-bcb0-497f-bca2-807ce8b1a778)
![Untitled](https://github.com/user-attachments/assets/439b4af8-0579-4226-8319-31a75b8c26b5)
![Untitled](https://github.com/user-attachments/assets/326e0e6b-7c6c-45da-86f8-b70d55d7960d)

### **Library binding and placements**
- Bind netlist with physical cells
![image](https://github.com/user-attachments/assets/ea21f3dc-9949-48f5-a26a-417f3c0917f3)
- Placing the blocks based on the io pins and connections
  ![image](https://github.com/user-attachments/assets/19cf5b3d-55af-409f-8f54-98bf104741e0)
- Optimizing the placements: based on the distance between blocks and pin adding buffers or repeters to maintain the signal quality
  ![image](https://github.com/user-attachments/assets/f5fcafd8-fd71-49e7-9971-9b3222214c86)

### **Need for libraries and charectorization**
IC design flow
- Logic synthesis
- Floorplanning
- Placement
- Clock synthesis
- Routing
- Static Time analysis

### **Congestion aware placement using RePlAce**
Two types of placements
- Global placement
- Detailed placement

What we are doing in this lab is Global placement
To open the placement blocks
```
#First run on open lane
run_placement
#go to placement folder which is created in results and type the commmand
magic -T /home/vsduser//Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![Untitled](https://github.com/user-attachments/assets/2869760e-06b7-424a-8470-f56099491996)
### **Cell design flow**
![image](https://github.com/user-attachments/assets/c9417dd5-be1c-4d06-ad69-a78f81bc9ebf)
Timing considorations
![image](https://github.com/user-attachments/assets/d9091589-a225-41e3-ac72-c59eaa47510c)
Propogation delay


## **Day 3**
### **Spice deck creation for CMOS inverter**
![image](https://github.com/user-attachments/assets/5977ee74-d8bc-4d6e-865a-08963319968e)
**Technical Specs for CMOS inverter**
![image](https://github.com/user-attachments/assets/3515122a-2445-44ca-9a9d-be8feedfbc7c)
**Cloning the vsdstdcelldesign repo**
> Type the command in the on the folder openlane
```
git clone https://github.com/nickson-jose/vsdstdcelldesign --depth 1
```
> to see the layout of cmos inverter
```
magic -T sky130A.tech sky130_inv.mag &
```
![Untitled](https://github.com/user-attachments/assets/1498a2d6-2e95-4897-9588-3a90cb6e9baa)
> goto tckon.tcl window to create the spice deck and type the command
```
/ to extract all the files
extract all
// all the files from sky_130_inv will be copied to sky130_inv.ext
ext2spice rthresh 0 cthresh 0
ext2spice
// itll create the spice deck
```
### **Steps to create SPICE deck**
- Goto the file vsdstdcelldesign
- to see the spice file
  ```
  vim sky130_inv.spice
  ```
  ![image](https://github.com/user-attachments/assets/557c566f-09a7-42d2-b232-1cd2c2faaf78)

- to edit the sepcs defined in the spice deck
   ```
   gedit sky130_inv.spice
   ```
- to run the spice simulation
   ```
   ngspice sky130_inv.spice
   ```
  ![image](https://github.com/user-attachments/assets/3b497a33-8286-4034-87f1-65ff6b26399f)


- it will show all the specs and to plot
  ```
  plot y vs time a
  ```
 ![image](https://github.com/user-attachments/assets/5f7e3437-6486-49fe-a103-95e59b802bbe)

  rise time = (5.5-5.184)=0.316 ns
  fall time =0.39659ns

  ### **Preparing files for drc check**

  - go to root folder
```
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
```
- after donloading type the command
```
tar xfz drc_tests
```
- now change the directory to drc tests
- run the magic
```
magic -d XR
```
- in tckon.tcl filoe
```
drc check
```
- to resolve the drc error go to tech folder and edit the required feilds
  ```
  gedit sky130A.tech
  ```
  ![image](https://github.com/user-attachments/assets/431bebb9-6730-4edf-a3ac-6c261b16902d)
![image](https://github.com/user-attachments/assets/f8dd4c35-71f5-48f9-8321-10c05da2bf68)

- again load the tech file after editing
  ```
  load sky130a.tech
  drc check
  ```
  ![image](https://github.com/user-attachments/assets/46f571d5-c1a9-4640-9c62-bba2e6f1806f)


## **Day 4**

- creating lef file
```
  # type the command in the tcl window
  lef write
```
- Copying tosrc directory
```
#Copy lef file
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
#Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```
- editing config.tcl file
  ![image](https://github.com/user-attachments/assets/ce865c6e-ce6f-4b5a-9453-5c9c4cbc2dc3)
  - run the docker and open open lane
  - To work on the previous created directory
  ```
  prep -design picorv32a -tag 22-09_11-03
  set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
  add_lefs -src $lefs
  ```
 - now run the synthesis
![image](https://github.com/user-attachments/assets/86e7361a-a657-4d25-9f77-f5f76fddfd6a)
![image](https://github.com/user-attachments/assets/885b213c-90ad-4d9a-bdf9-1a7121a3de1b)
```
echo $::env(SYNTH_STRATEGY)

#set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

#display current value of variable SYNTH_BUFFERING
echo $::env(SYNTH_BUFFERING)
echo $::env(SYNTH_SIZING)
set ::env(SYNTH_SIZING) 1

#display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

```
- now re run the synthesis
![image](https://github.com/user-attachments/assets/c857b767-91d6-4ca3-a286-92bc6c299492)
- now run the floorplan
```
init_floorplan
place_io
tap_decap_or
```
- run placement
- now run the magic in othewr terminal to see weather our cell is modified or what
![image](https://github.com/user-attachments/assets/d29936b3-8795-4d5f-9380-a6551800176e)
![image](https://github.com/user-attachments/assets/da48e821-3ccf-4a71-930e-b5e4cc6d6d6b)
![image](https://github.com/user-attachments/assets/9ca38ad9-1f2a-4bee-9c84-10bb75e056dd)

- pre-sta.conf
![image](https://github.com/user-attachments/assets/53b20520-f432-4af1-89a8-c9f062fdf055)
-run the sta
```
sta pre_sta.conf
```
![image](https://github.com/user-attachments/assets/ccc6a4e3-e362-42db-9084-c1576495a3d4)
![image](https://github.com/user-attachments/assets/34f4b7d4-1570-461b-b307-bf2b9cc24f92)
- check for the cells which has more delay and fanouts replace them with other
![WhatsApp Image 2024-09-28 at 19 46 38_2f2cf062](https://github.com/user-attachments/assets/21e0d960-bbe1-47db-8232-bd96b74163c6)
![WhatsApp Image 2024-09-28 at 19 46 09_2db2d077](https://github.com/user-attachments/assets/7f5181d7-9ffb-44bf-a610-f26c1ab12031)
- doing it untill it gets the minimal value
- slack should be in positive value
- write the verilog file
```

write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/picorv32a.synthesis.v

```
- Run the neccesary commands to run the synthesis
- Post-CTS OpenROAD timing analysis.
```
  
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all clocks as propagated clocks
set_propagated_clock [all_clocks]
# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
```
Commands to be run in OpenLANE flow to do OpenROAD timing analysis
```
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/placement/picorv32a.placement.def


run_cts


openroad


read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef


read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def


write_db pico_cts1.db


read_db pico_cts.db


read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v


read_liberty $::env(LIB_SYNTH_COMPLETE)


link_design picorv32a


read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc


set_propagated_clock [all_clocks]

report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
report_clock_skew -hold

report_clock_skew -setup

# Exit to OpenLANE flow
exit


echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)
```

## **Day 5**

### **Routing**
Routing is the process of connecting components such as standard cells, macros, IOs, and other circuit elements using metal interconnects. It is a fundamental step in transforming the synthesized netlist into a physical design.

- Key Aspects of Routing:
### **Global Routing**

**Purpose**: Provides a high-level, coarse path for how nets (interconnections) will be routed across the chip.
**Functionality**: Divides the chip into grids and assigns paths for nets without detailing the actual geometry.
**Outcome**: Guides the subsequent detailed routing by providing a global connectivity framework.

### **Detailed Routing**

**Purpose**: Converts global routing into exact geometrical paths on different metal layers.
**Metal Layers**: Lower layers are typically used for local connections, while higher layers are used for global or long-distance connections.
**Tools**: Commonly used tools for routing include Cadence Innovus, Synopsys IC Compiler II, and others.
Design Rule Check (DRC):

### **Design Rule Check (DRC)**
Ensures that the layout follows the rules defined by the semiconductor foundry. These rules are critical for ensuring that the design can be reliably manufactured.

- Key Aspects of DRC:
**Design Rules**:

**Spacing Rules**: Ensure that different layers, such as metals and vias, maintain minimum distances to avoid shorts and ensure manufacturability.
**Width Rules**: Enforce minimum and maximum wire widths to ensure wires can carry the required current without issues.
**Enclosure Rules**: Define how layers like vias and metal should overlap to ensure reliable connections.
**Alignment Rules**: Ensure that different layers are properly aligned to avoid manufacturing misalignment.

![image](https://github.com/user-attachments/assets/ae8ac6cb-1d1f-405e-900a-c4f2e8d7941a)
![image](https://github.com/user-attachments/assets/1dd124b4-86ba-4551-988b-eb1523cdc62c)

### **Lee's algorithm**

Lee's Algorithm is a well-known pathfinding algorithm used in maze routing, often applied in VLSI physical design for routing connections on a grid (like metal traces on an IC). It finds the shortest path between two points in a grid while avoiding obstacles. The algorithm guarantees finding the optimal solution, as it explores all possible paths in a breadth-first manner.

**Key Characteristics**:
- Optimality: Lee’s Algorithm always finds the shortest path if one exists.
- Complexity: Its time complexity is proportional to the number of cells in the grid (O(n × m) for an n × m grid), making it inefficient for very large grids.
- Applications: It's used in IC routing for global and detailed routing, and in general pathfinding problems where obstacles are present.
![image](https://github.com/user-attachments/assets/a1a31a68-46ee-4b47-b028-1f09e3117087)
![image](https://github.com/user-attachments/assets/75d57970-e660-46b8-9bf5-e835fb394348)

### **Maze Routing**
Maze Routing is a fundamental pathfinding algorithm used in physical design, particularly in VLSI routing, to find a path between two points on a grid while avoiding obstacles.

**Key Features**:
- Grid-Based Approach: The chip area is divided into a grid, where each cell can be empty (passable) or blocked (obstacle).
- Breadth-First Search (BFS): The algorithm typically uses a breadth-first search (similar to Lee's Algorithm) to explore all possible paths from the source to the target, ensuring the shortest path is found.
- Wavefront Expansion: Starting from the source, the algorithm marks all neighboring cells and continues expanding outward until it reaches the destination.
- Backtracking: Once the target is reached, the algorithm backtracks to determine the shortest path by following the sequence of cells with decreasing distance values.
**Applications**:
-Maze routing is commonly used in detailed routing of ICs, especially when there are many obstacles (e.g., previously routed nets).
- It guarantees an optimal path, but it can be slow and memory-intensive for large grids.

## **Steiner Tree Algorithm**
The Steiner Tree Algorithm is an optimization technique used in routing to minimize the total wire length when connecting multiple terminals (or pins) in a circuit.

**Key Features**:
- Minimizing Wire Length: Unlike traditional shortest-path algorithms, Steiner Trees introduce additional points (called Steiner points) to reduce the total wire length needed to connect all terminals.
- Steiner Points: These are points that are not part of the original terminal set but are added to the routing solution to minimize the overall interconnection length.
- Tree Structure: The output of the algorithm is a tree that spans all the terminals (and Steiner points), providing the shortest overall interconnect distance.
**Applications**:
The Steiner tree algorithm is especially useful in global routing where multiple pins need to be connected, such as when routing signal nets in a VLSI design.
It is used to reduce wire delays and minimize routing resources by reducing the total wire length, which can improve the performance and power efficiency of the IC.
**Limitation**s:
- Finding the exact Steiner tree is NP-hard, meaning that it is computationally expensive to find the absolute best solution.
- In practice, heuristic or approximate algorithms like Prim’s or Kruskal’s algorithm are used to solve Steiner Tree problems efficiently.

## **Power Distribution in IC Design**
Power distribution in IC design ensures that all components, including logic gates, memory cells, and other circuits, receive a stable and sufficient power supply from external sources (e.g., power pads or pins). The goal is to minimize issues like voltage drops and noise while ensuring reliable operation.

**Key Concepts:**
- Power and Ground Rails:
VDD (Power) and VSS (Ground): These are the main metal conductors running across the chip, distributing power and ground to all parts. Wide metal lines are used to reduce resistance and prevent significant voltage drops.
- Power Grids:
 A mesh-like structure of horizontal and vertical metal lines (on multiple layers) that ensures uniform power distribution across the entire chip.
- VDD Grid: Carries supply voltage.
- VSS Grid: Carries ground potential.
**Power Rings:**
Metal rings surrounding key blocks (e.g., memory or large logic blocks) on the chip to provide stable power and ground supplies.
They reduce noise and help maintain a steady power supply to critical areas.
**Power Straps:**
Wider metal lines that connect power grids to external power pads or sources, ensuring reliable power delivery and reducing resistance.
**Decoupling Capacitors:**
These capacitors are placed close to power-consuming circuits to stabilize voltage by compensating for sudden current spikes and filtering noise.
**Power Network Routing**
Power network routing is the detailed process of distributing the power supply across the chip, ensuring all blocks receive adequate power without excessive voltage drop or noise.

Steps in Power Network Routing:
- Placement of Power Pads:
Power pads (for VDD and VSS) are strategically placed on the periphery or internally to connect the internal power distribution network (PDN) to external power supplies.
- Creation of Power Grid:
A network of metal layers is laid out as the power grid, spanning multiple metal layers (lower layers for local power and upper layers for global distribution).
- Power Rings and Straps:
Power Rings: Surrounding key blocks, these rings ensure stable power delivery.
Power Straps: Used to connect power rings to the global power grid and ensure efficient current flow.
- Via Placement:
  Vias connect metal layers in the power grid. Using multiple vias reduces resistance and ensures reliable power delivery.
- IR Drop Analysis:

Ensures voltage drop across the grid is within acceptable limits. IR drop refers to the drop in voltage due to the resistance of metal interconnects. Excessive IR drop can cause circuit malfunction.
- Electromigration Check:
High current densities can cause electromigration, the gradual movement of metal atoms, which can eventually break the interconnects. The power network must be checked to ensure current densities remain below safe limits to avoid this issue.
- Noise and Decoupling:
The power network is designed to minimize ground bounce and power noise. Strategically placed decoupling capacitors stabilize the power supply and absorb noise spikes.

![image](https://github.com/user-attachments/assets/67e8e124-d900-44e9-86b2-ce530101b6ea)

## TritonRoute
TritonRoute is a detailed routing engine that is part of the TritonEDA framework, an open-source physical design tool suite developed for digital integrated circuit design. TritonRoute focuses on the detailed routing stage in VLSI physical design and offers several advanced features for handling the complexities of modern IC routing.

**Key Features of TritonRoute:**
- Layer Assignment:
Multi-layer routing: TritonRoute efficiently assigns routing paths across multiple metal layers, optimizing for routing resources while meeting design rules and constraints.
- Design Rule Checking (DRC):
TritonRoute ensures that the routed layout adheres to manufacturing design rules set by semiconductor foundries, including spacing, width, and via requirements. The tool automatically fixes minor DRC violations that arise during routing.
- Congestion Management:

It actively manages routing congestion by identifying and rerouting paths to balance the usage of routing resources and prevent bottlenecks.
- Pin Access Optimization:
The tool includes advanced algorithms to improve pin accessibility, ensuring that all pins in standard cells or macros can be efficiently connected during routing.
- Via Optimization:
TritonRoute optimizes via insertion to minimize resistance and improve reliability. It places multiple vias where necessary to avoid electromigration issues and reduce IR drop.
- Crosstalk and Signal Integrity:
It implements strategies to minimize crosstalk between adjacent signal lines, which could otherwise lead to signal integrity issues in high-frequency designs.
- Timing and Power Optimization:
TritonRoute ensures that routed paths meet timing constraints by minimizing wire lengths and improving signal propagation. It also helps reduce power consumption by optimizing the overall interconnect structure.
- Fault Tolerance and Redundancy:
The routing engine provides built-in support for handling manufacturing defects by generating alternative routing paths and ensuring redundancy to improve yield.
- Parallel Processing:
TritonRoute uses multi-threading and parallel processing techniques to handle large-scale designs efficiently, reducing the overall runtime for complex routing tasks.
**Integration with OpenROAD:**
TritonRoute is integrated into the OpenROAD flow, allowing for seamless use in an end-to-end open-source digital design flow. It interacts with other tools like OpenDB for database management and OpenSTA for timing analysis.
**Applications:**
- TritonRoute is used in the detailed routing phase of physical design for ASIC and SoC development.
- It is particularly useful in academic research and for companies looking for cost-effective, open-source solutions for physical design.

![image](https://github.com/user-attachments/assets/1b4d707c-2508-4d19-8d4a-a9569fa99dcc)
![image](https://github.com/user-attachments/assets/0f829b98-759c-4f57-aee1-15437a7e26a7)
![image](https://github.com/user-attachments/assets/82e8a49f-5342-44d1-b94c-a796174c62dd)


** Lab practice **
- First go to the folder openlane
- run the docker
- run the command
  ```package require openlane 0.9 ```
- now ``` prep -design picorv32a -tag 22-09_11-03 ```
- ```
  set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
  add_lefs -src $lefs
  ```
- now run the synthesis,floorplan,placement and cts
- now generate pdn using the command ``` gen_pdn```
![WhatsApp Image 2024-09-29 at 12 18 56_5e5420a3](https://github.com/user-attachments/assets/8ef7377b-6829-4921-b211-dfad6c817acc)
- now run the routing using the command ``` run_routing ```
- check for drc violations
![image](https://github.com/user-attachments/assets/11ec44ba-d057-4e1a-9df3-adbd54c6729f)
![image](https://github.com/user-attachments/assets/3d75988f-541a-4e7c-92fc-bca7a9dfa021)
![image](https://github.com/user-attachments/assets/fb2ea6d8-39b0-45da-bda6-28f81c72a234)

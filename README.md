# VSD SoC Design

## **Day-1**
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
// path for floorplan folder
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
// First run on open lane
run_placement
//go to placement folder which is created in results and type the commmand
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
  // type the command in the tcl window
  lef write
```







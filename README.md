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








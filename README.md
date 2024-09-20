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




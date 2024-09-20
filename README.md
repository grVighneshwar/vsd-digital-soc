# VSD SoC Design

## **How to open the tool openlane?**

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

## **Setting up the files for the design**
```
prep -design picorv32a
```
> Merges LEF's
> to run the synthesis
```
run_synthesis
```

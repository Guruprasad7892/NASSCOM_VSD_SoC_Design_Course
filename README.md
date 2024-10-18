# NASSCOM_VSD_SoC_Design_Course
In this course, we will go through the process of designing an ASIC (Application Specific Integrated Circuit) from the RTL (Register Transfer Level) to the GDS (Graphical Data System)

# Day-1 : Introduction to Open-source EDA, OpenLANE and sky130 PDK
## Implementation
## Day 1 tasks:-
### a) Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
### b) Calculate the flop ratio.

### Flop ratio = Total Number of D flip flops / Total Number of Cells
### Percentage of DFF's = Flop ratio * 100

## a) Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs
    
```
  # Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```

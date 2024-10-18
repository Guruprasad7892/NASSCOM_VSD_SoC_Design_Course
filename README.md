# NASSCOM_VSD_SoC_Design_Course
In this course, we will go through the process of designing an ASIC (Application Specific Integrated Circuit) from the RTL (Register Transfer Level) to the GDS (Graphical Data System)

# Day-1 : Introduction to Open-source EDA, OpenLANE and sky130 PDK
## Implementation
## Day 1 tasks:-
### a) Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
### b) Calculate the flop ratio.

### Flop ratio = Total Number of D flip flops / Total Number of Cells
### Percentage of DFF's = Flop ratio * 100

## a) Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
    Commands to invoke the OpenLANE flow and perform synthesis
*/ 
  # Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
*/

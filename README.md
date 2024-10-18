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
![lab1_1](https://github.com/user-attachments/assets/d4ecdca9-f9a3-4512-a52a-cbdaf63b37c2)

![lab1_2](https://github.com/user-attachments/assets/b3d7ede4-472a-4296-b497-9a6def046b58)

![lab1_3](https://github.com/user-attachments/assets/d20b7341-c6a6-4837-ac52-ea0b8537209a)

![lab1_4](https://github.com/user-attachments/assets/375ecf93-9c1b-413a-8d3d-4d7c0cbf6477)

![lab1_5](https://github.com/user-attachments/assets/2e1b4ef4-b2ad-418c-8195-e5c52fa756ea)

![lab1_6](https://github.com/user-attachments/assets/1340e63d-f911-45a5-b07b-16c8794788e9)

## b) Calculate the flop ratio.

![s1](https://github.com/user-attachments/assets/cf15a91f-d29d-4d7d-bde6-0672f98f082e)

### total no.of cells=14876
### no.of d_ff=1613
### flop_ratio=(1613/14876)=0.1084296853993009
### Percentage= flop_ratio*100=10.84296853993009%

# Day 2 - Good floorplan vs bad floorplan and introduction to library cells

## Tasks to be completed
### a) Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
### b) Calculate the die area in microns from the values in floorplan def.
### c) Open a new terminal to load the generated floorplan definition in the Magic tool and explore the layout.
### d) Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.
### e) Load generated placement def in magic tool and explore the placement.

## a) Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
```
# Change directory to openlane flow directory
 cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e 
PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```
//invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

//input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

//prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

//Now that the design is prepped and ready, we can run synthesis
run_synthesis

// ready foe floorplan
run_floorplan
```
![lab2_1](https://github.com/user-attachments/assets/aa00bc36-65eb-4f3f-9d6c-f04954b5206d)

![lab2_2](https://github.com/user-attachments/assets/12666406-9326-4e27-980d-9f12b2d5b99e)

![lab2_3](https://github.com/user-attachments/assets/5dc76238-b3c7-4222-9aa0-e5a87fadd972)

![lab2_4](https://github.com/user-attachments/assets/7b75692a-46fe-4981-95ad-b20853a0bfb7)

![lab2_5](https://github.com/user-attachments/assets/747f5da6-7138-4b68-8cf2-0e1fbce45dc6)

![lab2_6](https://github.com/user-attachments/assets/7c3ca205-1ad3-48a8-97e9-5e4dbd1475ee)

## b) Calculate the die area in microns from the values in floorplan def.

### Die width in units=660685/1000=660.685 (in microns)
### Die height in units=671405/1000=671.405
### Area of Die = 660.685*671.405 = 443587.212425 square microns

## c) Open a new terminal to load the generated floorplan definition in the Magic tool and explore the layout.

```
//Change directory to newly generated floorplan def file
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/11-10_06-41/results/floorplan/

// command to run floorlan def file in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![p1](https://github.com/user-attachments/assets/f0bf621b-18b7-48c9-8c35-b8c5bd372b67)

![p2](https://github.com/user-attachments/assets/b36b045d-31b4-4a29-96ef-d04d43ead00c)

![p3](https://github.com/user-attachments/assets/d4ac20a1-cbe4-448b-bd18-ec32cfed9bd4)

![p4](https://github.com/user-attachments/assets/4498c388-51c2-4039-adcd-9f5cbcc688b9)

![p5](https://github.com/user-attachments/assets/44d77364-22f4-4619-b686-9192d1dcf26e)

## d) Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.

![rp1](https://github.com/user-attachments/assets/45ed0bca-70d4-41d7-8527-d70ad6ba37c1)

## e) Load generated placement def in magic tool and explore the placement.

```
// change directory to newly generated placement file in another terminal
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/11-10_06-41/results/placement/

// command to run placement def fie in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![rp2](https://github.com/user-attachments/assets/89dd76f3-dda5-4bb3-b494-73de08138d2d)

# Day3 - 

## Task to be completed
### a) Cloning the custom inverter standard cell design from github repo
### b) Load the custom inverter layout in magic and explore.
### c) Spice extraction of inverter in magic
### d) Spice technology file, simulation and output graph
### e) Parameters Calculation
### f) Identify issues in the DRC section of the old Magic tech file for the SkyWater process and resolve them.

## a) Cloning the custom inverter standard cell design from github repo
```
change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

enter command to clone github repo
git clone https://github.com/nickson-jose/vsdstdcelldesign

after cloning change directory
cd vsdstdcelldesign

copying the Magic tech file in vsdstdcelldesign
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech 

command to open custom inverter design in magic tool
magic -T sky130A.tech sky130_inv.mag &
```
![q1](https://github.com/user-attachments/assets/1ddda6c0-7f0a-4336-af23-5fc2b885e3e9)

## b) Load the custom inverter layout in magic and explore.

![q2](https://github.com/user-attachments/assets/e0281358-cd0a-4c21-8ab8-117476e2c344)

![q3](https://github.com/user-attachments/assets/b6c3ea0a-c17a-44c0-bb62-deb4f01efce0)

## c)  Spice extraction of inverter in magic
```
command to check directory in which you are present
pwd

command to run for extraction of file to .ext format
extract all

command to enable parasitic Extraction
ext2spice cthresh 0 rthresh 0

command to convert ext to spice file format
ext2spice
```
![g1](https://github.com/user-attachments/assets/11f0838d-d7eb-418b-a0d3-6c501d1417de)

## d) Spice technology file, simulation and output graph

![2](https://github.com/user-attachments/assets/0ac90374-6acf-4c00-a215-32ee429209c2)

![1](https://github.com/user-attachments/assets/e1eee3eb-6f12-4e87-a309-f7f05807ed8d)

## e) Parameters Calculation

### 20% 





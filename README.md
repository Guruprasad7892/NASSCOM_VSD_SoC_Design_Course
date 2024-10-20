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

![4](https://github.com/user-attachments/assets/2a26ee75-886d-4d9c-bc9e-126d2cf67747)

![3](https://github.com/user-attachments/assets/45bf77dc-5a95-4d2a-b7f9-850e757eef77)

### 80%
![5](https://github.com/user-attachments/assets/ce0bbd77-2724-417c-b3b8-da98c344ceaf)

![6](https://github.com/user-attachments/assets/c7b6bc59-b103-4867-b0ee-997db9900cd5)

![7](https://github.com/user-attachments/assets/253f9d10-a35a-45d4-b886-44b728a573ee)

![8](https://github.com/user-attachments/assets/8c6b1ff4-b28a-4530-9ea7-896403fe5233)

![9](https://github.com/user-attachments/assets/736a24dd-5dd0-4337-a058-f01d0b41b145)

![10](https://github.com/user-attachments/assets/33ff10bb-0a17-4c93-bdb2-537ab7f735f8)


### 50%
![11](https://github.com/user-attachments/assets/6e07a9ea-f907-4afd-90b7-a0d41a473ee3)

![12](https://github.com/user-attachments/assets/357fcaae-0f48-4822-9539-09b601d1e3e9)

![13](https://github.com/user-attachments/assets/ad14aacb-1609-42c9-a809-dae6ebfa5d01)

![14](https://github.com/user-attachments/assets/525304e2-1538-4e31-bea6-5204d108ace5)

## f) Identify issues in the DRC section of the old Magic tech file for the SkyWater process and resolve them.

![p1](https://github.com/user-attachments/assets/9a36e9b1-a2eb-43eb-9eeb-a3346229fcd8)

![p2](https://github.com/user-attachments/assets/27da3f8e-097a-4002-b286-dbf4a72d1fdc)

![p3](https://github.com/user-attachments/assets/e2d244a7-12cd-4b13-bf5c-9e047a073956)

![p4](https://github.com/user-attachments/assets/4e6a6086-5a0d-4c09-80b2-b4804093197c)

![p5](https://github.com/user-attachments/assets/c3d19792-c6e2-40d4-86db-35fa5c887daf)

# Day4 - Pre-layout timing analysis and importance of good clock tree.

## Task 1: Fix minor DRC errors and verify the design for flow insertion.
```
# Change directory to the vsdstdcelldesign folder
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
```
```
# Open the custom inverter layout in Magic
magic -T sky130A.tech sky130_inv.mag &
```

### Track Information of sky130_fd_sc_hd
 a) The track information for the standard cell library sky130_fd_sc_hd is shown below. This will be used to verify the alignment and dimensions of the custom inverter cell.


![j1](https://github.com/user-attachments/assets/96a8ed1e-3112-40e6-97af-dcb83a2dc653)


 ```
# Get syntax for the grid command
help grid
```
```
# Set grid values for track alignment (locali layer)
grid 0.46um 0.34um 0.23um 0.17um
```

![j2](https://github.com/user-attachments/assets/4437e224-781c-404e-8ac8-0a31467d2177)

### Condition 1: Port Alignment on Tracks

Verified that the input and output ports of the custom inverter cell are aligned at the intersections of vertical and horizontal tracks.

### Condition 2: Width Verification

The width of the standard cell should be an odd multiple of the horizontal track pitch 0.46𝜇𝑚
Horizontal track pitch=0.46 umWidth of standard cell=1.38 um=0.46×3

This condition is satisfied as the width is an odd multiple.


![j3](https://github.com/user-attachments/assets/24165e79-a614-4e21-98d9-a6026d439eb1)



### Condition 3: Height Verification

The height of the standard cell should be an even multiple of the vertical track pitch 0.34𝜇𝑚
Vertical track pitch=0.34 umHeight of standard cell=2.72 um=0.34×8

This condition is satisfied as the height is an even multiple.

![j4](https://github.com/user-attachments/assets/a626ec46-ad30-478d-bc65-de82de43cc36)

```
  # type the command in the tcl window
  lef write
```
```
# Copy lef file
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
# Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

![v1](https://github.com/user-attachments/assets/a5433c8f-ca28-453d-91f7-9bd1c983f310)

```
prep -design picorv32a -tag 22-09_11-03
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```
![v2](https://github.com/user-attachments/assets/ff3f0272-338d-4d5c-ad30-59f360f3c980)


![v3](https://github.com/user-attachments/assets/12ffb8cd-8c88-48af-b9e4-9e5fce66b375)


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

![v4](https://github.com/user-attachments/assets/a0062b7e-e06a-4b75-8087-c330662a005d)

```
init_floorplan
place_io
tap_decap_or
```

![g1](https://github.com/user-attachments/assets/f52db066-5c77-436a-9f28-946034b97bc7)

![g2](https://github.com/user-attachments/assets/7d230cba-b779-4d1e-a5f5-b480745f7c0e)

![g3](https://github.com/user-attachments/assets/c678a345-70be-4bb9-b5ac-d3138c139b55)

![g4](https://github.com/user-attachments/assets/277a3e8d-4bb7-4696-9066-39cd594b16d9)

```
sta pre_sta.conf
```

![c1](https://github.com/user-attachments/assets/76231d8e-84de-4864-830c-dbffc6ded866)

![c2](https://github.com/user-attachments/assets/2e65d480-6725-425f-b88f-c36fa8c55e91)

![c3](https://github.com/user-attachments/assets/2e9b4a69-b168-46c0-adbf-558b26ce07e9)

![c4](https://github.com/user-attachments/assets/712d6665-0051-4748-8bf9-5489fa4e1b56)

```

write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/picorv32a.synthesis.v
```

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
# Day-5 

```
First go to the folder openlane

run the docker

run the command package require openlane 0.9 

now prep -design picorv32a -tag 22-09_11-03

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

now run the synthesis,floorplan,placement and cts

now generate pdn using the command  gen_pdn
```

![n1](https://github.com/user-attachments/assets/d6deb9ac-1ed0-44d1-b45b-f2370bc0ff6f)

```
now run the routing using the command run_routing

check for drc violations
```


![n2](https://github.com/user-attachments/assets/b93d1406-c322-41bf-b0f0-86041984ee20)

![n3](https://github.com/user-attachments/assets/e0782165-591c-4551-867d-c56d0c58448a)

![n4](https://github.com/user-attachments/assets/e85656d3-c2e0-4919-ad7e-bdcd60eea13f)

Post-Route parasitic extraction using SPEF extractor.
```
cd Desktop/work/tools/openlane_working_dir/openlane/scripts/SPEF_EXTRACTOR

# Command extract spef
python3 main.py /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-09_11-03/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-09_11-03/results/routing/picorv32a.def
```
Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

```
openroad
read_lef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/tmp/merged.lef
read_def /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.def
write_db pico_route.db
read_db pico_route.db

read_verilog /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```


![n5](https://github.com/user-attachments/assets/65b42450-f4da-47f1-a1c1-b847b8a17d13)

![n6](https://github.com/user-attachments/assets/7491a239-de4d-4275-b751-253da630e5a9)

![n7](https://github.com/user-attachments/assets/bd7275e4-7815-4db2-a6f3-36d22fdfcf97)

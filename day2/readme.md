## Day2
### Chip Floor Planning Considerations
**Utilization Factor and Aspect Ratio**
1) Defining width and height of core and die
Consider a netlist with flip-flops and combinational logic. We use combinational logic in terms of blocks to calculate the area.

![image](https://github.com/KKiranR/Pes_pd/assets/89727621/81b84cc8-f5f6-43ae-a0a2-4eef16f0efe1)
- We consider a simple netlist with a Launch and Capture Flop. It also has an AND and an OR gate.
- We then convert it into squares since we need appropriate dimensions
  
![image](https://github.com/KKiranR/Pes_pd/assets/89727621/4cdbf4fb-ff1d-4123-8062-5cce546012f3)

- Let us consider the areas of the gates and Flops as 1 sq unit

  ![image](https://github.com/KKiranR/Pes_pd/assets/89727621/06ba6004-c236-42ee-826d-a52631fb8de8)
- Clubbing them together, we get an area of 4 square units
- The 'core' section of a chip is where the fundamental logic design is placed.
- The 'die' area contains the core and is a small semiconductor area on which the fundamental circuit is fabricated.

![image](https://github.com/KKiranR/Pes_pd/assets/89727621/015b67a2-ba55-4b3e-a86d-6d11bbfc45a8)

- Now we put the netlist in the 'core' area and check the utilization. Using the formula

  ```Utilization Factor = Area Occupied by the Netlist/Total Area of the Core```
  
- As we can see here, there is 100% utilization, and ```Utilization Factor = 1.```
- In practical scenarios, we don't go for such a high utilization factor.
- The 'Aspect Ratio = Height/Width = 1'.
**Concept of Pre Placed Cells**
- We take the below combinational logic as an example
![image](https://github.com/KKiranR/Pes_pd/assets/89727621/1e0fec8d-92e6-4967-86dc-c84b5ec1ba04)

**Running floorplan **
Use Command ```run_placement``` to run the placement 

![Screenshot from 2023-09-15 16-44-26](https://github.com/KKiranR/Pes_pd/assets/89727621/3bb29b33-397b-4069-bd26-c15e6cdd30a3)

After Running this command, the placemnt def file is created inside the dir runs/placememt

![Screenshot from 2023-09-15 16-44-59](https://github.com/KKiranR/Pes_pd/assets/89727621/84b3d680-2555-41a7-b4fb-02b73a0afaba)

 Use magic commands to veiw the schematic of placed design

 ```magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def```
 
 ![Screenshot from 2023-09-15 16-47-28](https://github.com/KKiranR/Pes_pd/assets/89727621/49fcff35-8bc4-4e01-9611-816e3a94015b)

![Screenshot from 2023-09-15 16-47-13](https://github.com/KKiranR/Pes_pd/assets/89727621/1c3c40f1-6c94-4ddb-bf5e-262bf44d7278)


**Cell Design and Characterization Flow**
**Cell Design Flow**

- Inputs -> Process design kits(PDKs) : DRC and LVS rules, SPICE models, library and user-defined specs.
- Design Steps -> Circuit Design, Layout Design(Euler Path and Stick Diagram), Characterization.
- Outputs -> CDL(Circuit Description Language), GDSII, LEF, extracted spice netlist(.cir)

**Characterization Flow For Inverter**

 Step-1:Read the model files.
 
 Step-2:Read the extracted SPICE netlist.
 
 Step-3:Recognize the behaviour of the buffer.
 
 Step-4:Attaching the necessary power sources
 
 Step-5:Apply the stimulus, which is the input signal to the circuit.
 
 Step-6:Read the sub-circuit of the inverter.
 
 Step-7:Provide necessary output capacitances.
 
 Step-8:Provide the necessary simulation commands
 
** Timing Characterization**
- slew_low_rise_thr = 20%
- slew_high_rise_thr = 80%
- slew_low_fall_thr = 20%
- slew_high_fall_thr = 80%
- in_rise_thr = 50%
- in_fall_thr = 50%
- out_rise_thr = 50%
- out_fall_thr = 50%
- Propogation delay = time(out_fall_thr) - time(in_rise_thr)
- Transition Time
  - On rise: time(slew_high_rise_thr) - time(slew_low_rise_thr)
  - On fall : time(slew_high_fall_thr) - time(slew_low_fall_thr)

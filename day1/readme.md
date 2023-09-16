## SoC Design and OpenLANE
**What is a PDK?**

PDK stands for Process Design Kit.
- It is a collection of files used to model a fabrication process for the EDA tools used to design an IC
  - Process Design Rules.
  - Device Models
  - Digital Standard Cell Libraries
  - I/O Libraries
### A simplified RTL to GDSII Flow is :

- Synthesis -> Floor/Power Planning -> Placement -> Clock Tree Synthesis -> Routing -> Signoff
- Synthesis - Converts RTL to a ciruit, out of compomments from the standard cell library.
- Floor and Power Planning - Obejctive here is to plan the silicon area and create robust power distribution network to power the chip.
- Chip Floor Planning - Partition the chip die between different system building blocks and place the I/O pads.
- Macro Floor Planning - We define the macro dimensions, pin locations and rows are defined.
- Power Planning - The power distribution network is contructed.
- Placement - Placing the cells on the floorplan rows, aligned with the sites. There are 2 steps: Global and Detailed.
- Clock Tree Synthesis - To deliver the clock to all sequential elements.
- Routing - Implement the interconnect using the available metal layers.
- Sign Off - Perform physical verification such as DRC(Design Rule Check) and LVS(Layout vs Synthesis). Also perform STA(Static Timiing Analysis).

**OpenLANE ASIC Flow**

![image](https://github.com/KKiranR/Pes_pd/assets/89727621/1e22d2c9-fa89-4942-a3bb-0b238862e0ee)

### Getting fimilarising with OpenSource EDA tools
- To run the openlane in the VM go to the directory ```work/tools/openlane_working_dir/openlane```
- we will be using picorev32a which is present in the directory ```designs/picorv32a```
- initally when we open the file loaction we will not have any runs directory as we havent prepare our design
#### Working with openlane 
- Enter the follow comands to work with openlane pdk and prep the design
  ```
  #### You should be in the directory /Desktop/work/openlane_working_dir/openlane
  doker
  ./flow.tcl -interactive
  ```
  ![image](https://github.com/KKiranR/Pes_pd/assets/89727621/9f7ffea4-4e00-4d6c-8983-216586dce8a2)
- Now to prep the design run the following command ```prep -design picorev32a``` after running this command we will see a new directry created called as run
  ![image](https://github.com/KKiranR/Pes_pd/assets/89727621/535b29ef-7d3d-47bd-875b-89a851cf3598)
- Now to run synthesis run the following command ```run_synthesis```
  
  ![Screenshot from 2023-09-15 15-51-19](https://github.com/KKiranR/Pes_pd/assets/89727621/69c39f50-57bc-49f2-b86a-0fc9fc29e939)
  
- From these results the flop ratio is calculate by the formula ```number of flops/total number of cells``` in this case it is equal to 0.108
- After running the synthesis there will be a netlist file created under the folder runs
  ![image](https://github.com/KKiranR/Pes_pd/assets/89727621/89ea4981-7b76-43da-a857-3000a3ca4fc0)

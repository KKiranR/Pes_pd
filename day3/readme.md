# Day3
**IO Placer Revision**
- We can set the different optimizations using the command ```set :: ```
we are setting the IO mode to 2 by the following command
```bash
set ::env(FP_IO_MODE) 2
```
## Inception of Layout and CMOS Fabrication Process
**Spice deck Considerations**
- component connectivity
- component values
- identifying the nodes
- giving a designation to the nodes

![Screenshot from 2023-09-19 10-50-54](https://github.com/KKiranR/Pes_pd/assets/89727621/9969dc2e-4913-4b28-b3bf-d4b83536348e)

**SPICE Simulation and Switching Threshold**

![image](https://github.com/KKiranR/Pes_pd/assets/89727621/5e1ca133-7318-4b9c-a6c3-c755d640500d)

- The CMOS on the right side has a bigger size than the one on the left.
- These waveforms tell us that the CMOS is a very robust device. The characteristics of the CMOS are maintained across a variety of sizes.
- The arrow is pointing to the point where 'Vin = Vout'.

  ![image](https://github.com/KKiranR/Pes_pd/assets/89727621/c85f813b-b74b-4efc-8f08-1db5a00cc547)

**Opening the Inverter from the github **
 - Clone the repository
   ```bash
   git clone https://github.com/nickson-jose/vsdstdcelldesign.git
   ```
- copy the technology file which is in pdks directory  to the repository using the command
  ```bash
  cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
  ```
- To open the schematic  using the command
  ``` bash
  magic -T sky130A.tech sky130_inv.mag
  ```
![image](https://github.com/KKiranR/Pes_pd/assets/89727621/57f56c80-c849-496f-b179-a258c4916bee)

**16 Mask CMOS Process**
1)Selecting a Substrate - Selecting the appropriate substrate to synthsize the design on.

2)Creating active reagion for transistors - Adding layers of SiO2(40nm), Si3N4(80nm) and photoresist(1um). On top of the photoresist we put a mask layer. Pass UV light and remove the mask. Resist is removed. LOCOS(Local Oxidation of Silicon) is performed. Si3N4 is etched.

3)N-Well and P-Well formation - The next masks are used to create the source and drain regions of the MOSFETs. Boron is used to make P-Well using ion implantation. Phosphorus is used to create N-Well. Put the MOSFET in a Drive In furnace.

4)Formation of Gate - Gate formation involves depositing a gate oxide, defining gate patterns using photolithography, depositing gate material, etching to create gates, doping the substrate and insulating the gates.

5)Lightly Doped Drain Formation(LDD) - Lightly doped drain (LDD) formation involves implanting the drain and source regions of a MOSFET transistor with a lighter concentration of dopants to reduce hot electron effect and short channel effect and enhance device performance.

6)Source and Drain Formation - Source and drain formation in a MOSFET transistor typically involves doping the silicon substrate with chemicals such as arsenic or phosphorous for n-type regions (source and drain) and boron for p-type regions (source and drain). High temperature annealing is performed.

7)Steps to form Contacts and Interconnects(local) - Titanium is deposited with a process known as sputtering. Wafer is heated to about 650 - 700 C in an N2 ambient furnace for 60 seconds. TiSi2 contacts are formed. TiN is also formed used for local communication. TiN is etched using RCA cleaning.

8)Higher Level Metal Formation - Forming contacts and interconnects locally involves depositing a dielectric material like silicon dioxide, patterning it using photolithography, etching contact holes, depositing a barrier metal (e.g., titanium or titanium nitride), filling with a conductor (e.g., aluminum or copper) using chemical vapor deposition (CVD), and then planarizing through chemical-mechanical polishing (CMP).

**Sky130 Basic Layers Layout and LEF using Inverter**
- To extract the spice file use the following commands
  ```bash
  pwd
  extract all
  ext2spice cthresh 0 rthresh 0
  ext2spice 
  ```
![Screenshot from 2023-09-19 11-35-00](https://github.com/KKiranR/Pes_pd/assets/89727621/9f0aa6a1-95aa-4de8-91d0-8f47a0df2708)
- To View the extracted spice file use the command ```gedit sky130_inv.spice```
  ![image](https://github.com/KKiranR/Pes_pd/assets/89727621/9b535fcb-8243-44bc-a365-cad964efce91)
The above file has details of inverter netlist but the sources and their values are not specified. So we have to modify the file.

- Grid size from the layout is 0.01u

- specify the library for MOS

- create VDD, VSS, Input pulse Va

- specify the type of analysis to be done

![image](https://github.com/KKiranR/Pes_pd/assets/89727621/db184f78-7b57-41b7-bfa8-d7ca582fd72d)

To plot the graph run the command ``` ngspice sky130_inv.spice``` and ```plot y vs time a```

![Screenshot from 2023-09-19 12-14-56](https://github.com/KKiranR/Pes_pd/assets/89727621/1b901b07-fa24-45a1-8735-f9ed7320faf6)

**Results :**

![image](https://github.com/KKiranR/Pes_pd/assets/89727621/a5cf35ff-4bba-4e04-8057-56a17f20d7c3)



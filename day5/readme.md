# Day5

## Power Distribution Network and Routing

**Build Power Distribution Network**

- To do this first we type
```
gen_pdn
```
![Screenshot from 2023-09-22 16-07-32](https://github.com/KKiranR/Pes_pd/assets/89727621/1676d93e-622a-4d65-9fb2-9bed66539f50)

![Screenshot from 2023-09-22 16-14-23](https://github.com/KKiranR/Pes_pd/assets/89727621/3b000a22-3fb6-479f-bb19-15d6f357f2ed)

- We see that there is a change in the DEF.
- To run the rounting we type
  ```
  run_routing
  ```.
- To check for DRC errors we need to check the 'tritonRoute.drc' folder
- To extract the parasitics we need to use an extractor engine.
- We use the SPEF Extraction.

**SPEF Extraction**
- To use this engine we need to go to
```
cd Desktop/work/tools/SPEF_Extractor
```
- Next we need to use this command
```
python3 /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_19-58/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_19-58/results/routing/picorv32a.def
```
- SPEF file is created in ```/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-09_19-58/results/routing/```

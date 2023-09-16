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

- Now we put the netlist in the 'core' area and check the utilization. Using the formula ```Utilization Factor = Area Occupied by the Netlist/Total Area of the Core```
- As we can see here, there is 100% utilization, and ```Utilization Factor = 1.```
- In practical scenarios, we don't go for such a high utilization factor.
- The 'Aspect Ratio = Height/Width = 1'.
**Concept of Pre Placed Cells**
- We take the below combinational logic as an example
![image](https://github.com/KKiranR/Pes_pd/assets/89727621/1e0fec8d-92e6-4967-86dc-c84b5ec1ba04)


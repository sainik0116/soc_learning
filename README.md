SOC-learning : <details>
           <summary>DAY 1 : TOOL INSTALLATION</summary>
           <p>YOSYS :
           
![Yosys](https://github.com/user-attachments/assets/90c11a4f-d722-4a08-9d82-67972123b419)
![Yosys_tool working snapshot](https://github.com/user-attachments/assets/99f9f510-5b3c-41a4-bce9-2c3401985754)
IVERILOG :

![iverilog    gtkwave](https://github.com/user-attachments/assets/dceb0649-e892-4cf7-873e-c22d8f292a26)
![iverilog_tool_working snapshot](https://github.com/user-attachments/assets/123ebf3e-50cc-4939-ac40-eb151dfc77d3)

gtkwave :

![gtkwave_tool_working_snapshot](https://github.com/user-attachments/assets/6bf15da3-4d17-4ff8-bfbc-0a20e5409c17)</p>
         </details>
SOC-learning :  <details>
           <summary>DAY 2 - Introduction to Verilog RTL Design and Synthesis</summary>
           BLOCK DIAGRAM OF IVERILOG BASED SIMULATION FLOW:
           ![Screenshot (283)](https://github.com/user-attachments/assets/74ccd96d-384d-4249-89a7-7d7580e52a36)
           Simulator:  -> RTL Design is checked for adherence to the spec by simulating the design.
                       -> Simualtor is the tool used for simulating the design. Iverilog is the tool used for this course
           Design : -> Design is the actual verilog code or the set of verilog codes which has the intended functionality
                       to meet with required specifications.
           Testbench : -> Testbench is the setup to apply stimulus(test_vectors) to the design to cehck its functionality.
           How Simulator works :
           -> Simulator looks for the changes on the input signals.
           -> Upon changes to the input the output is evaluated.
           -> If no change to the input, no change to the output
           -> Simulator is looking for change in the values of input.
           BLOCK DIAGRAM OF TESTBENCH
           ![Screenshot (282)](https://github.com/user-attachments/assets/855efcc4-f476-427c-97e2-b25658cfd65c)
           Yosys : -> Tool used for converting the RTL to netlist.
                   -> Yosys is the synthesizer use din the course.
           ![Screenshot (327)](https://github.com/user-attachments/assets/7311b5ac-14a5-46e8-8336-4fef102ef070)
           Gtkwave :  This is the tool used to see the waveforms of VCD files generated after giving testbench and netlist as an inputs to iverilog.
           Netlist is the representation of design in terms of cells present in the .lib
           Verify the synthesis- Block diagram :
           ![Screenshot (287)](https://github.com/user-attachments/assets/f69155c5-8b12-41b8-a0e5-3ed146ea6c63)
SOC-learning :  <details>
           <summary> Day 3 - Timing libs, hierarchical vs flat synthesis and efficient flop coding styles
           Introduction to .lib :
           example of a .lib file is "sky_130_fd_sc_hd_tt_025c_1v80 : describes about process-tt corner , temperature : 25 C , Operating Voltage : 1.8 volts.
           This is specifying at a particular PVT corner, set of cells which were characterised and the information of those cells is given in terms of their timing and output capacitance  for all possible 
           combinations for differrent drive strenghts. We also have  power(leakage, dynamic and static) information also inside the cell. 
           ![Screenshot (301)](https://github.com/user-attachments/assets/09df6fcc-9c75-413c-8c35-0a8d43d92df7)
           ![Screenshot (302)](https://github.com/user-attachments/assets/e73a1414-052b-4349-9c5d-cd0f7910bb9b)
           Showing an example of a mutltiple_modules.v block : hierarchy vs flatten
           First presenting you the basic commands how to synthesize (hierarchy sub-module is taken as an example)
           ![yosys_synth_hier_1](https://github.com/user-attachments/assets/da6fd8fb-af1a-42dd-9ae3-74b085c4d222)
           ![yosys_synth_hier_2](https://github.com/user-attachments/assets/83bd9a4c-f416-4772-8216-930842b469e0)
           ![yosys_synth_hier_3](https://github.com/user-attachments/assets/14c32b9d-e0ec-43da-95cb-d2e5db9962d7)
           ![yosys_synth_hier_4](https://github.com/user-attachments/assets/180c79f6-951b-4991-9f92-f57761caedb2)
           Secondly, showing you the commands history required for falttening the hierarchy:
           ![commands_used_for_hierarchy_flatten](https://github.com/user-attachments/assets/c1e060b2-aba8-46e9-8a1d-8319c0f4c7c9)
           Observation of difference between written verilog code in hier vs flatten:
           ![submodule_flatten_verilog_code_after_synth](https://github.com/user-attachments/assets/22402a81-085b-453b-a0d0-513dfe216240)
           ![submodule_written_verilog_code_after_synth_hierarchy](https://github.com/user-attachments/assets/e2978027-bdfb-4160-aed1-c6ee440a52f4)
           One important thing about Synthesis is it always calculate the logical effort of the design and take appropriate cells from the .lib during synthesizing the circuit for optimisation.

           Advantages of Sub-module synthesis
           1.) When we have multiple instances of same module, we can save time by synthesizing the sub-module once and use it multiple times.
           2.) Divide and conquer : Let's say we have a massive design, which is unable to synthesize the netlist properly, we can break the netlist into couple of sub-modules , synthesize and stitch it later.

           Why flops ?,  A very important topic
           -> So, theoritically if we observe Glitch is one of the important reasons we went to the flops.
           -> With the flops in between the combinational circuit will actually prevent the glitches.
           Giving you the screenshot of the explanation :
           ![Screenshot (304)](https://github.com/user-attachments/assets/1fca88d0-3420-48d5-a7a2-1b1772739073)
           Different types of flops effiecient coding styles :
           Here we are looking into four flops coding styles:
           1.) ASynchrounous-reset
           2.) Synchronous-set
           3.) Asychrounous-reset-Synchrounous-reset
           4.) Asynchrounous-set
           We will not use syncres_asyncres.v d-ff because we will end up in the race around condition:
           ![Screenshot (303)](https://github.com/user-attachments/assets/9743ad75-1d70-4b4e-b597-0eee03997b4d)
           
           

           
           



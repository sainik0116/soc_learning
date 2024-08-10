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
           </details>
SOC-learning :  <details>
           <summary>Day 3 - Timing libs, hierarchical vs flat synthesis and efficient flop coding styles</summary>
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
           </details>
SOC-learning :  <details>
           <summary>Day 4  - Combinational and sequential optmizations</summary>
           There are some images of hand-wriiten notes I want to share with you for Combinational and sequential circuits logic optmization:
           Bare with my hand-writing , but it is really good info given in the videos i just wanted to share some of the knowledge I gained.
           ![WhatsApp Image 2024-07-30 at 6 11 15 PM (1)](https://github.com/user-attachments/assets/4db27caa-1b7b-48cf-9953-64c7adc43b19)
           ![WhatsApp Image 2024-07-30 at 6 11 15 PM](https://github.com/user-attachments/assets/cf5248b3-c5a8-4b29-9a67-ed15a3a6ddf0)
           ![WhatsApp Image 2024-07-30 at 6 11 16 PM](https://github.com/user-attachments/assets/dbcde17d-1c35-4090-a331-730c969f0be1)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (1)](https://github.com/user-attachments/assets/6039d4b9-dbb3-4195-902b-e50f2cc341ab)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (2)](https://github.com/user-attachments/assets/18330b16-7411-4403-9f39-646ab8ac3f1e)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (3)](https://github.com/user-attachments/assets/c1ff989c-bf36-4477-95f4-7d56a64af252)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (4)](https://github.com/user-attachments/assets/ca3cef79-fc32-4c5b-a9ed-ee5f857d2f8a)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (5)](https://github.com/user-attachments/assets/61f95dbe-b651-41a7-8ed3-52cd1d4e3b54)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (6)](https://github.com/user-attachments/assets/8ca9315c-f1f6-4bee-87ba-5f9ff3c194fc)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (7)](https://github.com/user-attachments/assets/34126f45-44d3-43b4-be87-8888911b74e4)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (8)](https://github.com/user-attachments/assets/d4ccab45-c82d-49f7-896a-a31a870352b0)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (9)](https://github.com/user-attachments/assets/0f1136ab-9df7-4f6a-a5c2-8dc3939a60b1)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (10)](https://github.com/user-attachments/assets/a68649af-dbef-48e8-9a20-aa3317fd35e4)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM (11)](https://github.com/user-attachments/assets/be7d25ea-6a82-43d5-a9aa-c73e327ff3e0)
           ![WhatsApp Image 2024-07-30 at 6 11 17 PM](https://github.com/user-attachments/assets/f30a6c51-17af-4ee3-ab0a-d05729b81569)
            Logical-optimisation :
           I am providing you a simple example of a mux optimised to and gate.
           Here are the screenshots of the optimisation :
           ![Screenshot (328)](https://github.com/user-attachments/assets/6e3002c3-537b-4651-af21-41cb9c027b50)
           ![Screenshot (329)](https://github.com/user-attachments/assets/949ad744-423a-4b9a-ba76-4000e4efa6e4)
           ![Screenshot (330)](https://github.com/user-attachments/assets/e63ee733-9180-48b8-8334-627342e0a976)
           Some of the advanced techniques explained for optimisation :
           1.) Cloning : So, in this technique if the slack between the launch flop to the capture flop is more then we can clone the launch flop closer the capture flop to optimise the timing.
           2.) Retiming : This means we can adjust the combinational logic between the flops to make the worst(setup of flop1, setup of flop2) to a better setup timing.
           Example of what i am speaking about will be available in the below screenshot .
           ![Screenshot (309)](https://github.com/user-attachments/assets/9dc8834f-866f-4f42-8ed9-b7f8337634fd)
           </details>
           SOC-learning :  <details>
           <summary>Day 4 - GLS, blocking vs non-blocking and Synthesis-Simulation mismatch</summary>
           What is GLS ?
           -> Running the testbench with netlist as Design under test
           -> Netlist is logically same as RTL code.
              * Same testbench will align with the design.
           why GLS ?
           -> Verify the logical correctness of design after synthesis.
           -> Ensuring the timing of the design is met.
              * For this GLS needs to be run with delay annotation.(Outisde the scope of this discussion)
           ![Screenshot (335)](https://github.com/user-attachments/assets/32520423-4675-41f7-9aaf-9fb909483c65)
           We will do GLS synthesis to check the functionality because of Synthesis simulation mismatch, 
           In the below screenshots you can observe some of the reasons for Synthesis simulation mismatch.
           ![Screenshot (336)](https://github.com/user-attachments/assets/1e2a1164-e002-420d-a9d5-d5ac74cff877)
           ![Screenshot (338)](https://github.com/user-attachments/assets/b8668877-90bd-4fb3-a736-441aebc4cb4b)
           Missing Sensitivity list :
           let us take an example of mux 2 x 1,
           if we only provide select line as an input to the sensitivity list this will break the logic because as we know that in simulation when the input changes then only the output changes . So, if the input lines are not provided to the mux in the sensitvity list then output does not change if input (i0 or i1) changes keeping the sel line constant.
           Giving you the screenshot of the missing sensitivity list.
           ![Screenshot (316)](https://github.com/user-attachments/assets/1f3f62bc-28dd-435b-9227-02b24edf1b41)
           Blocking and Non-blocking Statements in verilog :
           -> Inside always block
              * =  Blocking 
                executes the statements in the order it is written.
                So, the first statement is evaluated before the second statement.
              *  <= Non-blocking
                  Executes all the RHS when always block is entered and assigns to LHS.
                  Parallel evaluation.
             LAB work example to show bad_mux: 
             Which has the sensitivity Mismatch problem:
             Before GLS :
             Commands used before GLS :
             ![bad_mux_commands_before_GLS-1](https://github.com/user-attachments/assets/5194dcd6-a5d5-47e6-90a6-4869bd444526)
             Waveform to be observed how sensitivity list is effecting the output before GLS:
             ![Before_GLS_waveform_bad_max](https://github.com/user-attachments/assets/07ff8b96-b415-4f66-8246-21701388b6b1)
             Here, Output changes only when the sel line changes, it is independent of changes in the input. This is not desirable!.
             After GLS :
             ![bad_mux_commands_used_after_GLS](https://github.com/user-attachments/assets/5dceedb4-1b8c-4786-aa37-13bd2953ec29)
             ![bad_mux_commands_after_GLS-1](https://github.com/user-attachments/assets/ac4d75ed-e442-43e0-936d-83f3d6066512)
             
             We can clearly observe after the GLS ,the synthesised netlist is giving the waveforms where output changes when the input changes as well as sel line changes.
             So, This synthesized netlist will give us the mismatch and let us know that there is a correction in the RTL. So, hence the significance of the GLS(Gate level synthesis is explained).</p>
             </details>
SOC-learning : <details>
           <summary>DAY 5 : INTRODUCTION TO LOGIC SYNTHESIS</summary>
           ![Screenshot (348)](https://github.com/user-attachments/assets/ed03062e-ced0-479c-922a-d58fcf52bf9d)
           ![Screenshot (349)](https://github.com/user-attachments/assets/8e0e0516-d500-43f5-a891-3f6172b9d698)
           ![Screenshot (351)](https://github.com/user-attachments/assets/05a61fdd-45b7-446c-8f9b-73388273e793)
           Digital logic helps us to deisgn the logic we want in real life applications like PC's,laptops, Washing machines etc.       
           We know that logic synthesis is  been done through synthesizing the rtl code.
           How did we do this ? .We will explain it in the next slide .
           ![Screenshot (352)](https://github.com/user-attachments/assets/cf43c6e6-0b42-4961-a6c3-374afe2c3c4e)

           Now we need to understand what is .lib ? .lib is the file which helps us to pick the right cell for the rtl logic in the synthesis. This depends on several factors like PVT corners, timing, power , drive strength  etc.
           So, when we synthesize the rtl logic we need to know which cells are required to meet the setup and hold violations , which cell has the better performance and less area.
           So, mainly the challenge engineers face is to optimise the PPA(Power,Performance and Area) . This is the , most important part in the whole VLSI design.
           ![Screenshot (354)](https://github.com/user-attachments/assets/a2f79ccd-37f9-4921-a6e1-a26965b33961).
           Then next comes to understand the significance of why we require the different types of cells in the .lib file and how we deal with this when we optimise the timing for the design.
           This is been explained in the next slides.
           ![Screenshot (355)](https://github.com/user-attachments/assets/c0ce811d-f5a8-4237-9bf9-bfaac45b99c0)
           ![Screenshot (356)](https://github.com/user-attachments/assets/62928bd6-2dac-44da-aa4e-06add0eadf50)
           ![Screenshot (357)](https://github.com/user-attachments/assets/4203518b-c509-440a-b870-215c079c0166)
           ![Screenshot (358)](https://github.com/user-attachments/assets/447251e1-18b4-4a43-8933-8ff07f5978ef)
           ![Screenshot (359)](https://github.com/user-attachments/assets/0f50c628-5918-46cb-8220-98f3531f9e39)
           ![Screenshot (360)](https://github.com/user-attachments/assets/688baf92-b232-46a5-9f0a-804b0bd3e221)
           Here i am gonna explain the synthesis illustration from a slide given.
           So, when we give an rtl code we know that we can synthesize the rtl code into gate level blocks .
           ![Screenshot (361)](https://github.com/user-attachments/assets/531d2f30-f336-4461-bc85-c5483f59571b)
           Now, we have to understand the significance of the constraints.
           How constraints are helpful in understanding which design is required for the application .
           Here is the slide which presents three implementations for a rtl code .
           ![Screenshot (362)](https://github.com/user-attachments/assets/4546c90d-583b-4fd1-be73-f8146d71b163)
           Let us know analyse which implementatation is the best 
           ![Screenshot (363)](https://github.com/user-attachments/assets/6adc6b1e-2fa1-46a2-a358-6b7affa4bd39)
           ![Screenshot (365)](https://github.com/user-attachments/assets/98a69b2c-c928-47f5-9364-c0e4049ccb17)
           Now from the explanation in the slides , we caanot confirm that implentation is always the best . Because we will take a coarse example which says that hold time is not meeting with the implentation 3 then we cannot prefer implementation 3.
           ![Screenshot (367)](https://github.com/user-attachments/assets/412cb933-5152-4381-93b9-891d41685089)
           ![Screenshot (368)](https://github.com/user-attachments/assets/626758df-15a5-4456-b77c-6bdbc08d3622)
           So, to decide which implemenatation is the best we need to know the constraints first.
           


           

           
           



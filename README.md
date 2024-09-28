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
             So, This synthesized netlist will give us the mismatch and let us know that there is a correction in the RTL. So, hence the significance of the GLS(Gate level synthesis is explained).
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
           INTRODUCTION TO DC COMPILER
           DC compiler is the mostly used synthesis tool in the VLSI industry , This tool is developed by synopyss EDA vendor .
           Here are the slides which explain how dc_compiler synthesizes the rtl logic.
           Through slides we will understand how the rtl code gets sythesized , what is the terminlogy used in the industry for sythesis. Then we will get to know. Then we will understabnd the ASIC flow at top level and then we will understand how DC compiler flow will work at the top level through the block diagrams.
           ![Screenshot (370)](https://github.com/user-attachments/assets/abe0bfbe-3540-40ce-8f75-8904c8360298)
           ![Screenshot (373)](https://github.com/user-attachments/assets/7fe1459e-0b79-4a94-b15a-2bfd3af7eee5)
           ![Screenshot (374)](https://github.com/user-attachments/assets/dfa1d820-f45f-4f90-93a6-9e58a465fe02)
           ![Screenshot (377)](https://github.com/user-attachments/assets/53c7c71b-afe1-4b56-93a1-56e66b6a1473)
           ![Screenshot (379)](https://github.com/user-attachments/assets/bf9d5b30-2e17-4ec5-b19b-52fecc0a2f9d)
           ![Screenshot (380)](https://github.com/user-attachments/assets/9b45a871-b0de-4386-8f6e-dd0d48a0e8b8)
           I am providing you some of the lab work I had done with DC compiler tool .
           ![Screenshot (397)](https://github.com/user-attachments/assets/950a36c4-ce7c-458c-847a-de18deb12486)
           ![Screenshot (398)](https://github.com/user-attachments/assets/c5325f49-33c8-4590-a199-4fc8b5fcdd34)
           ![Screenshot (399)](https://github.com/user-attachments/assets/eca3ee7d-960e-47c2-a740-daec9e304a00)
           ![Screenshot (400)](https://github.com/user-attachments/assets/a4ccbfb1-f98f-45dd-95aa-582a9fd1fd14)
           ![Screenshot (401)](https://github.com/user-attachments/assets/57851f14-3419-4f88-bc9b-b8d18609018e)
           ![Screenshot (402)](https://github.com/user-attachments/assets/c8f1b3d6-5699-4e36-8235-16649b33ce9f)
           I am also giving you some lab notes I prepared.
           ![WhatsApp Image 2024-08-10 at 3 01 28 PM](https://github.com/user-attachments/assets/b5296c2b-71a4-46af-882d-5551a481f731)
           ![WhatsApp Image 2024-08-10 at 3 01 40 PM](https://github.com/user-attachments/assets/71f83071-cf09-4d6e-803f-569244dd705c)
           ![WhatsApp Image 2024-08-10 at 3 01 54 PM](https://github.com/user-attachments/assets/50049d84-f421-4bf5-8e24-2cb3117e7ec3)
           </details>
           
SOC-learning : <details>
           <summary>DAY 6 : BASICS OF STA(Static Timing Analysis)</summary>
           First slide explains:
           Max delay constraint : Constraint which says that this is the max delay we can have in the design to make it function normally. If it is more than this it will effect the performance. (Setup time)
           Min delay constarint : Constarint which says that this is the min delay constarint we can have in the design , so that the design will not get it's performance deteriorated. (Hold time)
           ![Screenshot (408)](https://github.com/user-attachments/assets/989fc8d4-43c4-465d-ac8e-98c9b6a6bccc)
           Now, we will understand this water bucket analogy while analysing what are the factors that gonna effect the delay.
           ![Screenshot (409)](https://github.com/user-attachments/assets/cf27e67a-3d6c-4884-a32e-d95c0b2bf3c5)
           ![Screenshot (412)](https://github.com/user-attachments/assets/a9fd146d-2aba-4846-9099-526323cf9c0f)
           Water Bucket analogy says that the delay of the cell is the function of input transition and ouptut capacitance.
           ![Screenshot (415)](https://github.com/user-attachments/assets/11ef81af-e106-470c-bfea-ccc6a616e264)
           Here is something we need to understand about timing arcs in comabinational and sequential circuits:
           They are useful in the analysis of the delay in a cell.
           ![Screenshot (416)](https://github.com/user-attachments/assets/e6a8e1c5-7bd5-464f-afdc-9b8c2095ae7a)
           ![Screenshot (420)](https://github.com/user-attachments/assets/e5bdb40d-37a9-4689-836f-74282f4a46f7)
           Now, we need to understand the timing paths. This is really important when you do physcial design beacause, we need to know the worst case scenario of the design to know what frequency can it work on without breaking the functionality. This paths are generally called as critical paths.
           ![Screenshot (425)](https://github.com/user-attachments/assets/de1fd449-7042-46f1-8acc-bf0d9d528811)
           Here is one of the beautiful explanation given regarding a design and how to model the design by considering the constraints. 
           ![Screenshot (426)](https://github.com/user-attachments/assets/7bad3e15-ae2e-456e-8909-0e8a9875c1c8)
           ![Screenshot (428)](https://github.com/user-attachments/assets/fa06479a-4a49-4b5e-bd8c-8742947dda03)
           ![Screenshot (429)](https://github.com/user-attachments/assets/11a2ab87-f432-465d-99a2-4cdc1f94afe8)
           ![Screenshot (430)](https://github.com/user-attachments/assets/3d4c4bec-a1ad-4009-959b-0b127af81d50)
           ![Screenshot (431)](https://github.com/user-attachments/assets/50568dfa-d113-4ea9-a907-52aff451640f)
           ![Screenshot (432)](https://github.com/user-attachments/assets/6bcf7855-b5c9-46db-b9fe-bb97bdedf63c)
           ![Screenshot (433)](https://github.com/user-attachments/assets/d15bb8ee-cf35-48ea-8841-86318854089a)
           ![Screenshot (434)](https://github.com/user-attachments/assets/770fff06-b215-4b7d-8774-516a11b70248)
           ![Screenshot (435)](https://github.com/user-attachments/assets/81a354f0-7e48-4405-bc7c-921822a588e6)
           ![Screenshot (436)](https://github.com/user-attachments/assets/007dd20a-bc4a-4dff-83f7-932d697a95d7)
           ![Screenshot (437)](https://github.com/user-attachments/assets/4d6587cd-8e36-4b40-9ba8-e40c41f7e182)
           ![Screenshot (438)](https://github.com/user-attachments/assets/7f99c05f-3361-42a6-8fea-bd6f56bd2d64)
           ![Screenshot (439)](https://github.com/user-attachments/assets/0176fd07-1cdf-4e9d-a344-811edd4d80d8)
           ![Screenshot (440)](https://github.com/user-attachments/assets/ed75ee75-0c21-49bc-abd8-15b3bbaa5676)
           ![Screenshot (441)](https://github.com/user-attachments/assets/45a0c7ed-4cf9-4c4c-97f3-370d97e8c5c0)
           ![Screenshot (442)](https://github.com/user-attachments/assets/76fb2e94-3bf0-404f-ac36-fca94b079b82)
           So, here we took only analyzed the setup time , we should also analyze the hold time for IO paths.
           There is another important concept called as timimg unateness . 
           Which helps us to know the timing sense of the block present in the .lib.
           ![Screenshot (451)](https://github.com/user-attachments/assets/277cd9aa-c1c8-4515-9f31-1a433152d508)
           This is what some of the lab work which helped me to understand  DC compiler tool , practice this stuff 
           ![Screenshot (454)](https://github.com/user-attachments/assets/c749f391-1327-4bf5-ae0b-eebe76e006de)
           ![Screenshot (455)](https://github.com/user-attachments/assets/d719e9b0-1dfb-4eba-9f4d-bfc7ff98218f)
           ![Screenshot (456)](https://github.com/user-attachments/assets/9d38651d-3587-4ce0-85c3-9e15f55c0db7)
           ![Screenshot (457)](https://github.com/user-attachments/assets/e1b02e7e-b6be-4a7e-8ec9-94a3669d6842)
           ![Screenshot (458)](https://github.com/user-attachments/assets/79961ac0-1c98-4f9f-9532-bddc3a6c248a)
           ![Screenshot (459)](https://github.com/user-attachments/assets/1ab810b3-1767-4be9-b991-f835731a45af)
           ![Screenshot (460)](https://github.com/user-attachments/assets/8dd5c0d5-28ed-4abb-a91d-5b724dc784c2)
           ![Screenshot (461)](https://github.com/user-attachments/assets/325b48b4-b475-4dd4-b658-bcd24560384e)
           ![Screenshot (462)](https://github.com/user-attachments/assets/1ddc94c7-0cdc-4e70-8de4-6df3d4ebbd27)
           ![Screenshot (463)](https://github.com/user-attachments/assets/6347f81c-9913-4dd4-99e1-115717e24965)
           ![Screenshot (464)](https://github.com/user-attachments/assets/2d010e68-43e0-47a3-83fd-89caabbfc935)
           ![Screenshot (465)](https://github.com/user-attachments/assets/4ede5a97-9e60-4c85-bd36-f93c34247dfe)
           ![Screenshot (466)](https://github.com/user-attachments/assets/70a150d0-2ec8-4513-a2fa-8a0472bab0b4)
           ![Screenshot (467)](https://github.com/user-attachments/assets/e7664ce7-8268-420e-9b2c-5ef70c7dd75d)
           ![Screenshot (468)](https://github.com/user-attachments/assets/8a8f80ae-06d6-43f4-bee6-2430cb058720)
           ![Screenshot (469)](https://github.com/user-attachments/assets/2009c2df-1892-4561-be22-097c7e3bd1b4)
           ![Screenshot (470)](https://github.com/user-attachments/assets/72a79b10-267e-4496-afad-bb2f667545a2)
           ![Screenshot (471)](https://github.com/user-attachments/assets/fa7b9533-fd12-4d81-94ee-8938b3094534)
           ![Screenshot (472)](https://github.com/user-attachments/assets/23d5ce1c-068b-4bcf-83fa-adfa132deaf8)
           ![Screenshot (473)](https://github.com/user-attachments/assets/7eceff97-c894-434c-bad7-1a6c913d4f37)
           </details>
           
SOC-learning : <details>
           <summary>DAY 7 : INTRODUCTION TO BABY SOC MODELLING</summary>
           What is a SoC and Why SoC should be used ? :
A System on a Chip (SoC) is an integrated circuit that consolidates all the necessary components of a computer or other electronic system onto a single chip. These components typically include:

Central Processing Unit (CPU): The primary processor responsible for executing instructions and managing tasks.
Memory: Such as RAM and ROM, for temporary and permanent data storage.
Input/Output (I/O) Ports: Interfaces for communication with other devices and peripherals.
Graphics Processing Unit (GPU): Handles rendering of images and video.
Digital Signal Processor (DSP): Specializes in handling audio and video processing.
Other specialized modules: These can include wireless communication components (e.g., Wi-Fi, Bluetooth), power management circuits, and sensors.
Key Advantages of SoCs :

Size Reduction: Integrating multiple components into a single chip significantly reduces the overall size of the device.
Power Efficiency: SoCs typically consume less power than systems with discrete components because of optimized interconnections and reduced need for external interfaces.
Performance: Close proximity of components can lead to faster data transfer rates and improved overall performance.
Cost Efficiency: Manufacturing a single chip can be more cost-effective than producing multiple separate components, leading to lower production costs for the end devices.
Reliability: Fewer interconnections between separate components reduce the likelihood of failure due to connection issues.
Common Applications of SoCs :

Smartphones and Tablets: SoCs are fundamental in mobile devices due to their compact size and efficiency.
Wearable Devices: Such as smartwatches and fitness trackers, which require compact and power-efficient processing.
IoT Devices: Internet of Things (IoT) devices often use SoCs to handle various sensors and connectivity tasks.
Embedded Systems: Used in automotive, industrial, and consumer electronics for dedicated processing tasks.
Examples of Popular SoCs :

Apple A-Series: Used in iPhones and iPads.
Qualcomm Snapdragon: Found in many Android smartphones.
Samsung Exynos: Used in Samsung devices.
NVIDIA Tegra: Used in devices like the Nintendo Switch.
Challenges and Considerations :

Design Complexity: Integrating multiple functions onto a single chip is complex and requires sophisticated design and manufacturing processes.
Heat Management: Concentrating multiple components in a small area can lead to heat dissipation issues, which need to be managed effectively.
Flexibility: SoCs are less flexible than discrete systems because they are highly integrated and customized for specific applications.
Overall, SoCs play a crucial role in modern electronics by enabling more compact, efficient, and powerful devices.

Types of SoC :
• SoCs built around a microcontroller • SoCs built around a microprocessor, often found in cell phones • Specialized application-specific integrated circuit SoCs designed for specific applications that do not fit into the above two categories

SoC Structure :
• An SoC consists of hardware functional units, including microprocessors that run software code, as well as a communications subsystem to connect, control, direct and interface between these functional modules. • Functional components: Processor Cores, Memory, Interfaces, Digital Signal Processor, others • Intermodule communication: Bus-Based Communication, Network on a chip.

SoC Design Flow :
SoC development process can be broken into multiple stages as illustrated in the following figure:
SoC Design Flow
Specification and Planning:

Define the system requirements, including performance, power, area, and functionality.
Choose the target applications and markets.
Architecture Design:

Develop the overall architecture, including CPU, GPU, memory, and peripherals.
Define the interconnect scheme and data flow.
Component Selection:

Choose standard IP cores (e.g., processors, memory controllers) or design custom components.
Ensure compatibility and integration capability of all components.
Integration and Verification:

Integrate the chosen components into a unified design.
Perform extensive verification using simulation, emulation, and formal methods to ensure functionality and performance.
Physical Design:

Perform synthesis to convert the high-level design into a gate-level netlist.
Conduct floorplanning, placement, and routing to create the physical layout of the chip.
Optimize for power, performance, and area (PPA).
Fabrication and Testing:

Send the final design to a semiconductor foundry for fabrication.
Perform post-fabrication testing to ensure the chip meets specifications.
Software Development:

Develop and optimize software to run on the SoC, including drivers, operating systems, and applications.

Ensure seamless integration between hardware and software components.

![SOC-designlifecycle-ezgif com-webp-to-jpg-converter](https://github.com/user-attachments/assets/a00144f8-e7f4-42b6-bec7-086b784e2490)

Introduction to VSDBabySoC :
VSDBabySoC is a small yet powerful RISCV-based SoC. The main purpose of designing such a small SoC is to test three open-source IP cores together for the first time and calibrate the analog part of it. VSDBabySoC contains one RVMYTH microprocessor, an 8x-PLL to generate a stable clock, and a 10-bit DAC to communicate with other analog devices.
![357534769-d7dcc6b8-e7dd-4fed-be88-7991e110a4eb](https://github.com/user-attachments/assets/e6cf23f7-489a-4c02-81de-09e51ed3dde5)

BabySoC Components
RVMYTH
RVMYTH: The RVMYTH core is a simple RISC V-based CPU designed for educational purposes and small-scale applications. It provides a practical example of a RISC-V processor implementation.
PLL
Phase-Locked Loop (PLL): A phase-locked loop or PLL is a control system that generates an output signal whose phase is related to the phase of an input signal. PLLs are widely used for synchronization purposes, including clock generation and distribution.
DAC
Digital-to-Analog Converter (DAC): A DAC is a system that converts a digital signal into an analog signal. DACs are widely used in modern communication systems, enabling the generation of digitally-defined transmission signals.

REFERENCES:
https://github.com/Subhasis-Sahu/SFAL-VSD?tab=readme-ov-file#what-is-a-soc-and-why-soc-should-be-used--
https://github.com/vpamidi9/sfal-vsd-venkatesh

Note :

RVMYTH is designed and created by the TL-Verilog language. So we need a way for compile and transform it to the Verilog language and use the result in our SoC. Here the sandpiper-saas could help us do the job.
Step-by-Step process of modelling :
Install These Required Packages:

 $ sudo apt install make python python3 python3-pip git iverilog gtkwave docker.io
 $ sudo chmod 666 /var/run/docker.sock
 $ cd ~
Step-by-Step process of modelling :

1.)  While installing pip there are some challenges I faced while downloading the sandpiper-saas
 ![pip-sandpiper-error](https://github.com/user-attachments/assets/ed4a499d-ac2d-43ba-96e0-fa2698474099)
 The work-around which helped to overcome the problem of downloading the sandpiper -saas
 ![work-around-fixing-pip-sandpiper-saas-module](https://github.com/user-attachments/assets/2f2eb6d9-b037-4d13-99f2-8e93df99a5b6)
 ![sandpiper-saas screenshot](https://github.com/user-attachments/assets/6fbb6d59-2ef2-4a10-a3c8-9ef3929d04f4)
 
2.)
 ```
git clone https://github.com/manili/VSDBabySoC.git - clone this repo containing VSDBabySoC design files and testbench.

cd /home/sai-goutham/VSDBabySoC

sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/ - to translate .tlv definition of rvmyth into .v definition.
```
It will generate following .v files rvmyth.v and rvmyth_gen.v.

view the ouput vcd file: cd /home/sai-goutham/VSDBabySoC/output/pre_synth_sim.vcd

waveform: DAC output is verified along with out 
![BabySoC_functional_waveforms](https://github.com/user-attachments/assets/edf8c039-6dee-4cda-9afd-a7f841cdbab8)
</details>
SOC-learning : <details>
           <summary>DAY 8 : Post-Synthesis Simulation (GLS) of BabySoC</summary>

#**Why do pre-synthesis Simulation? Why not just do post-synthesis Simulation? :**

Pre-synthesis simulation is done according to the logic we have designed for and written -> only functionality.
Post synthesis simulation / ‘gate level simulation’ is done after synthesis considering each and every gate delays into account. It reports the violations in both functionality and timing.
This also shows the mismatches we are likely to get due to wrong usage of operators and inference of latches.
For ex: using ‘X’(simulator terms/ synthesizer terms) - ‘Unknown’/“Don’t care”.

#**GLS: a brief introduction :**

The term "gate level" refers to the netlist view of a circuit, usually produced by logic synthesis.
So while RTL simulation is pre-synthesis, GLS is post-synthesis.
The netlist view is a complete connection list consisting of gates and IP models with full functional and timing behavior.
RTL simulation is a zero delay environment and events generally occur on the active clock edge.
GLS can be zero delay also, but is more often used in unit delay or full timing mode.
Gate level simulation is used to boost the confidence regarding implementation of a design and can help verify dynamic circuit behaviour, which cannot be verified accurately by static methods. It is a significant step in the verification process.

#**To synthesize the VSDBabySoC design,**
##**Converting .lib file to .db file**

Errors while reading the .lib file 

![errors_encountered_while_read_lib_post_gls](https://github.com/user-attachments/assets/08f4286f-14e3-43b4-baa3-36d8f6aeb0bd)

After rectifying the issue in the .lib file , we are able to read the .lib file successfully while converting .lib file to .db file 

![fixed_errors_while_Read_lib_post_GLS](https://github.com/user-attachments/assets/b9779da9-eaa7-4bc5-bf7d-92c75623ec13)

Convert .lib file to .db file using Synopsys Library Compiler (lc_shell). We need .db format for avsddac.lib, avsdpll.lib & sky130_fd_sc_hd__tt_025C_1v80.lib.

So, just as a heads up , if you are unsuccessful in coverting the .lib to .db files then please installl the sky130_fd_sc_hd__tt_025C_1v80.lib file 
**Use below command to downlaod latest sky130_fd_sc_hd__tt_025C_1v80.lib file:**

wget [https://raw.githubusercontent.com/efabless/skywater-pdk-libs-sky130_fd_sc_hd/master/timing/sky130_fd_sc_hd__tt_025C_1v80.lib](https://raw.githubusercontent.com/efabless/skywater-pdk-libs-sky130_fd_sc_hd/master/timing/sky130_fd_sc_hd__tt_025C_1v80.lib)

Commands I used to convert .lib to db files :
```
cd /home/sai/VSDBabySoC/src/lib
lc_shell
read_lib sky130_fd_sc_hd__tt_025C_1v80.lib
write_lib avsdpll -format db -output sky130_fd_sc_hd__tt_025C_1v80.db
```
This is the output we will see after the coversion of .lib to .db file

![coversion_lib_to_db](https://github.com/user-attachments/assets/c899d1ea-dd28-4fcb-854a-5203b4c803f3)

## Lab - Synthesis and Post Synthesis (Gate Level) Simulation

### Below commands to perform the synthesis:

```
cd /home/sai/VSDBabySoC/
dc_shell
set target_library /home/sai/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.db
set link_library {* /home/sai/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.db /home/sai/VSDBabySoC/src/lib/avsddac.db /home/sai/VSDBabySoC/src/lib/avsdpll.db}
set search_path { /home/sai/VSDBabySoC/src/include/ /home/sai/VSDBabySoC/src/module/}
read_file {sandpiper_gen.vh  sandpiper.vh  sp_default.vh  sp_verilog.vh clk_gate.v rvmyth.v rvmyth_gen.v vsdbabysoc.v} -autoread -top vsdbabysoc
link
compile_ultra
write_file -format verilog -hierarchy -output /home/sai/VSDBabySoC/output/babysoc_netlist.v
report_qor > report_qor.txt
```
### QOR Report
![qor_without_sdc_constraints](https://github.com/user-attachments/assets/23a1a03d-7960-474c-a020-e42a58155a51)
![qor_without_sdc_constraints_2](https://github.com/user-attachments/assets/5c4b92c6-8217-4b25-a272-cb0d98a17765)

### Commands to perform post-synthesis simulation:
```
iverilog -DFUNCTIONAL -DUNIT_DELAY=#1 -o ./output/post_synth_sim.out ./src/gls_model/primitives.v ./src/gls_model/sky130_fd_sc_hd.v ./output/vsdbabysoc_net.v ./src/module/avsdpll.v ./src/module/avsddac.v ./src/module/testbench.v
cd output
./post_synth_sim.out
gtkwave dump.vcd
```
### post-synth and pre-synth wave forms are same :
We see the same output for pre synthesis and post synthesis : (Verified that functionality is same for pre-synthesis and post-synthesis)
#### pre-synth :
![Pre-GLS-BabySoC_functional_waveforms](https://github.com/user-attachments/assets/eaa856f1-7c68-4e34-8d53-a0cb6c5ae1c2)
#### post-synth :
![post_GLS_synthesis_waveform](https://github.com/user-attachments/assets/2ec637cb-f6b7-4c92-b1d1-9881e7afa74d)

## Lab - Synthesis with SDC Constraints
### Synthesis using constraints:
In SDC file we have defined the constrains based on the constrains we will synthesis our design.
Following are the constrains add in the vsdbabysoc_synthesis.sdc file in the folder /home/sai/VSDBabySoC/src/sdc/
```
set_units -time ns
set_max_area 8000
set_load -pin_load 0.5 [get_ports OUT]
set_load -min -pin_load 0.5 [get_ports OUT]
create_clock [get_pins pll/CLK] -name clk -period 10 -waveform {0 5}
set_clock_latency 1 [get_clocks clk]
set_clock_latency -source 2 [get_clocks clk]
set_clock_uncertainty 0.5  [get_clocks clk]
set_max_delay 10 -from [get_pins dac/OUT] -to [get_ports OUT]
set_input_delay -clock clk -max 4 [get_ports VCO_IN]
set_input_delay -clock clk -min 1 [get_ports VCO_IN]
set_input_delay -clock clk -max 4 [get_ports ENb_CP]
set_input_delay -clock clk -min 1 [get_ports ENb_CP]
set_input_transition -max 0.4 [get_ports VCO_IN]
set_input_transition -min 0.1 [get_ports VCO_IN]
set_input_transition -max 0.4 [get_ports ENb_CP]
set_input_transition -min 0.1 [get_ports ENb_CP]

```
### Commands to perform synthesis with SDC constraints:

```
cd /home/sai/VSDBabySoC/
dc_shell
set target_library /home/sai/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.db
set link_library {* /home/sai/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.db /home/sai/VSDBabySoC/src/lib/avsddac.db /home/sai/VSDBabySoC/src/lib/avsdpll.db}
set search_path { /home/sai/VSDBabySoC/src/include/ /home/sai/VSDBabySoC/src/module/}
read_file {sandpiper_gen.vh  sandpiper.vh  sp_default.vh  sp_verilog.vh clk_gate.v rvmyth.v rvmyth_gen.v vsdbabysoc.v} -autoread -top vsdbabysoc
link
read_sdc /home/sai/VSDBabySoC/src/sdc/vsdbabysoc_synthesis.sdc
compile_ultra
write_file -format verilog -hierarchy -output /home/sai/VSDBabySoC/output/babysoc_netlist.v
report_qor > report_qor_sdc.txt
report_timing -nets -attributes -input_pins -transition_time -delay_type max > report_setup_sdc.txt
report_timing -nets -attributes -input_pins -transition_time -delay_type min > report_hold_sdc.txt
```
Compare and observe the differences between qor report before using and after using sdc constraints:

**gvimdiff report_qor.txt report_qor_sdc.txt **

</details>

SOC-learning : <details>
               <summary>DAY 9 : STA analysis  of BabySoC before Floorplanning using Primetime</summary> 
```
cd /home/sai/VSDBabySoC/
Open pt_shell
source sta_mul_pvt_primetime.tcl > my_learning_sta_mul_pvt_primetime_run.txt 
After Successfully running primetime for the design BabySoC
Open sta_mul_pvt_primetime.tcl
```
# Table for all PVT corners for WNS and WHS :
```
PVT_Corner	             WNS	     WHS
ff_100C_1v65	 2.852984	  -0.250917
ff_100C_1v95	 4.220676	  -0.304045
ff_n40C_1v56	 1.592035	  -0.208451
ff_n40C_1v65	 2.574583	  -0.244908
ff_n40C_1v76	 3.444535	  -0.275657
ff_n40C_1v95	 4.447599	  -0.312528
ss_100C_1v40	-18.091564	   0.405345
ss_100C_1v60	-9.315001	   0.142039
ss_n40C_1v28	-55.31789	   1.329605
ss_n40C_1v35	-35.723297	   0.847522
ss_n40C_1v40	-27.194054	   0.624912
ss_n40C_1v44	-22.168922	   0.490901
ss_n40C_1v60	-10.624826	   0.162826
ss_n40C_1v76	-5.055514	   0.003838
tt_025C_1v80	 0.571624	  -0.190414
tt_100C_1v80	 0.418252	  -0.185542  
```
           
           Graph for WNS: Worst negative slack (Setup):
           ![BabySoC_STA_primetime_no_parasitic_WNS](https://github.com/user-attachments/assets/73309255-e2ac-4871-9cdb-90da7ba94ff0)
           Graph for WHS: Worst hold slack(hold):
         
         
           
           













           



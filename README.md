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
 : <details>
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
           

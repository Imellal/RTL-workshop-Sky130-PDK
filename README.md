![Verilog-flyer](https://user-images.githubusercontent.com/68396186/120019036-93aead80-c005-11eb-8d90-11b52d5f81e1.png)
#    RTL_WORKSHOP_using_ OPENLANE_Sky130PDK

5 days workshop on RTL design with Sky130 PDK. 

**-  Day 1: Introduction to Verilog RTL design and Synthesis**

To prepare the environment, OPENLANE and install the Sky130 PDK.

First of all, create a folder named VLSI and clone all the files from https://github.com/kunalg123?tab=repositories
You need to clone 4 repositories: sky130RTLDesignAndSynthesisWorkshop, sky130CircuitDesignWorkshop, vsdflow and SystemDesignWorkshopCollaterals
You can use cd to enter the VLSI folder and 'ls' to show the existing files:
![picture1](https://user-images.githubusercontent.com/48953224/120089643-48aa9e00-c0ca-11eb-98e8-e7fb45dc76e0.jpg)

Once you prepared the environemnt, you can use 'ls' to check all the flies in each folder.
The folder 'sky130RTLDesignAndSynthesisWorkshop' contains all the verilog files needed for this workshop: verilog files and test bench files for all the labs.

![picture3](https://user-images.githubusercontent.com/48953224/120089848-ff5b4e00-c0cb-11eb-8538-35111fabe5a1.jpg)

At this level the setup is done! You can simulate and synthesis your models.
The 'verilog_files' folder contains the verilog file and the associated corresponding test bench file of each project. The test bench file is named with 'tb_FileName.v'
Use 'iverilog' to lood the files: good_mux.v and tb_good_mux.v
Then wwe're going to execute the '.a/a.out' file to dump the dcv file. (out put of the simulator will be cvd file)
After that, you can run the simulator, gtkwave by runing the command: getkwavr tb_good_mux.vcd
You should use the VCD file generated previously, not use the 'tb_File"
The simulator will show all the signals, zoom and select a region for better understanding.

<img width="960" alt="Untitled" src="https://user-images.githubusercontent.com/48953224/120090279-34b56b00-c0cf-11eb-90c8-024063d24a5f.png">

The next figure shows the difference between the two files: good_mux.v and tb_good_mux.v

<img width="823" alt="tb1" src="https://user-images.githubusercontent.com/48953224/120090485-d8ebe180-c0d0-11eb-92a9-a1c7a173bc0e.png">

-----
Synthesizer: yosys
yosys is a synthesyser translating the design using a library into a netlist file. To call yosys, use the command 'yosys'
We will use three commands: 
- read_verilog:to read the design
- Read library: read the .lib file
- write_verilog: write out the netlist file as an outpu which is a representation of the design in form of standard cells 

<img width="641" alt="Untitleed" src="https://user-images.githubusercontent.com/48953224/120090662-3e8c9d80-c0d2-11eb-9a16-73fa10e71803.png">

During the synthesis the RTL is converted into gates and the connections are made between the gates, generating a netlist file.

Synthesis a design:
Invoque yosys with the command: 'yosys'
Once you're in the yosys promp, you should read the library with : 'read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib'

<img width="697" alt="Untitleeed" src="https://user-images.githubusercontent.com/48953224/120090973-b2c84080-c0d4-11eb-9478-fdae82f45aee.png">

You should read the verilog files with 'read_verilog'
The next step is to synthesis the verilog file using the command line: 'synth -top good_mux' Do not put the extension'.v' because it's the name of the top module name.

![image](https://user-images.githubusercontent.com/48953224/120091085-adb7c100-c0d5-11eb-8634-98283cc751fd.png)

Now, you can generate the netlist using the command 'abc liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib'
abc is the command to convert the rtl file into gate level and we need to specify the library file to be used. 
It shows all the cells and the resurces used. 
We can use the command 'show' to show the graphical logic that has beed realized.

<img width="1013" alt="abc" src="https://user-images.githubusercontent.com/48953224/120091252-66323480-c0d7-11eb-9e61-c8b97c237e3d.png">









**-  Day 2: Timing library hierarchical vs flat synthesis and efficient flop coding styles**

**-  Day 3: Combinational and Sequential optimization**

**-  Day 4: GLS, blocking vs non-blocking and Synthesis-Simulation mismatch**

**-  Day 5: Day 5 - If, case, for loop and for generate**


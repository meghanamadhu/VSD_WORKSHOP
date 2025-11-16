DIGITAL SoC Design Workshop 
Day 1   
 Launch the openlane using the below openlane: 
 
                                         cd Desktop/work/tools/openlane_working_dir/openlane 
                                         docker
                                        ./flow.tcl -interactive
                                         (Add image)
                                          package require openlane 0.9

There are already almost 40 designs in the design folder.(Add image)

                                       cd picorv32a
                                       cd src
                                       cd ../
                                       less config.tcl
The command to be run in the open lane window for design preparation is : 

                                    prep -design picorv32a
(Add Image)
After the design preparation stage a runs directory is created(in the normal window) 

                                  cd runs/16-11_06-11
                                  cd tmp
                                  less merged.lef
In the merged.lef File there will be cell information, metal layer information and so on.
Now go back one directory:

         cd ../
         cd results (Add Image)
Now go the openlane prompt
Run the below command for Synthesis:

                                run_synthesis
The synthesis step will take 3-5 minutes to complete the design.
The information about openlane can be obtained using
             efabless openlane
Inside the synthesis directory we can get the opensta timing and synthesis reports.
(Add Image)
Day2 - Good Floorplan v/s Bad floorplan and introduction to library cells.

Width and height of core and die.
We are trying to find the width and height of core and die.
(Add Image)

A die which consist of core is small semiconductor material specimen on which the fundamental circuit is fabricated.
Utilization Factor = Area occupied netlist/Total area of the core
Aspect ration = Height / Width

DEFINE LOCATIONS OF PREPLACED CELLS

<img width="1562" height="1038" alt="WIDTH_HEIGHT" src="https://github.com/user-attachments/assets/4c47cc31-c5a1-4a43-9ab3-56f491172d07" />
 
We can separately implement the blocks of circuits and can be reused multiple times.
<img width="2019" height="1039" alt="image" src="https://github.com/user-attachments/assets/b98568e8-e1d7-43cb-a638-2613606d20ca" />
A combinational ogic will do a particular function.
The placement of these cells is known as Floor planning.
<img width="2434" height="893" alt="image" src="https://github.com/user-attachments/assets/d06d37fc-109e-4546-84ae-c53ee30d8ebf" />
The placement of these cells will be fixed and will not touched by automated placement and routing tools.
Having a large physical distance from the power supply to the output voltage will result in a large drop in voltage and the output voltage can lie in an undefined voltage range.
<img width="2309" height="1082" alt="DECOUPLING_CAPAC" src="https://github.com/user-attachments/assets/68287cf3-5dc9-4368-90a8-3f229fe4f0c0" />
This porblem can be solved by decoupling capacitor.
<img width="2253" height="990" alt="image" src="https://github.com/user-attachments/assets/5e2665f3-bdb8-41e5-bc6d-b499299e5cc3" />

The decoupling capacitor can be used to decouple from the main supply.
It is used to charge the capacitor.
When there is switching activity happening it will charge to VDD.
<img width="2293" height="1045" alt="image" src="https://github.com/user-attachments/assets/638b5590-103a-4569-a65f-4bd5ef86e49b" />
Thereby local communication is handled.
Global communication is implemented using the concept of Power planning.
POWER PLANNING
<img width="1892" height="930" alt="image" src="https://github.com/user-attachments/assets/107cd6b3-9ac3-42ef-bf23-5d5a84ea06d6" />
<img width="1892" height="930" alt="image" src="https://github.com/user-attachments/assets/dccabc3f-2a95-4eb8-a6e5-347b514b156c" />
PIN PLANNING
Netlist
The connection between gates is written suing Verilog/VHDL and the connection is known as Netlist.
<img width="1916" height="1076" alt="image" src="https://github.com/user-attachments/assets/8ab47f04-34f7-4304-bb42-d5fb50860197" />
The above circuit has 4 input ports Din, 2 clock ports, 4 output ports.
The placement of pins is completely upto the designer.

The ordering of input ports comes random.
The clock signal plays a major role as the whole flipflop circuit is driven by the clock signal.
Hence it is important to make least resistance path is given to clock signal path.
<img width="1982" height="990" alt="image" src="https://github.com/user-attachments/assets/b7e4d17a-6143-493c-bff7-b2e2621e4613" />
Logical cell placement blockage
<img width="2245" height="1000" alt="image" src="https://github.com/user-attachments/assets/fe04d57b-e676-442a-94d0-93c5ca0ac7c9" />
This makes sure that the automated placement and routing tool doesnot place cells in that area.\
This area is reserved for the pin locations. 


FLOORPLANNING LABWORK 

Go to the configuration directory.
Within the directory there will be many tcl files and a README.md file.
<img width="637" height="477" alt="image" src="https://github.com/user-attachments/assets/e682569a-6639-4047-81a0-dbb8a9eef7af" />

IN the README.Md file the floorplanning,cts , utilization factor and all such values are defined.
<img width="569" height="104" alt="image" src="https://github.com/user-attachments/assets/557c1396-aaf1-4a8d-b62b-c8c53e067667" />
Run the following command to do floorplanning.

              run_floorplan
<img width="559" height="260" alt="image" src="https://github.com/user-attachments/assets/cf7e8e83-190e-4eb5-8876-fdb8714e19f6" />
The floorplan configuration can be seen inside the runs directory.
Go to the directory,
/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/16-11_12-25
<img width="558" height="380" alt="image" src="https://github.com/user-attachments/assets/a03b5563-c642-491f-a29a-6a9eeb6fce03" />

MAGIC LAUNCH
To launch Magic use the following command,

   magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &


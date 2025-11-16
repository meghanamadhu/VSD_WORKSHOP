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
The placement of these cells will be fixed and will not touhed by automated placement and routing tools.

# localisation-robot

1.	Connect the Power Supply to turn on the Jetson
2.	Also connect the 4 cell battery to turn on the servo
3.	 To access Jetson on the robot we need the VNC Viewer application installed on the Laptop and a LAN cable connected from Jetson to the Laptop by entering Jetson's IP address for example "192.168.123.12"
4.	 Once connected, the Ubuntu interface on Jetson will appear on our laptop
5.	 Turn on the Jetson fan with the following command “sudo ./jetson_clocks.sh”
6.	 To display the Localization GUI on the robot we need to go to the BarelangFC_2021 Folder then go to the BarelangFC_Particle_Filter_Sim folder then go to the Source-Codes folder with the command in the terminal 
7.	After running the python program, go to the BarelangFC_2021/Strategy/main.cpp folder with the command cd "BarelangFC_2021/Strategy/" inside there are several files then open the main.cpp and BarelangFC_Odometry.cpp files
8.	. The Localization GUI itself has a function to measure the percentage of distance errors made by the robot with the actual position
9.	. In this localization, we do a step test step, take the servo step data, after that fix the servo data in the odometry.cpp file. After the servo data has been confirmed, then test the steps again, and finally run the GUI and see in the picture the percentage of errors that occur
10.	. In the main.cpp file look for case 1001 (usually) where in that case there is a step test, and take step data from the foot servo to run case 1001 don't forget to fill in firststatecondition = case 1001
11.	. For the step test, there are 4 commands to display the foot servo data for the self-step test, namely walTot (forward), wakTot_mun (backward), csm_kiri (left), and csm_kanan (right) using the Walk variable. Then there are three numbers to fill in the speed (0.0, 0.0, 0.0) (x,y,theta). X functions for forward and backward values, for forward containing values (0.03 to 0.06), for backward containing values (-0.01 to -0.03). Y functions for left and right values, for left contains values (0.01 to 0.03), for right contains values (-0.01 to -0.03). Theta functions for left and right rotation values, left rotation contains values (0.0 to 0.4) and for right rotation contains values (-0.0 to -0.4)
12.	. To take servo data, turn off/command program for step test in case 1001 or in case of odometry calculation. If you want to take forward and backward data, fill in the value of X, for left and right data, fill in the value of Y, for rotational data, enter the value of Theta. If you want to take servo silent data, fill in 0.0 all the X, Y, and Theta values (0.0,0.0,0.0)
13.	. If you get servo data issued by the program through the terminal, then copy and paste the data into excel to make a graph to find out the upper limit (inm) and lower limit (out) on the servo data of the left servo legs totaling 6 and the right 6 as well
14.	. After filling in the servo odometry data for the upper and lower limits, we test the steps again by turning off/command the printf servo data command and turning on the step test program in case 1001 in the Strategy/Main.cpp program
15.	. After that set the position initialPos_X = 0; initialPos_Y = 0; countInitPos = 1; //0&1, 0 already has X and Y values, 1 follows X and Y values (X and Y position of the original robot according to the Localization GUI grid). moveGrid(44,0,0) = to specify the position you want to go to.
16.	. Save all the edited program files then compile the program with the command “./ok.sh” , then reset it with the command “./reset.sh”, then kill it with the command “./killall.sh”, then execute the program with the command "./BarelangFC"
17.	. After we have analyzed the percentage of GUI error Localization in the program with the robot's original position in the field, if the error means that we need to replace the appropriate odometry data so that the position is good
18.	attachment

# Xinput-test
## Description
This is the c++ code that utilizing Microsoft XInput Game Controller API to gain control inputs from the joystick, process the inputs, and send out to the UR3 robot controller. Outputs containing the Game controller actions and timestamps will be written into csv file called <filename>-event-timestamp.csv.
The code is originally developed using Visual Studio solution.



## Requirements and Dependencies
- It relies on XInput API so a Windows machine is required to run this code. XInput is a built-in Windows component, so you do not need to download it manually.
- Boost library is required for timer, socket, and other operations.
- The definition of the message structure sending to UR3 robot controller is in the directory 5gRemoteOperation/rccommonlib


## Compiling and Linkage Pre-requisites
- The VelocityControllerMessage.cpp and common.h are linked through solution to 5gRemoteOperation/rccommonlib. Need to take good care of the path.
- This code has been validated working with oost library boost_1_84_0
- Need to add <windows.h> for xinput reference
- Need to add <xinput.lib> to the linker  
- Note that windows.h uses winsock.h and boost:assio uses winsock2. So if you need to include both library, you need to include boost::assio before windows.h, or follow the solution in https://stackoverflow.com/questions/9750344/boostasio-winsock-and-winsock-2-compatibility-issue


## Parameters setup
These parameters should be characterized based on different scenarios and requirements:
- serverPort: The destination port number of the UDP server. It can also be set through -p option through command line.
- serverAddr: The destination IP address of the UDP server. It can also be set through -a option through command line.
- out_filename: The output csv filename. It can also be set through -o option through command line.
- DEADZONE_RATIO: The sensitivity level for the code to decide whether to process the input message or not.
- ACCESS_PERIOD: The frequency of the code to check the input message from the game controller 


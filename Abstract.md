# Autonomous_Control_of_Vehicle_Movement_Detection_in_Railway_Gate

This paper aims to provide an automatic railway gate at the level crossing by replacing the gates operated by the gate keeper by detecting train as well as clearing the vehicle which got struck in between the railroad intersection during the closing of the gates, generating corresponding alert signal and controlling the gate. 

The solution is provided by developing a train detection module, vehicle struck detection module, signal light module, alarm module, railway gate controller and a controller module. 

There are two IR sensors in the train detection module and four ultrasonic sensor in vehicle stuck detection module. 

The train detection module generate LOW and HIGH frequency signal through the IR sensors to detect the arrival and departure of train. 

Then the controller unit determines the train and passes the signal to the railway gate controller module to take necessary actions i.e., opening or closing of gates, alarm generator and signal lights. 

The vehicle stuck detection module also generates high frequency signal when the ultrasonic sensors detect the presence of vehicle in between the gates, if the echo is received back by the sensors. 

Then the controller unit determines the vehicle is found in between the gates and takes necessary steps by opening the gate. 

Experimental studies show that the proposed methodology provides a more cost effective, reliable and simpler railway gate controller than existing dominant work.
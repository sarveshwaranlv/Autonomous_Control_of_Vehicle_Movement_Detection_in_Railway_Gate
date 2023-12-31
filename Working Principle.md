# Autonomous Control of Vehicle Movement Detection in Railway Gate

# Working:-

First of all, we need to place the components correct position for the perfect work of this system. Two IR sensors are placed on both sides of level crossings and the distance between the two IR sensors is dependent on the length of the train. Four Servo motors are placed on both sides of the railway track.

When the train comes in front of the IR sensor, then IR sensor-1 detects the arrival of the train and produces LOW (0) output from its Data Pin. But, on the other side, the IR Sensor-2 output is HIGH (1) because this time sensor-2 does not detect the train. When the Arduino gets this signal from two sensors, then the Arduino sends the PWM signal to the servo motors. As a result, servo motors start working and close the gate. At this time, the Arduino sends commands to turn on Red LED and the buzzer starts to generate beep-beep sound, which means that the train is coming.

When the train crosses the level crossing and the train comes in front of the IR sensor-2. Then IR sensor-2 detects the arrival of the train. So, the sensor-2 output goes LOW (0). But, on the other side, the IR Sensor-1 output is HIGH (1) because this time sensor-1 does not detect the train. When the Arduino gets this signal from two sensors, then again the Arduino sends the PWM signal to the servo motors. As a result, the servo motors back to the first position, and automatically open the gate. This time Yellow LED will turn on and the buzzer will stop, it means that the train is gone.

When IR sensor 1 and IR sensor 2 does not detect the train, then the output of the sensor is HIGH (1). In this condition, the gate is open and the Yellow LED will turn on and the buzzer will stop, it means that the train does not come.

During the closing of the railway Gates, using the ultrasonic sensor we can find whether any of the vehicle got struck inside the gate or not. If the vehicle get into the gates after closing, the ultrasonic sensor sends the signal to the Arduino. Then the Arduino sends the PWM signal to the servo motor which is present opposite to the vehicle. As a result, the gate opposite to the vehicle alone gets opened to make the vehicle move away from the gate.

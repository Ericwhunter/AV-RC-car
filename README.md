# AV-RC-car
Autonomous driving car
RC car controlled by Jetson nano

An autonomous car, also known as self-driving cars, are those vehicles that can perfectly drive and navigate with little or no human intervention, guaranteeing the safety and security requirement needed to circulate throughout the existing roads

Parts of the vehicle
Servo motor: (KS4081-06W) it uses a servo motor to control steering wheels of the car. Servo motor is motor that rotates 0 degrees to 180 degrees depending on received signal PWM (pulse width modulation). For the purposes of this project is to aim to replace the receiver with Arduino or other servo driver shield to imitate the PWM signal to rotate the servo motor.  For most preferences servo motor stay at 90 degrees and turn no more than 45 degrees to either direction to turn left or right. 
                
Electronic speed Controller: An Electronic Speed Controller (ESC) is a device employed to regulate and manage the speed of an electric motor. It receives control signals from a receiver and converts them into the suitable power output for the motor. The ESC interprets the control signals, typically in the form of PWM signals, and adjusts the power delivery accordingly.
In the selected RC car, the (Kyosho 82245 60A Brushed ESC KSH KA060-91W) is utilized. This ESC model is designed to directly connect the battery power supply to the ESC itself. The ESC then distributes power to the radio receiver and servo motor. Thus, caution to be taken when connecting ESC to controlling electronics.
 


Receiver: a wireless receiver allows an RC car to be controlled via wireless controller. In this project (Syncro KT-231P+) receiver and controller comes with the RC car, in the scope of the project the receiver and controller to considered optional use to control the car when processor is not controlling it. Thus additional multiplexor PCB need to be used for switching between radio receiver and jetson nano. (proposed use of Pololu 4-Channel RC Servo Multiplexer)
 
2.2 Electronics  
To control the RC car, other electronics as well as processor is required to run the motors, communicate with sensors, process images, path plan and more. The following sub chapter explains what components were used. 
Processor/computer.  Project is decided to be powered by NVIDIA Jetson nano as it offers compact design, low power usage for relatively good processing. NVIDIA Jetson Nano is a compact, powerful computer designed for AI tasks and accelerated computing. t's a single-board computer with a quad-core CPU and NVIDIA GPU, ideal for applications like robotics and smart cameras.
   

 
Wireless. Jetson nano development kit does not have built in Wi-Fi and Bluetooth module. Intel 8265 M.2 card it allow WI-FI and Bluetooth connection. 
Servo and ESC driver. To control the servo and ESC (Electronic Speed Controller) using PWM signals, the Jetson Nano needs to provide these signals. One way to achieve this is by connecting an Arduino Nano or Uno to the Jetson Nano to generate and send the PWM signals. In this project, it is recommended to use the PCA9685 servo driver. This driver allows the Jetson Nano to send signals to the driver, which then converts them into PWM signals using its general-purpose input/output (GPIO) headers. This setup enables the Jetson Nano to control the servos and ESC accurately and efficiently.

Controller option 
•	Multiplexer. Its small circuit that allow a easy switching between multiple independent signal sources. For example (Pololu 4-Channel RC Servo Multiplexer) will allow switching between 2 signals from Jetson nano or RC controller to control RC car. Thus in case of connection failure between jetson and main computer RC controller can take control of the RC car.  
•	Gamepad controller can be used to control RC car through jetson as it ability to provide precise input data to jetson via Bluetooth but not sure about its proximity distance ( its stated max 50m with no interference)
 

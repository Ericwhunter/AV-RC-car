# AV-RC-car
Autonomous driving car
RC car controlled by Jetson nano
                                                           ![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/087d40a8-cf39-410d-88f2-c99fe3bc2b11)

  ![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/9fd052c9-b077-4baa-a9e4-9f60b334191b)

An autonomous car, also known as self-driving cars, are those vehicles that can perfectly drive and navigate with little or no human intervention, guaranteeing the safety and security requirement needed to circulate throughout the existing roads

Parts of the vehicle
Servo motor: (KS4081-06W) it uses a servo motor to control steering wheels of the car. Servo motor is motor that rotates 0 degrees to 180 degrees depending on received signal PWM (pulse width modulation). For the purposes of this project is to aim to replace the receiver with Arduino or other servo driver shield to imitate the PWM signal to rotate the servo motor.  For most preferences servo motor stay at 90 degrees and turn no more than 45 degrees to either direction to turn left or right. 

  ![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/9ca16348-eb84-4ead-9e20-da936d4f949c)      ![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/bb2b91ce-6cf1-42d3-9eb7-3aa0cce44782)

Electronic speed Controller: An Electronic Speed Controller (ESC) is a device employed to regulate and manage the speed of an electric motor. It receives control signals from a receiver and converts them into the suitable power output for the motor. The ESC interprets the control signals, typically in the form of PWM signals, and adjusts the power delivery accordingly.
                                     ![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/3e91143d-b1d2-49d6-a2b1-1f699b039e84)

In the selected RC car, the (Kyosho 82245 60A Brushed ESC KSH KA060-91W) is utilized. This ESC model is designed to directly connect the battery power supply to the ESC itself. The ESC then distributes power to the radio receiver and servo motor. Thus, caution to be taken when connecting ESC to controlling electronics.
 
   ![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/b2b65733-0f3a-44d4-9ce3-6ea7041efb32)
 
Receiver: a wireless receiver allows an RC car to be controlled via wireless controller. In this project (Syncro KT-231P+) receiver and controller comes with the RC car, in the scope of the project the receiver and controller to considered optional use to control the car when processor is not controlling it. Thus additional multiplexor PCB need to be used for switching between radio receiver and jetson nano. (proposed use of Pololu 4-Channel RC Servo Multiplexer)
 
2.2 Electronics  
To control the RC car, other electronics as well as processor is required to run the motors, communicate with sensors, process images, path plan and more. The following sub chapter explains what components were used. 
Processor/computer.  Project is decided to be powered by NVIDIA Jetson nano as it offers compact design, low power usage for relatively good processing. NVIDIA Jetson Nano is a compact, powerful computer designed for AI tasks and accelerated computing. t's a single-board computer with a quad-core CPU and NVIDIA GPU, ideal for applications like robotics and smart cameras.
  
![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/06aa878e-b809-40e8-bc60-e84fbd9780bc) ![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/b21ef8df-19f0-48de-b15e-d99e790a47d2)

 
Wireless. Jetson nano development kit does not have built in Wi-Fi and Bluetooth module. Intel 8265 M.2 card it allow WI-FI and Bluetooth connection. 
Servo and ESC driver. To control the servo and ESC (Electronic Speed Controller) using PWM signals, the Jetson Nano needs to provide these signals. One way to achieve this is by connecting an Arduino Nano or Uno to the Jetson Nano to generate and send the PWM signals. In this project, it is recommended to use the PCA9685 servo driver. This driver allows the Jetson Nano to send signals to the driver, which then converts them into PWM signals using its general-purpose input/output (GPIO) headers. This setup enables the Jetson Nano to control the servos and ESC accurately and efficiently.

Controller option 
•	Multiplexer. Its small circuit allows easy switching between multiple independent signal sources. For example (Pololu 4-Channel RC Servo Multiplexer) will allow switching between 2 signals from Jetson nano or RC controller to control RC car. Thus in case of connection failure between the jetson and the main computer RC controller can take control of the RC car.  
![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/62ad1081-5ecd-4e71-97c8-200d34c9bddd)

•	Gamepad controller can be used to control RC car through jetson as it ability to provide precise input data to jetson via Bluetooth but not sure about its proximity distance ( its stated max 50m with no interference)

 ![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/2377fb2a-3b27-4a72-9ca2-9ee31944fe9b)


 ![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/e848e3bc-b7c0-4ad3-99fc-c3376d06566b)

Connection PCA9685 to Jetson Nano.
When connecting servo driver with Jetson it needs to be connected to I2C pins (SCL and SDA) which Jetson nano has at GPIO pin 3 (SDA) and pin 5 (SCL) as BUS 1 and pin 27 (SDA) and pin 28 (SCL) as BUS 0. (Note: SDA/SCL pin works in pair as BUS 1 or Bus 0 and in Jetson nano BUS 1 is default). 
![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/57c0ce78-c426-435e-aab2-96c1c0ea8e65)

 
![image](https://github.com/EricMEP/AV-RC-car/assets/48544912/15c1e466-3c6b-444b-8b9f-0b9a0e200569)

Multiplexer circuits are used to switch between the 2 signal sources, allowing RC car to be controlled by a Radio controller as well as the Jetson nano.

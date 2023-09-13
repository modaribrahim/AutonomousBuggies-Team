
# WRO2023 FUTRE ENGINEERS - Autonomous Robot Vehicle

This is a breif description about the autonomous robot vehicle used by team 'Autonomous Buggies' in the aim of participating in WRO2023 competetion - Future Engineers category. 
 

The mechanical, electrical, and electronic parts of the vehicle can be found in the sections listed above.

The codes used to program the vehicle are written in Python and Arduino C.
## Sections

 - [Models](#)
 - [Schemes](#)
 - [Source](#)

- [Team Photos](#)
- [Vehicle Photos](#)



## Vehicle Main Body
The vehicle main body is built using `LEGO`.
The main Micrprocessor in the vehicle is `Raspberry Pi 4 Model b` provided with `Raspberry pi Camera V2.1`.
Main Macrocontroller is Atmega mounted on `Arudino Mega 2060` board.
To ensure the accurate and efficient control and direction of the vehicle’s movement, we employed two crucial components:
- **Servo Motor Model**
- **J Sumo DC Motor**
- **BTS Motor Driver**
The servo motor model was selected for controlling the vehicle’s steering, while the J Sumo DC motor was utilized to provide the necessary power to drive the vehicle’s motion. 

**The characteristics of the DC motor:**
1. The diameter of the motor is 37mm. Length is 75mm.
2. 6mm diameter shaft section, shaft length 17 mm.
3. No load current is 240ma, and stall current is 5.9 Ampere.
4. All Gearhead gears are metal.
5. Motor’s stall torque is 7.5 kg-cm.
## Why JSUMO Motor
If we want to reach a certain velocity, we need first to calculate the equivalent moment of inertia of the vehicle then depending on the time needed to reach the steady state velocity we can find the torque needed to translate the vehicle with the desired velocity. Due to the many components of the vehicle we estimated the equivalent moment of inertia, taking the mass of the vehicle **1.495kg** , wheels radius **28mm**, desired velocity **50cm/s**, steady state reach time **10 millisecond**, we found that the Jsumo DC motor we used that has a stall torque about **7.5kg-cm** is enough to handle the vehicle and make it move by **50cm/s** velocity in a good steady state time.

#### The Motion Mechanism 
We used Ackermann steering and for that employed a servo motor, while the DC motor (J Sumo 300 rpm) serves as the driving motor. The kinetic energy generated by the DC motor is transferred to the back wheels through a differential gearbox. The wheels receive this energy via a drive shaft made of LEGO components, which transmits torque to the differential gearbox through a suitable coupler designed and printed by 3d printer using this [model]().

- Raspberry pi 4 Camera.
- 10 UltraSonic Sensors.
The camera was used to discover the playfield of the robot and to identify the color of the pillars existed in front of the vehicle.
The 10 Sensor were mounted as the following:
- `L1 Sensor` Left Front (Closer to the frontend of the robot).
- `L2 Sensor` Left Back (Closer to the backend of the robot).
- `R1 Sensor` Right Front (Closer to the Frontend of the robot).
- `R2 Sensor` Right Back (Closer to the backend of the robot).
- `F Sensor` Frontal Sensor (In the middle of the frontend of the robot).
- `B Sensor` Rear Sensor (In the middle of the backend of the robot).
- `BL Sensor` Back Left Sensor - mounted on the edge of the vehicle and tilted by 45 counter-clockwise degrees about the x-axis of the robot.  
- `BR Sensor` Back Right Sensor - mounted on the edge of the vehicle and tilted by 45 clockwise degrees about the x-axis of the robot.
- `FL Sensor` Front Left Sensor - mounted on the edge of the vehicle and tilted by -45 counter-clockwise degrees about the x-axis of the robot.  
- `FR Sensor` Front Right Sensor - mounted on the edge of the vehicle and tilted by -45 clockwise degrees about the x-axis of the robot.
Each sensor is fixed into a squared LEGO piece. These Sensors allow the vehicle to well follow the walls, using the equation that will be explained later.


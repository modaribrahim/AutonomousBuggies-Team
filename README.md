
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


## Mobility Management
### Vehicle Main Body
The vehicle main body is built using `LEGO`.
The main Micrprocessor in the vehicle is `Raspberry Pi 4 Model b` provided with `Raspberry pi Camera V2.1`.
Main Macrocontroller is Atmega mounted on `Arudino Mega 2060` board.
To ensure the accurate and efficient control and direction of the vehicle’s movement, we employed two crucial components:
- **Servo Motor Model**
- **J Sumo DC Motor**
- **BTS Motor Driver**

The servo motor model was selected for controlling the vehicle’s steering, while the J Sumo DC motor was utilized to provide the necessary power to drive the vehicle’s motion. 

### Why JSUMO Motor
If we want to reach a certain velocity, we need first to calculate the equivalent moment of inertia of the vehicle then depending on the time needed to reach the steady state velocity we can find the torque needed to translate the vehicle with the desired velocity. Due to the many components of the vehicle we estimated the equivalent moment of inertia, taking the mass of the vehicle **1.495kg** , wheels radius **28mm**, desired velocity **50cm/s**, steady state reach time **10 millisecond**, we found that the Jsumo DC motor we used that has a stall torque about **7.5kg-cm** is enough to handle the vehicle and make it move by **50cm/s** velocity in a good steady state time.

### The Motion Mechanism 
We used Ackermann steering and to achieve that a servo motor was installed in way that can move the Ackermann freely, while the DC motor (J Sumo 1000 rpm) serves as the driving motor. The kinetic energy generated by the DC motor is transferred to the back wheels through a differential gearbox. The wheels receive this energy via a drive shaft made of LEGO components, which transmits torque to the differential gearbox through a suitable coupler designed and printed by 3D printer using this [model](https://github.com/jaafarmayya/AutonomousBuggies-Team/blob/main/models/Coupler.jpg).

### Steering Mechanism

Our design incorporates front Direct-Acting Steering, a mechanism that eliminates the need for a steering gear by connecting the steering wheel directly to the steering linkage. Our front direct-acting steering method offers several advantages over conventional steering systems:

**A. Enhanced Responsiveness:**
 By eliminating the steering gear, the direct connection between the steering wheel and the steering linkage results in immediate and precise response to driver input, providing enhanced control and maneuverability.

 **B. Reduced Complexity**
 By eliminating the steering gear mechanism, our steering method simplifies the overall design, reducing weight and complexity, and potentially lowering manufacturing and maintenance costs.

**C. Lower Maintenance Requirements**
 With fewer components involved, the direct-acting steering method can reduce the need for maintenance and potential points of failure, resulting in improved reliability and durability.

The working mechanism of our front direct-acting steering method can be summarized as follows:

   1. Direct Connection:
 The steering wheel is directly linked to the steering linkage, eliminating the need for a steering gear mechanism.

   2. Steering Input Translation:
 When the servo motor turns the steering axle, the input is directly transmitted to the steering linkage, causing the front wheels to turn accordingly.

   3. Cornering:
 Cornering: During cornering, the steering mechanism maintain a smooth trajectory based on the servo motor input.

![Direct Acting Steering](/Documentation/Images/Steering+Mechanism/Picture1.jpg)

![Direct Acting Steering](/Documentation/Images/Steering+Mechanism/Picture2.jpg)


When designing a steering mechanism, some parameters should be considered to measure the characteristics and specifications of the steering system:

**1. Steering Ratio**

It is a key parameter in a steering system that describes the relationship between the rotation of the steering wheel (which is servo axle in our case) and the resulting rotation of the wheels. Moreover, it quantifies the mechanical advantage or amplification provided by the steering mechanism.
Mathematically speaking, it is defined as the ratio of the angle turned by the steering wheel (servo axle) θ<sub>servo</sub> 
to the angle turned by the wheels θ<sub>wheels</sub> 
It can be expressed as:

![Steering Ratio ](http://www.sciweavers.org/tex2img.php?eq=Steering%20Ratio%20%3D%20%20%20%20%5Cfrac%7B%5Ctheta%20_%7Bservo%7D%7D%7B%7B%5Ctheta%20_%7Bwheels%7D%7D%20&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

The steering ratio determines how much the wheels will turn in response to a given rotation of the servo. A higher steering ratio means that a smaller rotation of the steering wheel will result in a larger rotation of the wheels, providing a greater turning effect. Conversely, a lower steering ratio means that a larger rotation of the steering wheel is required to achieve the same wheel rotation. So, it can be described as a measure of the sensitivity and responsiveness of the steering system.

**2. Steering Wheel Torque**
 
Steering wheel torque T<sub>wheels</sub>
is the influence of servo motor force or moment applied on the steering. In other words, it refers to the force or moment applied to the wheels as a result of the torque output from the servo motor.
T<sub>wheels</sub> can be calculated by multiplying the applied force by servo motor F<sub>servo</sub> by the effective lever arm or steering arm length L<sub>eff</sub> which is the distance between the point where the force is applied and the axis of rotation of the steering wheel: 


![Steering Wheel Torque](http://www.sciweavers.org/tex2img.php?eq=%20T_%7Bwheels%7D%20%3D%20F_%20%7Bservo%7D%20%20%5Ctimes%20L_%20%7Beff%7D&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

When interpreting the steering wheel torque, it should be noted that a higher steering wheel torque indicates that more force is needed from the servo motor to turn the steering wheel, providing a greater resistance to steering. Conversely, a lower steering wheel torque implies that less force is required, resulting in lighter and easier steering.

**3. Steering Wheel angle**

The steering wheel angle refers to the angle of rotation of the servo motor's output shaft, which is directly connected to the steering mechanism of the robot. Furthermore, it represents the angular displacement of the servo motor's output shaft from its neutral or reference position. 
This angle determines the orientation of the robot's steering mechanism and thus influences the robot's movement and direction.

![Steering Ratio Formul](http://www.sciweavers.org/tex2img.php?eq=%20%5Ctheta_%7Bwheel%7D%20%3D%20%5Ctheta_%7Bwheel%7D%20%20%5Ctimes%20SteeringRatio&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)


### Differential Gear
Differential gear is a crucial component in our robot that allows the rear-wheels to rotate at different speeds while maintaining power distribution. The primary function of the differential gear is to enable the wheels on the same axle to rotate at different speeds when the robot is turning or when there is a difference in traction between the two wheels. It distributes torque from the engine to the wheels while allowing them to rotate at varying speeds. Our differential gear consists of several components:
- Ring Gear: A large gear attached to the axle shaft that receives power from the engine or the driveshaft.
- Pinion Gear: A smaller gear connected to the drive shaft, which meshes with the ring gear.
- Side Gears: Two gears that connect the differential to the axle shafts.
- Spider Gears: These gears are positioned between the side gears and allow the wheels to rotate at different speeds.

When the vehicle is moving in a straight line, the differential distributes torque equally to both wheels. However, when the vehicle turns, the inside wheel needs to rotate at a slower speed than the outside wheel to prevent tire scrubbing. The differential allows this speed difference by allowing the side gears to rotate at different speeds while maintaining power distribution.
It is important to determine gear ratio before designing a differential gear, which involves understanding the specifications and characteristics of the motors, as well as the mechanical setup of the differential. To calculate the differential gear ratio, the ratio between the ring gear and the side gears should be determined. This can be done by counting the number of teeth on each gear:
   - The number of teeth on the ring gear (crown wheel). Let's call it $R$
   - The number of teeth on each side gear (sun gear). Let's call them $S1$ and $S2$
The differential gear ratio can be calculated as the ratio between the teeth on the ring gear and the teeth on one side gear. Since there are two side gears in the differential, the gear ratio is multiplied by 2:  

![Steering Ratio Formula](http://www.sciweavers.org/tex2img.php?eq=Gear%20Ratio%20%3D%20%5Cfrac%7B%20%282%20%5Ctimes%20R%29%7D%7BS_%7B1%7D%7D%20%20%3D%20%5Cfrac%7B%20%282%20%5Ctimes%20R%29%7D%7BS_%7B2%7D%7D&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

The gear ratio represents the rotational speed and torque distribution between the two side gears of the differential. 
Once the gear ratio calculation is done, motor speed can be related to the wheel speed. Since the side gears are connected to the wheels, their speed is directly proportional to the wheel speed. The no-load speed of the motor N<sub>MotorNoLoad</sub> from the motor's specifications, which will enable us to calculate the wheel speed using the formula:

![Steering Ratio Formula](http://www.sciweavers.org/tex2img.php?eq=N_%7Bwheel%7D%3D%20%5Cfrac%7BN_%7BMotorNoLoad%7D%7D%7BGearRatio%7D&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

The wheel speed represents the rotational speed of the LEGO differential's side gears, which directly affects the vehicle's speed. However, the calculated values may need to be calibrated when experimenting them (Real world values may differ from the calculated ones due to multiple constraints that can’t be considered when doing the calculations).

![Flow Chart](/Documentation/Images/Steering+Mechanism/Correct1.png)

![Illustrated Differential Gear Box](/Documentation/Images/Steering+Mechanism/Correct2.png)


## Power & Sense Management
### Electronic Components
- **Arduino Mega 2560:** The Arduino Mega 2560 is an open-source microcontroller board based on the ATmega2560 microcontroller. It is one of the most popular boards in the Arduino family due to its versatility and extensive I/O capabilities. The Mega 2560 is designed to offer a large number of digital and analog inputs and outputs, making it suitable for complex projects that require multiple sensors, actuators, and communication interfaces. The key features and specifications of the Arduino Mega 2560:

   1. Microcontroller: The Mega 2560 is powered by the ATmega2560 microcontroller, which has 256KB of flash memory for storing code, 8KB of SRAM for data storage, and 4KB of EEPROM for non-volatile storage.

   2. Digital I/O Pins: The board offers 54 digital I/O pins, of which 15 can be used as PWM outputs. These pins can be used for connecting various components such as sensors, switches, LEDs, and other digital devices.

   3. Analog Inputs: The Mega 2560 has 16 analog inputs, allowing you to read analog signals from sensors and other devices. These inputs have a 10-bit resolution, providing 1024 different voltage levels.

   4. Communication Interfaces: The board supports multiple communication interfaces, including UART (Universal Asynchronous Receiver/Transmitter), SPI (Serial Peripheral Interface), and I2C (Inter-Integrated Circuit). These interfaces enable communication with other devices such as sensors, displays, and modules.

   5. USB Interface: The Mega 2560 features a USB interface that allows it to be connected to a computer for programming and serial communication. It can appear as a virtual serial port for easy integration with software development environments.

   6. Operating Voltage: The board operates at 5V, making it compatible with a wide range of sensors, modules, and other components.

   7. Memory Expansion: The Mega 2560 supports external memory expansion through an optional SD card slot, allowing you to store larger amounts of data or log sensor readings.

   8. Compatibility: The Mega 2560 is fully compatible with the Arduino software and programming language, making it easy to get started with coding and prototyping.

   9. Shield Compatibility: The board is designed to be compatible with Arduino shields, which are additional modules that can be stacked on top of the board to extend its functionality. This allows you to easily add features such as Wi-Fi, Bluetooth, motor control, and more.  [[2]]() 
- **Raspberry pi 4 Model B:** The Raspberry Pi 4 Model B is a popular single-board computer (SBC) developed by the Raspberry Pi Foundation. It is the fourth generation of the Raspberry Pi series and offers significant improvements over its predecessors. The Raspberry Pi 4 Model B is designed to be a versatile and affordable platform for various applications, including education, prototyping, home automation, media centers, and more. The key features and specifications of the Raspberry Pi 4 Model B:
   1. Processor: The board is powered by a Broadcom BCM2711 quad-core Cortex-A72 (ARMv8) 64-bit system-on-a-chip (SoC) running at 1.5 GHz. This processor provides a significant performance boost compared to previous Raspberry Pi models, enabling smoother multitasking and faster execution of applications.

   2. Memory: The Raspberry Pi 4 Model B is available in different memory configurations, including 2GB, 4GB, and 8GB LPDDR4 RAM options. The increased memory capacity allows for better performance, especially when running resource-intensive applications or multitasking.

   1. GPU: It features a VideoCore VI GPU, which supports OpenGL ES 3.x and 4Kp60 hardware decode of HEVC video. The GPU enables multimedia applications, gaming, and hardware-accelerated video playback.

   1. Connectivity: The board offers improved connectivity options, including:
     * Gigabit Ethernet: Provides fast wired network connectivity.

     * Dual-band Wi-Fi: Supports 2.4 GHz and 5 GHz wireless networks, offering improved wireless performance.
     * Bluetooth 5.0: Enables wireless connectivity with Bluetooth-enabled devices.
     * USB Ports: The Raspberry Pi 4 Model B has two USB 2.0 ports and two USB 3.0 ports, allowing for easy connection of peripherals such as keyboards, mice, external drives, and more.
   5. Video and Display: The Raspberry Pi 4 Model B supports dual-monitor output with resolutions up to 4K. It features two micro HDMI ports, allowing you to connect two displays simultaneously. The board also has a MIPI DSI display port and a MIPI CSI camera port for connecting touchscreens and cameras.

   1. Storage: It includes a microSD card slot for the operating system and data storage. Additionally, it has two USB 3.0 ports and two USB 2.0 ports, which can be used to connect external storage devices such as hard drives or USB flash drives.

   1. GPIO Pins: The board maintains compatibility with previous Raspberry Pi models and provides 40 GPIO (General Purpose Input/Output) pins, which allow for the connection of various sensors, actuators, and other electronic components.

   1. Operating System: The Raspberry Pi 4 Model B is compatible with a wide range of operating systems, including Linux distributions such as Raspbian (now known as Raspberry Pi OS), Ubuntu, and others. This flexibility enables developers to choose the OS that best suits their needs and leverage the extensive software ecosystem available for the Raspberry Pi. [[3]]()
- **Raspberry pi camera:** The Raspberry pi camera was used to discover the playfield of the robot and to detect the color of the pillars existed in front of the vehicle. [[4]]()
- **BTS7960 Motor Driver:** The BTS7960 Motor Driver is a popular dual H-bridge motor driver module that allows you to control the speed and direction of DC motors. It is commonly used in robotics, automation, and other projects that require precise motor control.

   The key features and specifications of the BTS7960 Motor Driver:

   1. H-Bridge Configuration: The BTS7960 Motor Driver utilizes an H-bridge configuration, which consists of four power MOSFETs (Metal-Oxide-Semiconductor Field-Effect Transistors) arranged in pairs. This configuration enables bidirectional control of the motor, allowing you to control its rotation in forward and reverse directions.

   2. Motor Compatibility: The motor driver module is designed to work with DC motors and can handle a wide range of motor voltages, typically between 5V and 27V. The maximum continuous current per channel is typically around 43A, making it suitable for driving high-power motors.

   3. Current Sensing: The BTS7960 Motor Driver features built-in current sensing capabilities. It has two current sense pins that allow you to monitor the current flowing through each motor channel. This feature can be useful for various purposes, such as implementing motor current protection or feedback control.

   4. PWM Control: The motor driver supports Pulse Width Modulation (PWM) control for speed regulation. By varying the duty cycle of the PWM signal, you can adjust the motor's speed precisely. The module accepts a PWM input signal from a microcontroller or any other PWM source.

   5. Overcurrent and Overtemperature Protection: The BTS7960 Motor Driver incorporates protection mechanisms to safeguard both the driver and the motor. It includes built-in overcurrent and overtemperature protection circuits that can help prevent damage to the motor driver module and the connected motor.

   6. Input and Output Connections: The motor driver module typically has separate input pins for controlling the motor direction and speed. These control pins can be connected to the digital output pins of a microcontroller or other control devices. The motor connections are made to the driver's output terminals, allowing you to connect the DC motor.

   7. Heat Dissipation: Due to its high current handling capacity, the BTS7960 motor driver may generate heat during operation. To dissipate heat effectively, the module often includes a heat sink or a mounting hole for attaching an external heat sink.

   8. Compatibility: The BTS7960 Motor Driver can be used with various microcontrollers, such as Arduino, Raspberry Pi, or any other microcontroller capable of generating the necessary control signals for the driver module.[[5]]()
- **3 RioRand LM2596 step-down DC-DC Converter:** The RioRand LM2596 is a popular step-down DC-DC converter module based on the LM2596 switching regulator integrated circuit. It is commonly used to convert higher DC voltages to lower, more stable voltages for various electronic applications. The LM2596 module offers efficient and adjustable voltage regulation, making it widely used in projects requiring reliable power supply solutions.

  The key features and specifications of the RioRand LM2596 step-down DC-DC converter:

   1. Conversion Efficiency: The LM2596 module utilizes a switching regulator topology, which provides high conversion efficiency compared to linear regulators. It can achieve conversion efficiencies of up to 90% or more, depending on the input and output voltage differentials.

   2. Input Voltage Range: The LM2596 module can accept a wide range of input voltages, typically between 4.5V and 40V DC. This flexibility allows it to be used with various power sources, such as batteries, power adapters, or other DC power supplies.

   3. Adjustable Output Voltage: One of the key features of the LM2596 module is its ability to provide adjustable output voltage. By adjusting the onboard potentiometer or using an external voltage divider, you can set the desired output voltage within the module's specified range. The output voltage can typically be adjusted from around 1.25V to 37V DC.

   4. Output Current: The LM2596 module can handle a maximum output current of around 2A or more, depending on the specific module variant and configuration. This current rating determines the maximum load current that the module can reliably supply.

   5. Protection Features: The LM2596 module often includes built-in protection features to ensure the safety and longevity of the circuit. These features may include overcurrent protection, thermal shutdown, and input/output overvoltage protection.

   6. Heat Dissipation: Like other power electronics components, the LM2596 module may generate heat during operation. To dissipate heat effectively and maintain optimal performance, the module typically includes a heat sink or a mounting hole for attaching an external heat sink.

  7. Input and Output Connections: The LM2596 module typically has screw terminals or pin headers for easy connection to the input and output voltage sources. The input voltage is connected to the higher voltage source, while the output voltage is connected to the load or the circuit that requires the lower voltage supply.

   8. Applications: The LM2596 module finds applications in a wide range of projects, including electronics prototyping, DIY projects, power supply modules, battery charging systems, LED lighting, and more. Its adjustable output voltage and high efficiency make it a versatile choice for powering various electronic devices and circuits. [ [6]]()
* **Servo Motor:** [[7]]()
  + Torque: 1,6kgcm
  + Stall current 650±80mA
  + Voltage 4,8 V - 7,2 V
  + Speed 0.12 sec / 60 degrees (4.8V)
  + Gears Nylon
  + Length 22 mm
  + Width 11,5 mm
  + Height 22,5 mm Weight 16 g 
- **2 Li-Po RC Batteries 12V:** Li-Po (Lithium Polymer) RC batteries are commonly used in remote control (RC) vehicles, drones, and other hobbyist applications that require a compact and high-capacity power source. While Li-Po batteries are typically available in various cell configurations and voltages, a 12V Li-Po RC battery is not a standard configuration. However, it is possible to create a 12V power supply by combining certain Li-Po battery configurations.

   Li-Po batteries are usually rated based on their nominal voltage per cell, which is typically 3.7V. The most common Li-Po battery configurations are:

      1. 1S: This configuration consists of a single Li-Po cell with a nominal voltage of 3.7V. A 1S Li-Po battery alone cannot provide 12V.

      2. 2S: This configuration consists of two Li-Po cells connected in series, resulting in a nominal voltage of 7.4V (2 cells * 3.7V per cell). Two 2S Li-Po batteries connected in series can provide a combined voltage of 14.8V, which is higher than 12V.

  To achieve a 12V supply using Li-Po batteries, you would need to consider alternative configurations, such as:

   - 3S + 1S: Connect a 3S Li-Po battery (11.1V) in series with a 1S Li-Po battery (3.7V) to achieve a combined voltage of 14.8V. Then use a voltage regulator or step-down converter to regulate the voltage down to 12V.

   - 4S: Use a 4S Li-Po battery (14.8V) and regulate the voltage down to 12V using a voltage regulator or step-down converter.[[8]]()
- **J Sumo DC Motor:** [[1]]()
  - The diameter of the motor is 37mm. Length is 75mm.
  - 6mm diameter shaft section, shaft length 17 mm.
  - 6 M3 screw holes on the front side are available.
  - No load current is 240ma, and stall current is 5.9 Ampere.
  - All Gearhead gears are metal.
  - Motor’s stall torque is 7.5 kg-cm.

- **MPU 6050:** The MPU-6050 is a popular and widely used integrated circuit (IC) that combines a 3-axis gyroscope and a 3-axis accelerometer in a single package. It is commonly used in various applications such as motion sensing, orientation tracking, gesture recognition, and stabilization control systems.

  The key features and specifications of the MPU-6050:

      1. 3-Axis Gyroscope: The MPU-6050 includes a 3-axis gyroscope, which measures angular velocity around three axes (X, Y, and Z). It provides accurate motion sensing capabilities and can be used to detect rotational movements.

      2. 3-Axis Accelerometer: The MPU-6050 also incorporates a 3-axis accelerometer, which measures linear acceleration along the three axes (X, Y, and Z). It enables the detection of changes in velocity and the determination of tilt or inclination.

      3. Digital Motion Processing: The MPU-6050 features an onboard digital motion processor (DMP) that offloads motion processing tasks from the main microcontroller. The DMP performs sensor fusion, combining data from the gyroscope and accelerometer to provide accurate and reliable motion tracking information.

      4. I2C Interface: The MPU-6050 communicates with the microcontroller or other devices using the I2C (Inter-Integrated Circuit) protocol. It has an I2C interface that allows for easy integration and control with various microcontrollers and development boards.

      5. Motion Detection Interrupts: The MPU-6050 includes built-in motion detection capabilities and supports programmable interrupts. This allows the IC to generate interrupts to the microcontroller when predefined motion or orientation thresholds are met, enabling efficient and responsive operation.

      6. Low Power Consumption: The MPU-6050 is designed to operate with low power consumption, making it suitable for battery-powered applications and devices with power constraints.

      7. Temperature Sensor: The IC incorporates an onboard temperature sensor, providing accurate temperature measurements in addition to motion and orientation data.

      8. Applications: The MPU-6050 is widely used in applications such as robotics, drones, gaming controllers, virtual reality (VR) and augmented reality (AR) devices, inertial navigation systems, motion-controlled user interfaces, and many other projects where motion sensing and orientation tracking are required. [[9]]()
- **Cooling Fan:** The cooling fan is used to cool down the temperature of the Raspberry pi microprocessor.
- **10 UltraSonic Sensors:**
  Ultrasonic sensors are electronic devices that use ultrasonic waves to measure distance or detect objects. They work based on the principle of echolocation, similar to how bats navigate in the dark. Ultrasonic sensors emit high-frequency sound waves (typically above the range of human hearing) and then receive the reflected waves to determine the distance or presence of objects.

  The key characteristics and applications of ultrasonic sensors:

      1. Distance Measurement: Ultrasonic sensors are commonly used for non-contact distance measurement. They typically emit ultrasonic pulses and measure the time it takes for the sound waves to bounce back after hitting an object. By knowing the speed of sound in the medium (usually air), the sensor can calculate the distance to the object.

      2. Object Detection: Ultrasonic sensors can detect the presence or absence of objects within their range. When an object is detected, the sensor receives the reflected sound waves, and based on the intensity or time delay of the received signal, it can determine if an object is present or not.

      3. Range and Accuracy: Ultrasonic sensors can have varying range capabilities, typically ranging from a few centimeters to several meters. The accuracy of distance measurement depends on factors such as the sensor's resolution, beam angle, and environmental conditions.

      4. Ultrasonic Transducer: The core component of an ultrasonic sensor is the transducer, which converts electrical energy into ultrasonic sound waves and vice versa. It consists of a piezoelectric crystal that vibrates when an electrical current is applied, generating the ultrasonic waves.

      5. Beam Pattern: Ultrasonic sensors emit sound waves in a specific beam pattern, usually conical or cylindrical. The beam angle determines the width of the detection area. Narrower beam angles provide more focused sensing, while wider angles cover a larger area but with reduced accuracy.

      6. Environmental Considerations: Ultrasonic sensors are affected by environmental factors such as temperature, humidity, and air turbulence. These factors can influence the speed of sound and affect the accuracy of distance measurements.

      7. Applications: Ultrasonic sensors are widely used in various fields, including industrial automation, robotics, automotive, security systems, level monitoring, parking assistance, liquid flow measurement, and presence detection in consumer electronics.[[10]]() 
The 10 Sensor were mounted as the following:
  - `L1` Sensor Left Front (Closer to the frontend of the robot).
  - `L2` Sensor Left Back (Closer to the backend of the robot).
  - `R1` Sensor Right Front (Closer to the Frontend of the robot).
  - `R2` Sensor Right Back (Closer to the backend of the robot).
  - `F` Sensor Frontal Sensor (In the middle of the frontend of the -obot).
  - `B` Sensor Rear Sensor (In the middle of the backend of the robot).
  - `BL` Sensor Back Left Sensor - mounted on the edge of the vehicle and tilted by 45 counterclockwise degrees about the x-axis of the robot.
  - `BR` Sensor Back Right Sensor - mounted on the edge of the vehicle and tilted by 45 clockwise degrees about the x-axis of the robot.
  - `FL` Sensor Front Left Sensor - mounted on the edge of the vehicle and tilted by -45 counterclockwise degrees about the x-axis of the robot.
  - `FR` Sensor Front Right Sensor - mounted on the edge of the vehicle and tilted by -45 clockwise degrees about the x-axis of the robot.





#### Computer Vision
How the robot recognizes the surrounding area?
We developed a Python script that uses computer vision techniques to detect the presence of a
red or green pillar in front of a camera. The script captures video frames from a camera using the
OpenCV library, processes each frame to isolate regions that match the color of a red or green
pillar, and then applies contour detection to identify the location and size of the detected region.
Here is a brief explanation of the code:
* The script imports several libraries, including OpenCV, NumPy, time, and serial.
* It initializes a serial connection to communicate with an external device.
* It initializes the camera capture using OpenCV’s VideoCapture function.
* It sets up the color ranges for the red and green pillars in the HSV color space using NumPy arrays.
* It enters a loop that captures frames from the camera, processes them, and detects the presence of a red or green pillar in each frame.
* The loop extracts a region of interest from the frame, applies a mask to isolate the pixels that match the color range of the red or green pillar, and performs morphological operations to remove noise from the binary mask.
* The script then applies contour detection to find the contours of the identified regions. The contour with the largest area is selected to represent the detected object.
* The script calculates the distance to the detected object based on its area, and It sends signals as commands based on the image processing results to the Arduino using serial communication (The signals depend on the color and distance of the detected object).
#### Computer Vision
How the robot recognizes the surrounding area?
We developed a Python script that uses computer vision techniques to detect the presence of a
red or green pillar in front of a camera. The script captures video frames from a camera using the
OpenCV library, processes each frame to isolate regions that match the color of a red or green
pillar, and then applies contour detection to identify the location and size of the detected region.
Here is a brief explanation of the code:
* The script imports several libraries, including OpenCV, NumPy, time, and serial.
* It initializes a serial connection to communicate with an external device.
* It initializes the camera capture using OpenCV’s VideoCapture function.
* It sets up the color ranges for the red and green pillars in the HSV color space using NumPy arrays.
* It enters a loop that captures frames from the camera, processes them, and detects the presence of a red or green pillar in each frame.
* The loop extracts a region of interest from the frame, applies a mask to isolate the pixels that match the color range of the red or green pillar, and performs morphological operations to remove noise from the binary mask.
* The script then applies contour detection to find the contours of the identified regions. The contour with the largest area is selected to represent the detected object.
* The script calculates the distance to the detected object based on its area, and It sends signals as commands based on the image processing results to the Arduino using serial communication (The signals depend on the color and distance of the detected object).
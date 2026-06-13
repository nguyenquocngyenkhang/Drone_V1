# Drone Project Diary
## Day 12/06/2026: General research & software download

Today, I have learned about some of the common frame of fpv drone by the video "" on Youtube. There are True-X, square, Hypid X, H, Stretched X.
<img width="1105" height="577" alt="image" src="https://github.com/user-attachments/assets/3b73209f-2dcc-4396-8bfe-53dda90c024c" />
## Day 13/06/2026: What is Flight Controller
Today, I decided to use balance circuit JHEMCU GF30F722-ICM F722 Baro OSD Dual BEC Flight Controller 3-8S as a Flight control method and use 4 ESCs alone. Because it would be much cheaper. But i didnt know exactly what is a FC circuit yet. So i will learn it today.
Source: https://youtu.be/xSOaeSd1AlM?si=0e5g1HOr8b5ED1UR

#### 1. What it does?
1. Decode the RC signal
2. Provide the stabilization - add PID controllers(Proportional Integral Derivative) -> drive motors, servos
3. Navigation
4. Ports
5. Landing
6. Arming
7. Configuration
8. Plane should have for better control, but FPV is a must

#### 2. What makes a FC
1. Brain: microcontroller(small computer) - STM32 family - Stability, Navigation, Ports, Landing, Arming, Configuration. -> Where
2. Gyroscope and Accelerometer(Con quay hồi chuyển, cảm biển gia tốc) -> provides angular velocity and acceleration -> How fast roll, pitch, yaw
3. Input and Output:
<img width="1532" height="712" alt="image" src="https://github.com/user-attachments/assets/1f6631ae-580a-4158-a4ae-ec4abb475430" />
4. Voltage Stablilaztion

#### 3. Optional Components
1. Analog OSD(On-Screen Display): Truyền tín hiệu video tới goggles và thêm các thông tin kỹ thuật lên video
2. I2C, Sensors, Bluetooth

#### 4. Types
1. Multirotor oriented
- The generalpurpose flight controllers **JHEMCU**
  **vậy với JHEMCU ko kết nối với 4 esc thì cái thì 4 cái esc đó gắn hoặc nối vào đâu???**
  Đường đi của điện năng: Pin LiPo -> Mạch PDB -> 4 ESC lẻ -> 4 Động cơ.
  Đường đi của Tín hiệu: Tay điều khiển -> Mạch thu RX -> Mạch FC JHEMCU -> Chân S1-S4 -> 4 ESC lẻ -> 4 Động cơ.
- all-in-ones(builtin ESC's), dont need separate ESC's
3. airplane oriented
- Integrated PDB(Power distribution board)
-> We can use multirotor for airplane and vise versa, but will face some challenges

#### 5. Form Factor(the distance between the mounting holes and the orientation of the flight controller)
Will it inside your model?
Three most popular form factor:
1. Big standard flight controllers 30.5x30.5mm
2. The mini flight controllers 20x20mm, xoay 45 độ
3. 25.5x25.5mm

#### 6. Software
Three most popular software:
1. Ardupilot -> full-blown navigation (toàn diện)
2. Betaflight -> racing and freestyle
3. INAV -> somewhere between

#### 7. Changing software
There are some microcontrollers that are not compatible with the ardupilot at all. Those are F411s and F722s. These two MCU families will run only on Betaflight and INAV.
Please remember to note the version of the firmware you used as the firmware may update.

#### 8. Gyros
The era in good and bad Gyro are gone. So dont spend too much on the correct gyro. Suggested gyro: MPU 6000

#### 9. Tips
1. You will need serial ports
- With modern FPV systems and radio receivers you will need at least 3 hardware serial ports


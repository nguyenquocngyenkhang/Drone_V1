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

## Day 14/06/2026: budget estimate and ESC research
### 1. budget estimate
### 2. ESC(Electronic speed controller) research
#### 1. ESC BEC
The gemnini AI suggest that i shoundn't use the ESC BEC **(Battery Elimination Circuit)**, which are those on yellow or black. They are used to decrease the voltage of the battery down to 5V. But the FC like JHEMCU often have Dual BEC either, so it with would be unnecessary and add more dead weight to a drone. -> How does it work? **Still not know yet**
<img width="332" height="562" alt="image" src="https://github.com/user-attachments/assets/bd9c3fb1-78a5-4b06-bcee-e3b6546870e2" />


#### 2. ESC OPTO
Unlike the the BEC, which uses electric to control the rotor, OPTO(Optocoupler) uses light sensor and small LED to control the rotor. By converting the signal of the FC into LED light, the sensor then translates that signal to control the rotor. This method prevent EMF noise problem, caused by using the same **common ground**. Some of the common ESC OPTO is BL_HELI_S/32. However, the price is much higher at about 228k VNĐ for each, which is 912k for four. Then the sum of sole FC and 4 ESC would cost around 1.8 Million VNĐ, same as buying the stack -> **May choose stack** 
<img width="750" height="563" alt="image" src="https://github.com/user-attachments/assets/de1467d7-aa78-414a-90a2-448a0df37b80" />

## Day 15/06/2026: Motor and Battery
### 1. Motor
///
KV -> express the round per minute for each volt of the motor. For example, for 2300KV motor, at 10V -> we can have 2300*10 = 23000 RPM. The speed of the motor is inversely proportional to the torque(The power to spin)
///
Today, I am going to research about motor.
The Seller told me that the motor and the frame(kit) are related to each other, so I need to choose one of them first. I want to build a long-endurance drone, therefore the drone needs motor that has low KV but high in torque. So they use less electricity but fly more effective. The Gemini suggested that I should use the propeller at 7inch-17.78cm, that would go with 1300KV motor.

**Still not choose a specific motor yet**
### 2. Battery
For long-endurance drone, I can try to make myself a Li-ion battery for much more efficien in mAH and weight than Lipo battery. Let see how its done.

## Day 17/06/2026: DIY Li-ion battery research
Source: https://nshopvn.com/blog/hieu-ro-ve-pin-18650/
Source: https://youtu.be/u8EkRS_c3MM?si=HUxGZmVvXutexhbE
### 1. Intro
- li-ion NCR18650BW Battery
**What is 18650 Battery?**
**Li-ion** -> Lithium-ion

**Dimension:** 18mm x 65 mm, cylinder

**Voltage:** full(3.7-4.2V), low(3V-lower)
-> With different compination -> different use -> For example, when we connect two 3.7V 18650 li-ion, we get 7.4V in total
<img width="1009" height="490" alt="image" src="https://github.com/user-attachments/assets/7435e496-cec0-40bd-bec5-33bec898a661" />

**Capacity(mAh):** ex. 2000mAh -> the battery will run out when Discharge 2A in 1H. **How to increase?** -> connect the bat parallel
<img width="1038" height="507" alt="image" src="https://github.com/user-attachments/assets/a00d2e11-c700-4965-9c1b-12e35ad6f0ad" />

**Discharge current:** We need to use the right Dc for a specific task to avoid the decrease in voltage as U = I*R. The discharge unit is C(1C, 2C, 5C, 10C, 20C …). Ex. 2000mAh battery with 1C can discharge 2000mA at Max or 2000mAh battery with 2C can discharge 4000mA at Max. Li-ion battery usually can only discharge at 2C. To increase the DC, we need to connect parallely. 

**Internal Resistance:** the lower the IR, the better the battery. BC they minimize the voltage leak when charging. Ex. bat with 500m Ohm IR, 2A discharge rate will decrease the voltage by 1V (2*500*10^(-3) = 1). **How to calculate?:**
<img width="1047" height="705" alt="image" src="https://github.com/user-attachments/assets/6610233e-313a-40f1-9e47-f8a7e0133492" />

**Charging:** 
The maximum charging current is the rate at which the battery is charged. The unit is also counted as C. For longevity, the CC doesnt exceed 1C. Ex. 3000mA, charging current = 1*3000mAh = 3000 mA, charging current does not exceed 3A, but to ensure longevity, it should only charge about 70% theoretically. -> if we overcharge -> magic smoke and magic fire will appear:)))

**Discharging Charging Circuit:**
to prevent **overload and overvoltage** when charging or discharging, the charging circuit is used for balancing the batteries in a block to be charged evenly without the situation that one battery is full but the other is not full.

**Charging Adapter:** too low voltage -> break the adapter, too high voltage -> magic explode. We choose adapter base on the number of battery cells, 4.2*(No. of batteries in series). Ex. 6 batteries in series use 25.2V.

**Protected and unprotected batteries:** 
A protected battery means that the battery has a built-in protection circuit

This protection circuit has the following uses

- Automatic shut-off when the battery voltage discharges more than the rated voltage
- Automatically shut off the power when the discharge current exceeds the rated current (usually good currents such as AW have this function)
- Automatic shut-off when fully charged
Usually the battery will have the word protection or protected. If it is not written that there is no protection circuit

## Day 30/6/2026 Motors, Propeller
Source: https://www.dronetechplanet.com/how-a-quadcopter-works-along-with-propellers-and-motors/#How_Quadcopter_Motors_Work
Well, i realized that to choose which battery configuration should i build, i need to know which motor i will use. Because, in three relative components motors, propeller, and battery, motors are the most expensive. So which criteria will i use to choose motors
**Criteria:**
1. Purpose(Long endurance)
2. Budget

In the first criteria, the motors that used for long flight are those with low KV. from about 960KV -> 1100KV









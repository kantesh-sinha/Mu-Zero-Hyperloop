Electrical Subsystem

1. Award Category and Design Competition Award
Electrical Subsystem Award


2. Description of System/Component (ITD, FDD)
The pod relies on the amalgamation of various types of sensors necessary for state estimation as well as active control and safe operation during a run. Sensors capture and translate the physical attributes in and around the pod into observable electrical impulses which are then relayed to the microprocessor through the sensor ECU. Around thirty different sensors collect information about the position, angular/ linear orientation of the pod, the temperature of various subsystems and pneumatic pressure of the brakes. The three major categories of sensors used in the pod are position/navigation aid, temperature and pressure sensors. The navigation aid sensors play a major role in state estimation which is used to develop a precise and reliable system for position tracking. The combined data received from sensors allow the pod to follow a predefined trajectory profile that specifies a position-dependent speed. To achieve this, the estimation of the podâs state, consisting of its position, velocity, and acceleration, as well as a high-level control is needed. The aim for the sensor infrastructure is to facilitate autonomous functioning allowing active control of the pod at all points during the run which is done using both analog output sensors such as pressure sensor, LIM temperature sensor, NTC10K screw-in temperature sensors and digital output sensors namely fiducial sensor and mass flow rate sensor. The sensors are controlled through two different self-developed SensorECUs placed on the front and backside of the pod and exchanged data through the CAN bus connections.

![image](https://github.com/user-attachments/assets/bd425249-0b31-40d6-a2a2-b785c41800a4)

![image](https://github.com/user-attachments/assets/3b875a27-c35e-4282-a910-4bae8cf24c98)

3. Size and Appearance/ Components

![image](https://github.com/user-attachments/assets/eeee2264-2a37-4cc4-af53-742c822e1d25)

POWER CONSUMPTION OF SENSORS

![image](https://github.com/user-attachments/assets/d66c5aa0-1e52-45af-9798-c76ac6e3f260)

ANALOG I/P USAGE ECUs

ECU Brake front
Function: Control of brake front
DIN1: SDC(Shut Down Circuit)Reading
DIN2:
AIN1: 4..20mA I/P-Pressure sensor front 1 : Tank pressure
AIN2: 4..20mA I/P-Pressure sensor front 2 : Acting chamber pressure
AIN3: 4..20mA I/P-Pressure sensor front 3 : Retracting chamber pressure
AIN4:
Edit

ECU Brake rear
Function: Control of brake rear
DIN1: SDC(Shut Down Circuit)Reading
DIN2:
AIN1: 4..20mA I/P-Pressure sensor rear 1: Tank pressure
AIN2: 4..20mA I/P-Pressure sensor rear 2: Acting chamber pressure
AIN3: 4..20mA I/P-Pressure sensor rear 3: Retracting chamber pressure
AIN4:
Edit

ECU Sensor front
Function: Sensors and state machine
IMUs: 3 IMUs for state estimation
RS232:
Encoder: Wheel encoder left front
DIN1: Mass Flow Rate Sensor YF-S201C - between coolant reservoir and HX LIM
DIN2:
DIN3:
DIN4:
AIN1: 1500Ohms pull up-LIM temperature sensor stator 1
AIN2: 1500Ohms pull up-LIM temperature sensor stator 2
AIN3: 1500Ohms pull up-LIM temperature sensor stator 3
AIN4: 1500Ohms pull up-LIM temperature sensor stator 4
AIN5: Screw-in Temperature Sensors NTC10K at 25 °C - between coolant reservoir and HX LIM
AIN6: battery Temperature Sensor NTC10K
AIN7: Cooling temperature sensor NTC 10K 3950 - cooling tank reservoir center
AIN8: Screw-in Temperature Sensors NTC10K at 25 °C between HX LIM and HX PEU

ECU Sensor rear
Function: Sensors and state estimation
IMUs: 3 IMUs for state estimation
RS232:
Encoder: Wheel Encoder left rear
DIN1: Stripe Sensor left
DIN2: Stripe Sensor Right
DIN3:
DIN4:
AIN1: 1500Ohms pull up-LIM temperature sensor -coil1
AIN2: 1500Ohms pull up-LIM temperature sensor -coil2
AIN3: 1500Ohms pull up-LIM temperature sensor -coil3
AIN4:
AIN5:
AIN6:
AIN7:
AIN8:
Edit

Pin Mapping of Sensor ECU
![image](https://github.com/user-attachments/assets/966dab0c-bb52-4e78-8874-a9473bbe95d8)
VBAT - Voltage Battery
RTS - Reflowable Thermal Switch
TX - Transmit
Edit
Overview
The analog I/P are structured as follows:

Input attenuation. Configure input for
analog voltage 0..5V
analog current 4..20mA
Edit
Input Configuration
Edit
Input Attenuation
Input attenuation reduces the power of a signal without appreciably distorting its waveform. Each of the analog I/P can be configured by placing resistors to read either of the following

voltage e.g. 0…3.3V or 0…5V)
a current (e.g. 4…20mA)
resistive sensor (e.g. NTC)

![image](https://github.com/user-attachments/assets/f4d1db96-6ef4-4da6-bf7b-c373aaca9511)

Input Lowpass Filter
Analog input signals shall be filtered by a lowpass filter of at least 2nd order.
This is to remove high-frequency noise in the signal and prevent aliasing.

![image](https://github.com/user-attachments/assets/2c2cfa54-5f45-4983-8d3f-6868531ad15d)

Low Pass filter configurations
On the sensor ECUs and the brake ECUs is a 2nd order active Sallen-Key-Lowpass filter
The following table shows different resistor combinations for different cut-off frequencies
This tool was used: http://sim.okawa-denshi.jp/en/OPseikiLowkeisan.htm
![image](https://github.com/user-attachments/assets/f69bbde4-b096-4006-ad37-be7e7bf51cfd)




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

![image](https://github.com/user-attachments/assets/5985e2d9-2be7-469a-b88b-b271bb2467d4)

Interfaces to other subsystems

Edit
3.1 Interface to Subsystem 1: Cooling
Sensors are required for various operations and measurements in the cooling subsystem of the pod.NTC10K 3950 is placed at the cooling tank in the reservoir centre and is used to collect temperature data from the coolant in the reservoir to optimize coolant volume. Mass Flow Rate Sensor - YF-S201C is placed between coolant reservoir and HX LIM and is used to collect flow rate data from coolant flow into the reservoir to help determine coolant pressure Screw-in Temperature Sensors- NTC10K at 25 Â°C are placed betweenPEUHX and LIM HX to Reservoir) and is used to collect temperature data from the respective locations. The 3temperature sensors allow monitoring and controlling of cooling components

![image](https://github.com/user-attachments/assets/4cdc1d27-e9ca-4024-b07f-8f44a1d6f8e4)

3.2 Interface to Subsystem 2: Suspension
Kubler 2420 hollow shaft are navigation aid sensors used to determine the podâsvelocity and travelled distance. It will be placed on the shaft, there will be two shafts and the wheel encoder will be attached between both.
![image](https://github.com/user-attachments/assets/eb35380f-1886-4db1-887e-f45683ac6b62)


3.3 Interface to Subsystem 3: Brakes
:6 Pneumatic Pressure Sensors SICK-PBT-RB016SG1SSNAMA0Z will be attached to the valve, 3 in front and 3 in the rear. The values obtained by these sensors are read via an interference-proof 4-20 interface by the Brake ECU.In case of an error such as loss of power or microcontroller failure the switch opens the SDC and the EBS will activate
![image](https://github.com/user-attachments/assets/686856be-9a5e-4575-a551-bddbee14582d)


4. System Operation during Demonstration
During the demonstration and test runs the sensors will be powered though the Power Distribution Unit PDUdepending upon the stage of operation of the pod, for eg: the cooling sensors will not be powered in the accelerationphase but during the cruising and deceleration phase of the run due to them being useful in the said phases. Thesensors are expected to provide a complete set of data ranging from position, velocity, temperature and pressure.



5. Risks and Safety
Needed for: ITD, FDD
For each Subsystem a Risk assessment of the component needs to be done. This is especially important for safety critical components such as brakes, the HV-System and safety Sensors, but also needed for the other subsystems. This includes a decription of:
Which features of the system incorporate the highest safety risks?
How likely is that failure
For such a Risk assessment, an FMEA is a suitable method. See FMEA - Wikipedia



6. Testing and Validation
Sensor ECU - Analog input low pass filter: Checking of cut off frequency 50 Hz and scaling factor.•
Analog input conversion: Converting raw readings to PT100 temperatures (LIM temperature), NTC 10ktemperatures (PE cooling) and gap height sensor are correct. For the temperatures, an external temperature was used.
IMU driver: The IMU axis and read values are correct. The measured values were compared to the known gravitational acceleration for validation.
Fiducial Sensors: The value read by the laser sensor was confirmed with a tape measure.•Wheel Encoder: One revolution of the wheel encoder leads also to one revolution measured.•Stripe sensor: Verified stripe counting works correctly
Testing procedure:

Sensors data range check: All sensor values are checked for plausibility against limit values. If an implausible sensor reading is detected, the shutdown circuit will be opened.
Sensor data plausibility check: The data of different sensors is compared for plausibility. The position estimate based on the velocity sensor is compared with the stripe counter and on a too-high derivation, the shutdown circuit will be opened
The Sensor ECUs and the emergency brake ECUs are watchdogs interlocked via a heartbeat message over the CAN bus. If one of the ECUs fails, the other ECUs can open the shutdown circuit and therefore bring the pod to a safe state.


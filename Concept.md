SENSOR CATEGORIZATION
SNo	CATEGORY	SENSOR NAMES	MODEL OPTIONS	QUANTITY	PLACEMENT
1	POSITION	Inertial measurement unit( IMU)	TDK InvenSense ICM-20602	3	Front, centre, back
Wheel Encoders	DBS36E-BBAK02048	2	Front wheels
Optical sensors (MAIN- POSITION/CONTROL)	Correvit SFII: 2-axis optical sensors- Type CSF2A…OR CORRail®1000	1	Front, centre, back
Stripe sensor(navigation aid sensor)	WL4SL-3F2232	2	Bront, one on each side
GPS Module		Ublox GPS Neo 6m		1		Back
2	TEMPERATURE	Infrared sensors or Thermistor/thermocouple	T-GAGE™ M18T Series	1	battery
Cable Resistance Thermometer	PT100 M-OK / SH	8	evenly distributed along the length of LIM
Temperature sensor	NTC 10K 3950	3	1-cooling tank : reservoir centre
1-between pump and power electronic unit(PEU)
1- between power electronic(PE) outlet and reservoir
3	PRESSURE	Pneumatic	PBT-RB016SG1SSNAMA0Z	6	3 front, 3 back
Edit
Some comments from me:

The DBS36E-BBAK02048 encoder will not work for you, since it cannot go fast enough. You have to consider two limiting factors:
Mechanical maximum frequency: Use your planned maximum speed and the wheel diameter (ask mechanics guys) to check if the maximum RPM is within the range. (probably fine)
Electrical maximum frequency: Our encoder outputs 2048 impulses per revolution, multiply the number of pulses per revolution with the maximum RPM and it must be below 300kHz. (might be problematic, you might have to use a lower resolution than 2048. But do not lower it too much since then the resolution will get worse.)
Stripe sensor: The WL4SL cannot be used for counting stripes because it detects multiple pulses per stripe. This is because the measurement spot of the WL4SL is a small laser. A sensor with an LED light source that has a bigger diameter might not have this problem and might be more suitable.
So a different stripe sensor can be chosen which can be then used as an absolute position reference during the run?

Optical sensors: The correvit is very very expensive (> 15.000€), so not sure if we will get it. And it measures 2-axis, but we only need 1-axis (Only the distance along the track is important for us). So perhaps you can find a cheaper alternative with only 1-axis. And we will definitely get not more than one ;)
Did you talk to the other division if they have some special sensor needs? For example:
Displacement sensors: Last year the mechanics said that they wanted to use displacement sensors to measure the suspensions displacement in the y-direction. Did they say something to you about this?
Jenoptik LDM71: laser distance sensor - it measures the travelled distance of the pod up to 270 m with an update frequency of 40 kHz (it shall be clarified with the mechanical guys regarding the same and added to the list and schematics). Quantity: 2, placement: front and back.

IMUs: On each sensor shield, there are three IMUs mounted. The values of the three IMUs are averaged to reduce the noise.
Temperature: We did not use the T-GAGE™ M18T Series last year. We had the NTC 10k for the cooling system and PT100 M-OK / SH sensors for the LIM.
What about the battery temperature measurement?

GPS: Especially with RTK, GPS could be an interesting option. Normally, GPS does not update faster than once per second (fast modules max 10Hz), so this need to be integrated well into the fusion system
— Florian Keck 2021/10/26 16:58
Edit
SENSOR CONCEPT 1
IMU + WHEEL ENCODERS + OPTICAL SENSORS

Using wheel encoders to calculate the distance the pod has traversed on the track we obtain a precise position of the pod. Elaborating on the foundation of the Season 1 concept and using a wheel encoder as one of the main position estimations sensors, the aim is to form a complete position data set of the pod during its run.
While IMU (inertial measurement unit) acts as an accelerometer and gyroscope, giving us the angular orientation and linear acceleration of the pod at once thus acting as an orientation sensor. These are integral to the pod’s state estimator for active control
The optical sensor conveys data about the surface irregularities and height from the surface (allowing us to avoid the use of air gap sensors)
SNo	SENSOR NAME	DATA PURPOSE	PLACEMENT	RELEVANCE	PROS	CONS
1	IMU	acts as an accelerometer and gyroscope, giving us the angular orientation and linear acceleration of the pod at once	Front, centre and back (1×3)	POSITION ESTIMATION	Can quickly represent high dynamic speed profiles using integration	Error accumulates over time, known as “drift.” because the device is always measuring changes relative to itself, noisy
2	WHEEL ENCODERS	used to determine the pod’s velocity and travelled distance	Front wheels(x2)	POSITION ESTIMATION	It boasts a high accuracy encoder with some precision devices on the order of 5 arcseconds (0.0014 degrees)		The encoder can only report on the position of the equipment it is monitoring. If there is a mechanical error, the encoder cannot improve performance, moderate design complexity.	
3	OPTICAL SENSORS	measures longitudinal and transverse dynamics at high speed	Front (x1)	POSITION ESTIMATION	high sensitivity, immunity to electromagnetic interference, small size, lightweight, robustness, flexibility	limited dynamic range, ambient light can interfere with their operation, high component cost, a new concept- hasn't been tested by us and thus no reference for performance
Edit
Edit
SENSOR CONCEPT 2
IMU + WHEEL ENCODER + GPS MODULE

GPS Module is the only difference between concepts 1 and 2. In case the wheel encoders fail to perform the task of position estimation through the displacement of the pod the GPS module will act as the failsafe for position estimation. A tracking system comprises of mainly three parts- vehicle unit, fixed based station and database with a software system. The vehicle unit(pod) incorporates the hardware part.



SNo	SENSOR NAME	DATA PURPOSE	PLACEMENT	RELEVANCE	PROS	CONS
1	IMU	acts as an accelerometer and gyroscope, giving us the angular orientation and linear acceleration of the pod at once	Front, centre and back	POSITION ESTIMATION	Can quickly represent high dynamic speed profiles using integration	Error accumulates over time, known as “drift.” because the device is always measuring changes relative to itself, noisy
2	WHEEL ENCODERS	used to determine the pod’s velocity and travelled distance	Front wheels (x2)	POSITION ESTIMATION	It boasts a high accuracy encoder with some precision devices on the order of 5 arcseconds (0.0014 degrees)		The encoder can only report on the position of the equipment it is monitoring. If there is a mechanical error, the encoder cannot improve performance, moderate design complexity.	
3	GPS MODULE	calculates its position by precisely timing the signals sent by GPS satellites high above the Earth	Back (x1)	POSITION ESTIMATION	ease of access, signal availability	depends on sufficient received signal quality. GPS signal gets affected due to the multipath, atmosphere (i.e. ionosphere), electromagnetic interference etc, high configurational complexity, initialization of the GPS takes time
Edit
Edit
SENSOR CONCEPT 3
IMU + GPS MODULE + OPTICAL SENSOR + FIDUCIAL(STRIPE SENSOR)

The Fiducial sensors Sick WL4SL-3F2232 commonly known as stripe or navigation aid sensors detect the navigation aids that are placed every 15 meters on both sides along the track, The sensor shines light against the walls and reads the reflected signal.
The data obtained is as an additional confirmation for position estimation thus acting as a major safety sensor for the pod. In case the wheel encoders fail to perform the task of position estimation through the displacement of the pod, stripe sensors will be used to calculate the distance traversed by using the navigation aid stripes(if provided)
Basically, an object placed in the field of view of an imaging system which appears in the image produced, for use as a point of reference or a measure.” In other words, fiducials help machines recognize where an object is in its space
| SNo || SENSOR NAME || DATA PURPOSE || PLACEMENT || RELEVANCE || PROS || CONS || | |
| 1 || IMU || acts as an accelerometer and gyroscope, giving us the angular orientation and linear acceleration of the pod at once || Front, centre and back(1×3) || POSITION ESTIMATION || Can quickly represent high dynamic speed profiles using integration || Error accumulates over time, known as “drift” because the device is always measuring changes relative to itself, noisy || | |

2	WHEEL ENCODERS	used to determine the pod’s velocity and travelled distance	Front wheels(x2)	POSITION ESTIMATION	It boasts high accuracy encoder with some precision devices on the order of 5 arcseconds (0.0014 degrees)		The encoder can only report on the position of the equipment it is monitoring. If there is a mechanical error, the encoder cannot improve performance, moderate design complexity.			
3	GPS MODULE	calculates its position by precisely timing the signals sent by GPS satellites high above the Earth	Back (x1)	POSITION ESTIMATION	lose some accuracy in their interpretation of the signals ie: delaty due to surroundings	depends on sufficient received signal quality. GPS signal gets affected due to multipath, atmosphere (i.e. ionosphere), electromagnetic interference etc	
4	FIDUCIAL(stripe) SENSOR	used to measure how far the pod has travelled on the track and gives us the absolute position reference during the run	Front (x2)	POSITION ESTIMATION	provides real time data without any delay or drift in data value	If stripes are non-uniform the output varies multiple times which disrupts the counting of stripes, navigation aid stripes needed for them to operate		
Edit
Edit
SAFETY SENSORS
SNo	SENSOR NAME	SAFETY PURPOSE	PLACEMENT	CONCEPTS USED IN	RELEVANCE	PROS	CONS
1	FIDUCIAL(stripe) SENSOR	Detect the navigation aids that are placed every 15 meters on both sides along the track. The data is not used in the state estimation, but serves as a additional validation of the estimated position. If the two values diverge, the pod will transition into fault mode.	Front (2x)	1st,2nd	SAFETY CHECK SENSOR	provides real time data without any delay or drift in data value	If stripes are non-uniform the outvaries multipls times which disrupts the counting of stripes which may provide irregular displacement data
2	PNEUMATIC PRESSURE SENSORS	They are used in the EBS(Emergency Braking System), and are responsible for monitoring the data by interfacing through brake ECU's in the front and the back of the pod.	Front(x3) and back(x3)	1st, 2nd, 3rd	SAFETY CHECK SENSOR	values are read via an interference-proof 4-20 mA interface by the brake ECU	Seperate ECU's are required for pressure sensors (brake ECU)
3	TEMPERATURE SENSORS	Multiols temperature sensors used across the pod monitor the ambient temperature of various components and also the ECU	battery(x1), along the length of LIM(x8), cooling tank : reservoir centre(x1), between pump and power electronic unit(PEU)(x1), between power electronic(PE) outlet and reservoir(x1)	1st, 2nd, 3rd	SAFETY CHECK SENSOR	inexpensive, simple and roboust	slow response time ad low sensitivity to small temperature changes
Edit
Edit
OVERALL SCHEMATIC


Looking good! Each ECU already has a microcontroller on board. All the ECUs are connected to each other using the CAN bus then. — Florian Keck 2021/10/26 18:03

Edit
SENSOR PLACEMENT

![image](https://github.com/user-attachments/assets/d3dbbdff-83b2-4204-af12-0513364ad7cf)

SENSOR CONCEPT 1
IMU + WHEEL ENCODERS + OPTICAL SENSORS

Using wheel encoders to calculate the distance the pod has traversed on the track we obtain a precise position of the pod. Elaborating on the foundation of the Season 1 concept and using a wheel encoder as one of the main position estimations sensors, the aim is to form a complete position data set of the pod during its run.
While IMU (inertial measurement unit) acts as an accelerometer and gyroscope, giving us the angular orientation and linear acceleration of the pod at once thus acting as an orientation sensor. These are integral to the pod’s state estimator for active control
The optical sensor conveys data about the surface irregularities and height from the surface (allowing us to avoid the use of air gap sensors)

![image](https://github.com/user-attachments/assets/9daa52be-4698-4b00-a412-6cc750ea9cda)

SENSOR CONCEPT 2
IMU + WHEEL ENCODER + GPS MODULE

GPS Module is the only difference between concepts 1 and 2. In case the wheel encoders fail to perform the task of position estimation through the displacement of the pod the GPS module will act as the failsafe for position estimation. A tracking system comprises of mainly three parts- vehicle unit, fixed based station and database with a software system. The vehicle unit(pod) incorporates the hardware part.

![image](https://github.com/user-attachments/assets/3bfbed17-3568-43cf-a8d4-8284796b5c61)

SENSOR CONCEPT 3
IMU + GPS MODULE + OPTICAL SENSOR + FIDUCIAL(STRIPE SENSOR)

The Fiducial sensors Sick WL4SL-3F2232 commonly known as stripe or navigation aid sensors detect the navigation aids that are placed every 15 meters on both sides along the track, The sensor shines light against the walls and reads the reflected signal.
The data obtained is as an additional confirmation for position estimation thus acting as a major safety sensor for the pod. In case the wheel encoders fail to perform the task of position estimation through the displacement of the pod, stripe sensors will be used to calculate the distance traversed by using the navigation aid stripes(if provided)
Basically, an object placed in the field of view of an imaging system which appears in the image produced, for use as a point of reference or a measure.” In other words, fiducials help machines recognize where an object is in its space

![image](https://github.com/user-attachments/assets/0194a6e1-870d-4383-a813-126a31116fcc)

SAFETY SENSORS
![image](https://github.com/user-attachments/assets/1baba790-dbe9-4727-9aa1-a2efdcbf1065)

OVERALL SCHEMATIC
![image](https://github.com/user-attachments/assets/7295d418-1a20-41f4-9085-a4992ca5dde3)

SENSOR PLACEMENT
![image](https://github.com/user-attachments/assets/529d1985-73bc-4fa2-9b5b-0912cd557744)







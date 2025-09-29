# Exam
![[M1.png]]

# Projects
![[M2.png]]
![[M3.png]]

# Why/How mobile apps differ from desktop one?
Three main reasons: 
- Smaller Screen size 
	- Organize the information accordingly, e.g., list 
- Reacher Input/output system: 
	- Sensors: sensors (GPS, orientation), output: vibration, .. 
	- Camera 
- Energy consumption and efficiency 
	- Apps have a lifecycle (can be suspended) 
	- Memory management 

# Data processing
![[M4.png]]
# Device Orientation
![[M5.png]]

```ad-question
title: HOW ORIENTATION BECOMES AN INPUT?
From orientation it is easy to derive two tilt angles (respect to the Local Tangent Plane), that can become inputs of an app.

![[M6.png]]

```

## Pose Estimation
- The problem of determining $R$ from sensor readings is known as pose estimation problem or attitude estimation.
- One simple algorithm also used in android is the TRIAD algorithm that uses accelerometer and magnetometer readings (this is what android also uses). 
- A more sophisticated estimation uses the gyroscope and an Extended Kalman filter for fusing all data and makes the orientation available as a rotation vector.

![[M7.png]]

## Behind image processing
- Image Access 
- OpenCV (Open Source Computer Vision Library) 
- Image processing is just the surface of the capabilities of the library 
	- more than 2500 state-of-the art optimized algorithms

![[M9.png]]
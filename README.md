# **Active-Mass-Suspension**

## **Introduction** 

Active suspension systems improve ride comfort, handling and stability by dynamically adjusting suspension parameters. 
Four controllers were used :
### 1. PID 
   - Adjusts damping force using Proportional (Kp), Integral (Ki), and Derivative (Kd) constants.
   - Tuned parameters using the Ziegler-Nichols method for optimal performance.
     
### 2. Fuzzy 
   - Utilizes a fuzzy logic control system with two inputs (error and rate of change of error) and a single output (actuator force).
   - Error represents the difference between road displacement and the actual displacement of the car body when disturbed.
   - Fuzzy parameters were tuned using Least Mean Square Algorithm.
     
### 3. MPC
   - Calculates optimal control inputs to achieve a predefined control objective while respecting system constraints.
   - MPC toolbox in Simulink was used for this project

### 4. Fuzzy PID
  - Integrates fuzzy logic into the traditional proportional-integral-derivative (PID) control scheme.
  - Fuzzy logic adjusts PID parameters based on the current error, rate of change of error, and integral of error over time.
  - Useful in handling inadequate systems due to uncertainties, non-linearities, or changing operating conditions, where traditional PID controllers struggle.


## System Modelling -

### Active Suspension System Modeling:

- The system models an active suspension system for a quarter car model.
- It consists of two masses: the sprung mass (Mb) representing the vehicle body, and the unsprung mass (Mt) representing the wheel assembly.
- An actuator (force Fs) is added to the passive suspension system to make it an active suspension system, restricting the vertical movement between the two masses.


### Equations of Motion:

- Two equations of motion (EOMs) are derived for the system, one for each mass (Mb and Mt).
- The EOMs consider various forces acting on the masses, including spring forces, damping forces, active suspension force, and gravity.
- The EOMs are provided in the form of second-order differential equations, considering the displacements and velocities of the masses and the road surface.



### State-Space Representation:

The system is represented in a state-space form, with four state variables, two inputs (road surface velocity and control force), and two outputs (suspension travel and body acceleration).

Based on the equations the system was modelled on SIMULINK


![image](https://github.com/sagneeksengupta/Active-Mass-Suspension/assets/103427128/6850ef2f-b16b-4b9b-ad4c-f4174e2eae42)









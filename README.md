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


## System Modelling 

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
|:--:|
| *Figure 1: Suspension System Modelling on Simulink* |



The system is then connected to the four different controllers on Simulink


![image](https://github.com/sagneeksengupta/Active-Mass-Suspension/assets/103427128/0fce8137-d2ad-4eec-a0e9-37ad884a0dea)
|:--:|
| *Figure 2: Active Suspension system with four controllers* |

## Result

After simulating the system using all four controllers we obtained the following results

### Table: Simulation results of the four controllers

| Controller | Settling time(s) | Overshoot % | Maximum Peak |
|------------|------------------|-------------|--------------|
|            | Car displacement | Car displacement | Car displacement |
|            |                  |             |              |
| Open loop  | -                | 186.596     | 2.264        |
| PID        | 4.2              | 15.698      | 1.159        |
| Fuzzy      | 1.4              | 24.375      | 1.003        |
| Fuzzy-PID  | 0.98             | 0.501       | 1            |
| MPC        | 1.75             | 19.88       | 1.002        |


## Inference 

Based on this information we are able to arrive at our inference on which controller is the better suited and gives the most optimum results

### Overshoot:
The Fuzzy PID controller exhibits the lowest overshoot percentage (0.501\%), indicating superior performance in controlling overshooting compared to other controllers.
PID and Fuzzy controllers also demonstrate relatively low overshoot percentages compared to the Open Loop and MPC controllers.
### Maximum Peak:
For car displacement, among the controllers the PID controller has the highest maximum peak value (1.159), followed closely by the Fuzzy controller (1.003). The Fuzzy PID controller has the lowest maximum peak value for car displacement (1).
Regarding tyre displacement, the Fuzzy PID controller has the highest maximum peak value (2.171), while the Open Loop controller has the lowest maximum peak value (1.549).
### Settling Time:
The Fuzzy PID controller demonstrates the fastest rise time for car displacement (0.98s), suggesting efficient response and settling time.
The PID controller exhibits the longest rise time for car displacement (4.2 s).
### Overall Performance:
The Fuzzy PID controller stands out for its low overshoot, relatively low maximum peak values, and fast rise time, indicating robust performance across different metrics.
The PID and Fuzzy controllers also show competitive performance, particularly in terms of overshoot and maximum peak values.
The MPC controller generally performs moderately, although it shows relatively slower rise times compared to the Fuzzy PID and PID controllers.

### Summary

In summary, the Fuzzy PID controller appears to offer the best overall performance among the evaluated active suspension controllers, with low overshoot, controlled maximum peak values, and fast response times for both car and tyre displacements. However, further analysis and experimentation may be necessary to confirm these conclusions and identify the most suitable controller for specific application requirements.












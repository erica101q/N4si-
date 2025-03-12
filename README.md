# N4si-Analytical Dynamics AE 544 Project
## Different Representations Analyzed
In this project, the representation of Euler angles, quaternions, and classical Rodrigues parameters was explored. The major problem with using Euler angles to analyze a system's rotation is gimbal lock. Gimbal lock occurs when the system loses a degree of freedom, which can cause confusion. An ambiguity with quaternions is a negative sign change in the plots over time, but when the quaternion changes from positive to negative, it does not affect the attitude or angular velocity. Classical Rodrigues parameters have an ambiguity when phi in the scalar part of the equations is 180 degrees. When the system reaches this 180 degrees, it leads to inaccuracies and instability within the system. Each representation can show how a system behaves, but each system has its own faults. In the plots generated for Euler angles from the code, gimbal lock is detected when theta reaches or is close to pi/2. The plots also show the quaternion ambiguity with the negative sign flip. The classical Rodrigues parameters' ambiguity is seen in the plots when Bo in the plot is equal to zero utilizing the phi angle of 180 degrees. This is showed in the plots when the code is run to completion. 
## ODE 45, ODE 15, and ODE 23 Comparison
Each ODE function is a way to solve differential equations. However, ODE15s and ODE23s are for stiffer systems that have nonlinear equations. What the stiff ODE function can do is smooth over the system, causing gimbal lock not to be detected, as seen in the code. In the code, specifically for classical Rodrigues parameters, ODE23s was needed to solve the differential equation because the Rodrigues parameters involve more complex and nonlinear equations. A major problem that arose when using ODE45 for classical parameters is that it didn't run for the entire time span selected, so a smaller time step was needed, and a different ODE function had to be used. A small change occurred when changing from ODE45 to ODE23s, as the system was able to extend for a second. However, because it was a small change, ODE45 and ODE15 were explored using the Euler angles. Furthermore,if the time is put into increments the system can last up until the desired time such as tspan[0,10],tspan[10,20]. As stated before, the function smooths over the system and gimbal lock is not detected. The plot below shows the two functions in the Euler angles representation.
![Euler_ANgles_Final_Plots](https://github.com/user-attachments/assets/2735dcf9-1860-4ce5-985b-00f65d4e8161)
## Plot Explanation
The plot shows the system shifting towards the top away from the desired gimbal lock number which is pi/2. In the ode45 system the system is able to hit pi/2 and gimbal lock is detected however ode15s doesnt allow that. As stated before this is due to the way the differential equations are solved. Due to the function reducing the step size to a very small value the ambiguity is skipped over and the plot above shows that.  
## How to Use the MATLAB Code
### Intial Values and What to Change 
y0=[0.01,0.01,0.01,0.01,0.01,0.01]; For Euler Angles
y0q=[1,0.01,0.01,0.01,0.01,0.01,0.01]; For Quaternions
tspan=[0,2000];
y0r=[1,0.01,0.01,0.01,0.01,0.01,0.01]; Rodrigues Parameters
tspanr=[0,26];
The first 3 is the vector for euler angles and the first 4 is for the quaternions and rodrigues which is the scalar first and then the vector. The last 3 numbers for all are the angular velocites. wx,wy,wz or omega 1,omega 2, omega 3. 
These five variables are the variables to be changed within the code. However, the ambiguity and singularity are already set into place and the plots produced in the code are with the singularies. The above values are the intial conditions however in the code the variables change to the following:
y0=[0.01,0.01,0.01,0.01,0.07,0.01]; For Euler Angles
y0q=[1,0.01,0.01,0.01,0.01,0.07,0.01]; For Quaternions
tspan=[0,2000];
y0r=[1,0.01,0.01,0.01,0.01,0.07,0.01]; Rodrigues Parameters
tspanr=[0,26];
Furthermore changing these variables will change the plots and detections of gimbal lock and the 180 degree error.
### Why change the wy value in the code?
In the assignment a hint was given to change the angular velocities. The angular velocitiy was changed until an ambiguity or singularity was displayed then that change was kept with all 3 representations. 
### What needs to be installed
MATLAB 2024a, ode45 tool,ode15s tool ,ode23 tool,

# Adaptive Model Predicitive Control - Matlab

## Description

This repository contains the project of an adaptive Model Predictive Control (aMPC) algorithm that was executed using the Matlab/Simulink environment. The first file **aMPC_parameters.m** is a Matlab script that stores all the variables needed to run the system model in the Simulink environment. The Simulink model consists of two main elements:
  - a control object - first order inertia with variable parameters such as static gain K, time constant T and transport delay $$ T_{0} $$. It is possible to choose the characteristics of the changes of the given parameters. 
  - aMPC controller - a block containing the main control system algorithm, but also a reference trajectory that can be modified.

The aMPC controller block has some input parameters, such as
  - rho - weight of the objective function for the control signal,
  - L - control horizon,
  - H - prediction horizon,
  - Ts - sampling time,
  - n - order of the polynomial describing the object in the form of impulse response,
  - t - clock input specifying the current time.








## How it works

Model Predictive Control is based on using a mathematical model of control object to predict its behaviour a few moments ahead, at the prediction horizon, on the basis of a known reference trajectory. The idea is to determine the control signal values, on the control horizon, which are applied to the object at a given moment in time specified by a sample time. Control signal values are calculated in such a way as to minimise a certain control quality indicator J. Thanks to this solution, it is possible to generate the appropriate control signal earlier, before a change of the setpoint occurs. 

Control quality indicator can be desribed by an equation given below:

$$ min  J = \sum_{i=1}^{H} \left[ \overline{y}(k+i|k) - y_{ref}(k+i|k) \right]^{2} + \rho \sum_{i=0}^{L-1} \left[\Delta u(k+i|k) \right]^{2} $$ 

where:
- \overline{y}(k+i|k) - prediction of the output signal for k+i time, calculated in k time,
- \Delta u(k+i|k) - control signal increment for k+i time, calculated in k time,
- y_{ref}(i+j) - reference trajectory for k+i time, calculated in k time.

The adaptive MPC control system additionally uses a mechanism for estimating the parameters of the control object. Thanks to this it can adapt itself to changing operating conditions. The gradient method uses an approximation of the gradient of the objective function to obtain the largest error drop in a given step.

It uses the step response of the control object to estimate its parameters. In the first moments of time, this object is excited by a constant control signal in order to obtain the step response. On the basis of the collected response samples, the object parameters used in the AMPC algorithm are determined.

## Launch

To run the program, please run the Matlab environment and open the **aMPC_parameters.m** file. After that click on the Run button. Next run the Simulink toolbox and open **aMPC_simulink_model.slx** file. Click Run button to start the simulation. On the scope you can see some diagram like control object output, reference trajectory and control signal increment. 

## Summary

The project is a good base for further development. You can try to add a different control object, more complex to see if the algoritm will also work well. There is a plenty parameters to adjust and see how they affect the system. You can also try experimenting with another parameter estimation mechanism like LSE (Least Square Error).

This algorithm was made for study exercises and tested in different ways.

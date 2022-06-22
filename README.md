# Adaptive Model Predicitive Control - Matlab

## Description

This repository contains the project of an adaptive Model Predictive Control (aMPC) algorithm that was executed using the Matlab/Simulink environment. The first file **aMPC_parameters.m** is a Matlab script that stores all the variables needed to run the system model in the Simulink environment. The Simulink model consists of two main elements:
  - a control object - first order inertia with variable parameters such as static gain K, time constant T and transport delay T<sub>0</sub>. It is possible to choose the characteristics of the changes of the given parameters. 
  - aMPC controller - a block containing the main control system algorithm, but also a reference trajectory that can be modified.

The aMPC controller block has some input parameters, such as
  - rho - weight of the objective function for the control signal,
  - L - control horizon,
  - H - prediction horizon,
  - Ts - sampling time,
  - n - order of the polynomial describing the object in the form of impulse response,
  - t - clock input specifying the current time.

## How it works

Model Predictive Control is based on using a mathematical model of a control object to predict its behaviour a few moments ahead, at the prediction horizon, based on a known reference trajectory. The idea is to determine the values of control signals at the control horizon that are applied to the object at a given moment in time defined by the sampling time. The values of the control signals are calculated in such a way as to minimise a certain control quality indicator *J*. This makes it possible to generate the appropriate control signal in advance, before the setpoint is changed, and by limiting the influence of uncertainties in the system.

The control quality indicator can be described by the equation given below:

$$ min J = \sum_{i=1}^{H} \left[ y(k+i|k) - y_{ref}(k+i|k) \right]^{2} + \rho \sum_{i=0}^{L-1} \left[\Delta u(k+i|k) \right]^{2} $$  

where:
- y(k+i|k) - prediction of the output signal at time k+i, calculated at time k,
- $ \Delta u(k+i|k) $ - increment of the control signal at time k+i, calculated at time k,
- $ y_{ref}(k+i|k) $ - reference trajectory at time k+i, calculated at time k.

The adaptive MPC control system additionally uses a mechanism of estimation of control object parameters. This allows it to adapt to changing operating conditions. Thus, the model of the controlled object is determined on an ongoing basis during the operation of the control system. The gradient method was used to estimate the parameters of the object. The gradient method uses an approximation of the gradient of the objective function in order to obtain the greatest decrease in error in a given step.

In the first moments of time, this controlled object is excited by a constant control signal to obtain a step response. From the collected samples of this response, the estimation algorithm determines the parameters of the controlled object that are used in the control algorithm.

## Launch

To run the program, start the Matlab environment and open the **aMPC_parameters.m** file. Then click on the Run button. Then run the Simulink toolbox and open the **aMPC_simulink_model.slx** file. Click the Run button to start the simulation. The scope shows graphs such as the control object output, reference trajectory and control signal increment. 

## Summary

The project is a good base for further development. You could try adding another control object, more complex, to see if the algorithm would also work well. There are many parameters that you can adjust and see how they affect the system. You could also try experimenting with another parameter estimation mechanism such as LSE (Least Square Error).

This algorithm was created for research exercises and has been tested in various ways.

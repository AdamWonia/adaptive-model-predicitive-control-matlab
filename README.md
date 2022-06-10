# Adaptive Model Predicitive Control - Matlab

## Description

This repository contains a project of adaptive Model Predicitive Control (aMPC) algorithm which is made using Matlab/Simulink environment. First file **xxx.m** is the Matlab script in which are stored all variables needed to start a Simulink model of the system. The Simulink model consists of two main elements:
  - control object - simple, first order inertia with variable parameterers like static gain K, time constant T and transport delay. All these parameters can be switched between different changing. 
  - aMPC controller - block which contains main algorithm of a control system, but also reference trajectory which could be modified.

aMPC controller block has some input parameters like:
  - rho - objective function weight for control signal
  - L - control horizon
  - H - prediction horizon 
  - Ts - sample time
  - n - order of polynomial describing the object in the form of impulse response
  - t - clock input specifying the current time

## How it works

Model Predictive Control is based on using a mathematical model of control object to predict its behaviour a few moments ahead, at the prediction horizon, on the basis of a known reference trajectory. The idea is to determine the control signal values, on the control horizon, which are applied to the object at a given moment in time specified by a sample time. Control signal values are calculated in such a way as to minimise a certain control quality indicator J. Thanks to this solution, it is possible to generate the appropriate control signal earlier, before a change of the setpoint occurs. 

Control quality indicator can be desribed by an eqution given below:

** J = ... **

The adaptive MPC control system additionally uses a mechanism for estimating the parameters of the control object. Thanks to this it can adapt itself to changing operating conditions. The estimation mechanism is based on the recursive gradient method, which is described below.

** EST = ... **

It uses the step response of the control object to estimate its parameters. In the first moments of time, this object is excited by a constant control signal in order to obtain the step response. On the basis of the collected response samples, the object parameters used in the AMPC algorithm are determined.

## Launch

 - how to lauch the program and how to use it

## Summary

- co można jeszcze zmienić
- co można dodać od siebie

## TO DO
- math formulas of algorithm
- parameters to adjust
- description of control object and disturbances


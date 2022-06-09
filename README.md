# Adaptive Model Predicitive Control - Matlab

This repository contains a project of adaptive Model Predicitive Control (aMPC) algorithm wchich is made using Matlab/Simulink environment. First file **xxx.m** is the Matlab script in which are stored all variables needed to start a Simulink model of the system. The Simulink model consists of two main elements:
  - control object - simple, first order inertia with variable parameterers like static gain K, time constant T and transport delay. All these parameters can be switched     between different changing. 
  - aMPC controller - block which contains main algorithm of a control system, but also reference trajectory which could be modified. 

aMPC controller block has some input parameters like:
  - rho - coefficient for algorithm speed adjusting
  - L - control horizon - 
  - H - prediction horizon - 
  - Ts - sample time - 
  - n - number of samples - 
  - ....

## How it works

## Launch

## Summary

- opis projektu

## TO DO
- what is an MPC controller
- what is an adaptive MPC and what are the advantages of it
- math formulas of algorithm
- parameters to adjust
- description of control object and disturbances


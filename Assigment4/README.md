# Assignment 4

## Introduction

![Neural network](https://github.com/eva-6-3/nn_image_number/blob/main/Assigment4/NeuralNetwork.jpg)

The Neural network has two inputs i1 and i2 and it contains two layers h and o. 
Output of the final layer is e_total and this is sum of e1 and e2.
The neural network is fully connected layer having two neurons in each of the layer. 
The neurons are connected by weights w1, w2, ..., w8.
The input layer i1, i2 is connected to hidden layer neurons h1 and h2 through weights w1,w3 and w2, w4 respectively. 
The neurons h1 and h2 gets activated through sigmoid functions and becomes a_h1 and a_h2.
The activated neurons a_h1 and a_h2 gets connected to output neurons o1 and o2 through weights w5,w7 and w6,w8 respectively. 
The output layer neurons are also gets activated by sigmoid function and these activated neurons are called a_o1 and a_o2. 
The activated neurnns producess output e1 and e2 and finally give the output e_total which is sum of e1 and e2.

## Learning rate chart
![Learning Rate chart for different learning rates](https://github.com/eva-6-3/nn_image_number/blob/main/Assigment4/Learning_Rate.png)

## Excel Sheet experiment
![Neural Network excel sheet](https://github.com/eva-6-3/nn_image_number/blob/main/Assigment4/NeuralNetwork.xlsx)

## Calculations
### Forward Propagation

- h1 = w1 * i1 + w2 * i2
- h2 = w2 *i2 + w4 * i2

- a_h1 = σ(h1) = 1 / (1+EXP(-h1))	
- a_h2 = σ(h2) = 1 / (1+EXP(-h2))	

- a_o1 = σ(o1)
- a_o2 = σ(o2)

### calculating error
- e1=0.5 * (t1 - a_o1)^2	
- e2=0.5 * (t2 - a_o2)^2	
- e_total = e1 + e2

### Backward Propagation

- ∂ E_total / ∂w5 = ∂ (e1+e2) / ∂w5			
- ∂ E_total / ∂w5 = ∂ e1 / ∂ w5				
- ∂ E_total / ∂w5 = ∂ e1/ ∂ w5 = ∂ e1/ ∂ a_o1 * ∂ a_o1/∂ o1 * ∂ o1/ ∂ w5				
- ∂ e1/ ∂ a_o1 = ∂ (1/2 * (t1 - a_o1)^2) / ∂ a_o1				
- ∂ e1/ ∂ a_o1 = -1 * (t1 - a_o1) = a_o1 - t1				
- ∂ a_o1/ ∂ o1 = ∂(σ(o1)) / ∂ o1 =  σ(o1) * (1 - σ(o1))				
- ∂ a_o1/ ∂ o1 = a_01 * (1-a_o1)		 		
- ∂ o1/∂ w5 = a_h1

- ∂ E_total / ∂w5 = (a_o1-t1) * a_o1 * (1-a_o1) * a_h1			
- ∂ E_total / ∂w6 = (a_o1-t1) * a_o1 * (1-a_o1) * a_h2			
- ∂ E_total / ∂w7 = (a_o2-t2) * a_o2 * (1-a_o2) * a_h1			
- ∂ E_total / ∂w8 = (a_o2-t2) * a_o2 * (1-a_o2) * a_h2			

- ∂ E1 / ∂ a_h1 = ∂ E1 / ∂a_o1 * ∂ a_o1 / ∂ o1 * ∂ o1 / ∂ a_h1 = (a_o1 - t1) * a_o1 * (1 - a_o1) * w5					
- ∂ E2 / ∂ a_h1 = ∂ E2 / ∂a_o2 * ∂ a_o2 / ∂ o2 * ∂ o2 / ∂ a_h2 = (a_o2 - t2) * a_o2 * (1 - a_o2) * w7					
- ∂ E_total/ ∂ a_h1 = (a_o1 - t1) * a_o1 * (1 - a_o1) * w5 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w7					
- ∂ E_total/ ∂ a_h2 = (a_o1 - t1) * a_o1 * (1 - a_o1) * w6 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w8							

- ∂ E_total / ∂ w1 = ((a_o1 - t1) * a_o1 * (1 - a_o1) * w5 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w7) * (a_h1 * (1-a_h1)) * i1						
- ∂ E_total / ∂ w2 = ((a_o1 - t1) * a_o1 * (1 - a_o1) * w5 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w7) * (a_h1 * (1-a_h1)) * i2						
- ∂ E_total / ∂ w3 = ((a_o1 - t1) * a_o1 * (1 - a_o1) * w6 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w8) * (a_h2 * (1-a_h2)) * i1						
- ∂ E_total / ∂ w4 = ((a_o1 - t1) * a_o1 * (1 - a_o1) * w6 + (a_o2 - t2) * a_o2 * (1 - a_o2) * w8) * (a_h2 * (1-a_h2)) * i2			

### Calculation of weights

The different weights are calculated based on below formula:

New_weight = Previous_weight - (Learning_rate * Derivative of Previous_weight)

To view my physics final project, please visit [here](https://www.tychos.org/en/scenarios/q5aJiy). The start button is on the bottom. You can modify the slider any time you want.

### Introduction
You can assign values to many of the variables, such as the mass, force, etc.
For example:  
```slab.m = 2```  
```F_N = [0, slab.m * 9.8]``` (Note that force is a vector quantity)

You can then update the values by manipulating each equation after each dt.  
```slab.v = slab.v + dv``` for updating velocity  
```slab.pos = slab.pos + slab.v * dt``` for updating position  

### Guide

For reading comments on my code, please click the wrench in the top left corner and navigate the Inital State and Calculations tab. I outlined here some of the code that might require more explanation:

```effective = ((F_A[X] > (mu_s * F_N[Y])) * isStationary) or (F_A[X] * (1 - isStationary))```
```effective``` can either give us 1(true) or 0(false). This code tells us whether the applied force will cause a difference in the motion of the slab. Keep in mind, the applied force has to be greater than the coefficient of static friction * normal force in order to move. After that, as long as the slab is always moving(not stationary, ```(1 - isStationary)```) the applied force is effective.

```netF = F_A * effective + F_f_k * pow(-1, (slab.v[X] > 0)) * (1 - isStationary)```
To determine the direction of the frictional force, we know that it acts directly opposite of the motion, so -1 can allow us to switch directions at ease. The ```(1 - isStationary)``` allows us to get 0 frictional force if the object is not moving.

```drawLine([0, 0], [slab.pos[X] + 10, 0], "brown", 5)```
This allows us to take the position of the slab, and extend the surface 10 units end so the slab always has a surface to be on.

Of course, feel free to change any of the values in the Inital State (such as kinetic/static friction) to experiment what will happen with the slab. You can also slide the slider while the object is moving to "stop" the slab. 

Enjoy!

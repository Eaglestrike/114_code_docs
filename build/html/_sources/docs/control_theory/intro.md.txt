# Introduction to control theory

Getting the motor to move is cool and all, but not quite useful yet. As code we need to get the motors to DO something which requires control and precision in order to produce reliable and consistent results. For example using a motor to extend an elevator to reach some height. 

As code we control the voltage the motor applies to spin. Control theory is all about manipulating the voltage applied such that the motor spins the way we want it to, whether that be at a specific speed, to get to a certain position, or both.

This is where we step away from syntax and libraries and whatnot and get into the fun stuff.

## Robot kinematics

You might be wondering why this is even a problem to begin with. Can't you just stop once you get to the target? The robot must follow the laws of physics, so no. It takes time for it to speed up and slow down.

Applying voltage simply speeds up or slows down the existing motion of the motor. Unfortunately for us, there is no direct relationship between how much voltage you apply and how much the motor will speed up/slow down, because of the many forces acting on the motor such as electromotive force, load, static and kinetic friction, and heat.

The subject of control theory serves to align the desired motor behavior and the actual motion of the system, despite the complex nature of the behavior of the system.


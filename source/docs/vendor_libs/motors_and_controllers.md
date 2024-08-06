# Motors + Motor Controllers

A motor is a device that takes voltage and applies rotational force.
Basically it's a thing that spins.

A motor controller is what regulates the voltage supplied to the motor.
This is what code interacts with to manipulate how the motor moves.

We mainly use motors from CTRE and REV Robotics. Though code only
interacts with the motor controllers, it’s important to know which
controllers correspond to which motors. In order to communicate with the
controllers, code has to use 3rd party libraries (in the rightmost
column) supplied by the motor vendors (leftmost column).

```{image} images/table1.png 
```
```{image} images/table2.png 
```

There are definitely more motors (like mini NEOs and CIMs) and more
controllers (like the TalonSRX) that we might use but they’re used way
less often. 

# Motor Encoders

Motors apply voltage to make things spin. Encoders can give you information about the work a motor has done and the current state of the moving object. It can read "position", as well as velocity and acceleration.

These built in encoders are relative. This means every time the robot turns on, they reset their position. They are called relative encoders because their position is relative to where they are when they turn on, which can sometimes make it less accurate.
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
less often. If you want to know about those as well, let me know and
I’ll add them.

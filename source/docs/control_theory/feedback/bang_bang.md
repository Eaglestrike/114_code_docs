# Bang-Bang Control

Bang bang control is the simplest controller. If your target is in front of you, go forwards. If it's behind you, go backwards. 

In more technical terms, it's applying a constant output negative to the sign of the error.

One problem with bang-bang control is that since it does not slow down
as it gets to the target, it will consistently overshoot. Once it
overshoots, it will go in the opposite direction and overshoot again,
oscillating and never reaching the target and coming to a stop like we
want it to. 

Even if you use [tolerances](../tolerance.md) and stop applying voltage when you reach near the target, the robot will take time to come to a stop and miss the target, making it either continue to oscillate or to have high error.
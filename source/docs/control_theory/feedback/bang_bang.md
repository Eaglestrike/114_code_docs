# Bang-Bang Control

The simplest control. **Apply a constant output negative to the sign of
the error.** In other words, if it’s positive/ahead, go backwards and if
it’s negative/behind, go forwards.

One problem with bang-bang control is that since it does not slow down
as it gets to the target, it will consistently overshoot. Once it
overshoots, it will go in the opposite direction and overshoot again,
oscillating and never reaching the target and coming to a stop like we
want it to.
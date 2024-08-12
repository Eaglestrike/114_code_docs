================
Feedback Control
================

Feedback control usually is the most intuitive type of control, as it is
what us humans do. We respond to the environment around us and change
our movement accordingly.

The code moves the robot, which impacts the sensor data,
which then is fed back to code, like this:

.. image:: images/image15.png

Essentially, the code takes feedback from it's sensors to adapt what it's doing and better achieve its goal

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Feedback Controllers

   bang_bang
   PID

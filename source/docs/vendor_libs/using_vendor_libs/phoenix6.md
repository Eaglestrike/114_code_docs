# Phoenix6

As of 2024 this is the most recent library released by CTRE. 
## TalonFX
Phoenix6 has a class called [TalonFX](https://api.ctr-electronics.com/phoenix6/release/cpp/classctre_1_1phoenix6_1_1hardware_1_1_talon_f_x.html) which has useful methods to send commands to TalonFX motor controllers as well as to read data from the built in encoders. Motors that use TalonFX include Krakens and Falcons. 
### Include the library
Include the library at the top of the header file (but below the `#pragma once`)
```
#include <ctre/phoenix6/TalonFX.hpp>
```

### Declare the object
Declare the variable in the definition of the class in the header file.
```
ctre::phoenix6::hardware::TalonFX m_motor;
```
Where you replace motor with whatever you want to call the motor. Make sure the variable is private. 

If you don't want to type out the long path to get to TalonFX every time you create a motor, you can declare that you are
```
using namespace ctre::phoenix6::hardware::TalonFX;
```
at the top of the file, and then when you construct the object you can simply write 
```
TalonFX m_motor;
```

### Construct the object
To construct the object, you must pass in the **motor ID** to the constructor. To find the motor ID, you have to run phoenix tuner X on the driver station. If you don't know how to, ask someone from electronics to do it for you. Usually motor IDs are stored as constants in either the header file or in a constants file.

You can also specify settings like whether or not the motor is inverted. **Inverting the motor reverses which direction is positive to the encoder.**

Another important setting is the **brake mode** (of type [ctre::phoenix6::signals::NeutralModeValue](https://api.ctr-electronics.com/phoenix6/release/cpp/classctre_1_1phoenix6_1_1signals_1_1_neutral_mode_value.html)). This controls how the motor behaves when no voltage is applied. If the motor is on coast mode it will not attempt to resist motion when it is idle. If the motor is on brake mode, it will resist motion when idle. 

For example my constructor might include the following:
```
m_motor{MOTOR_ID};
m_motor.SetNeutralMode(ctre::phoenix6::signals::NeutralModeValue::Brake);
m_motor.SetInverted(true);
```

### Set Voltage
Now that the object is constructed, we can use it to make the motor move!
it is always good practice to clamp the voltage before setting it, so that it never goes above the max voltage. Since the [SetVoltage function ](https://api.ctr-electronics.com/phoenix6/release/cpp/classctre_1_1phoenix6_1_1hardware_1_1_talon_f_x.html#a95eeb271496559266ef5894d3671a3dd) doesn't take doubles, we have to typecast the data. So setting the motor to a voltage of *v* might look something like this:
```
double volts = std::clamp(v, -MAX_VOLTS, MAX_VOLTS);
m_motor.SetVoltage(units::volt_t{volts});
```

### Using the relative encoder
[GetPosition()](https://api.ctr-electronics.com/phoenix6/release/cpp/classctre_1_1phoenix6_1_1hardware_1_1core_1_1_core_talon_f_x.html#ac0b84a1fb760ff692dc4eebae34a9b10) returns the position of the motor in turns (1 full rotation = 1 turn)
[GetVelocity()](https://api.ctr-electronics.com/phoenix6/release/cpp/classctre_1_1phoenix6_1_1hardware_1_1core_1_1_core_talon_f_x.html#acfff8403da9f990793d61b32a135f174) returns the velocity of the motor in turns per second
and [GetAcceleration()](https://api.ctr-electronics.com/phoenix6/release/cpp/classctre_1_1phoenix6_1_1hardware_1_1core_1_1_core_talon_f_x.html#ac0a869459063e34623dcaf413587a546) returns the acceleration of the motor in turns per second squared

In order to get this info as a double so its easier to work with you can do:
```
double position = m_motor.GetPosition().GetValueAsDouble(),
velocity = m_motor.GetVelocity().GetValueAsDouble(),
acceleration = m_motor.GetAcceleration().GetValueAsDouble();
```

## CANcoder


# Phoenix5

Phoenix 5 is depreciated and should only be used if you are using a motor that uses the TalonSRX motor controller.
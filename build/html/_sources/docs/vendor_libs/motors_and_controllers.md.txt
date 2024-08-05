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

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 38%" />
<col style="width: 31%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Supplier</th>
<th>Motor(s)</th>
<th>Motor controller</th>
<th>Software library</th>
</tr>
<tr class="odd">
<th rowspan="2"><p>CTRE</p>
<p>(+ vex)</p>
<p>(+ WCP)</p></th>
<th><p>Falcon 500</p>
<p><img src="media/image10.png"
style="width:2.30729in;height:2.07897in" /></p></th>
<th rowspan="2"><p>TalonFX (built on the motor)</p>
<p><img src="media/image11.png"
style="width:1.87716in;height:1.82952in" /></p></th>
<th rowspan="2">Phoenix6</th>
</tr>
<tr class="header">
<th><p>Kraken</p>
<p><img src="media/image13.png"
style="width:2.32675in;height:1.72722in" /></p></th>
</tr>
<tr class="odd">
<th rowspan="2">REV robotics</th>
<th><p>NEO V1.1</p>
<p><img src="media/image12.png"
style="width:2.18265in;height:1.60447in" /></p></th>
<th rowspan="2"><p>SparkMax</p>
<p><img src="media/image3.png"
style="width:1.88021in;height:2.62497in" /></p></th>
<th rowspan="2">REVlib</th>
</tr>
<tr class="header">
<th><p>NEO 550</p>
<p><img src="media/image5.png"
style="width:2.32762in;height:1.54734in" /></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

There are definitely more motors (like mini NEOs and CIMs) and more
controllers (like the TalonSRX) that we might use but they’re used way
less often. If you want to know about those as well, let me know and
I’ll add them.

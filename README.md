In this repository, we control a stepper motor based on the distance of a connected plane from a maximum position. If the plane is within 5 centimeters of this maximum position, we change the direction of the motor's rotation, causing the plane to move in the opposite direction. 

To detect the distance of the plane, we use an ultrasonic sensor, which operates with three signals: GND, Echo, and Trigger. The sensor's timing diagram is as follows:
 ![image](https://github.com/user-attachments/assets/7713acb4-f23f-4dc2-a4db-2d68514d93be)

1. A trigger pulse is sent from the microcontroller to the sensor, prompting it to start working.
2. The sensor emits a series of pulses (8 cycles) into the environment.
3. The echo pulse has a rising edge and waits for the reflected waves to return.

We use two external interrupts to detect the rising and falling edges of the echo pulse. The time spent in this cycle, from sending to receiving the pulses, allows us to calculate the distance of the plane. 

For the stepper motor, we configure three pins: direction, enable, and step. The PWM pin of the microcontroller controls the step pin. If the distance \( d \) is less than 5 centimeters or greater than 35 centimeters, we reverse the motor's direction by changing the digital output pin of the microcontroller. The enable pin is set to 0 because it is active low.

Finally, we display the distance on an LCD.

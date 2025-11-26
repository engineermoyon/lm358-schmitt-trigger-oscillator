# lm358-schmitt-trigger-oscillator
Showing how an LED blinks periodically using an LM358 IC. 
An LED oscillator circuit built using an LM358 op-amp, demonstrating analog circuit design, Schmitt trigger operation, and systematic debugging.
This project evolved from a broken 555 timer IC into a learning journey through op-amp circuit design, hysteresis, and real-world debugging. The final circuit successfully oscillates an LED with clean digital switching using only analog components.

The MATHS: 
Frequency was found to be 0.36Hz rounding to about 20 blinks per minute.
The period is 2.8 seconds per cycle
This was powered by a 5V source (using Arduino Uno and USB as power source directly from my PC).
Used 5 10k ohm resistors, 1 220uF capacitor, 1 LM358 IC and 1 red LED.


Simulation of the circuit:  
<img width="958" height="521" alt="oscillator simulation" src="https://github.com/user-attachments/assets/20569470-1864-42af-acbf-87deb3b0229f" />

Full image of the working circuit: 
![image0 (2)](https://github.com/user-attachments/assets/f4ec463e-049d-45b0-8f14-42c6aedbe429)

I created a voltage reference of 2.5V. Then connected the capacitor to a resistor to build a timing circuit. Then there was a need to create some hysteresis (Positive feedback) to prevent an oscillation around a single point. This was for noise immunity. 

The capacitor gets charged through a 10k ohm resistor, then it switches output when it reaches upper and lower threshold voltages. This repeats indefinitely. 

The error analysis: 
There was a 25% deviation from the theoretical and calculated analysis. 
![IMG_5326 (1)](https://github.com/user-attachments/assets/d5bcc889-830a-44ce-876b-2a337672b07e)


The simulation confirms the Schmitt trigger operation and hysteresis! (I did not think it would be that close). 

The debugging: 
Oh this took me a while to make the perfect circuit and simulation. 
Initially, I had opted in to use an LM555 timer IC but it broke during handling and I had to find an alternative. I then opted to design using an LM358 op-amp which made me learn more about Schmitt triggers. 

I was battling with finding the correct capacitor for the circuit. The 470uF was making the LED blink slower than the 220uF, but also I had used a feedback resistor of 100k ohm to see how it behaved. So the dilemma was between choosing the right capacitor or resistor, but through maths I was able to decide on the frequency I prefered. Because I wanted to show a couple of blinks per cycle, I kept the capacitor at 220uF and switched the 100k resistor until I could find the best value for demonstration. (10k ohm was a good option). Additionally, the 100k was making the LED blink extremly fast (145 blinks per minute!) so I had to change it. 

My future edits: 
Add potentiometer for adjustable frequency
Design PCB version for permanent installation
Add 7-segment display showing count
Implement dual LED (alternating blink) using second half of LM358
Add enable/disable switch

peeeeew!

I have designed an adjustable output buck regulator using LM2596S-ADJ that can regulate an input voltage of 20V to 12V DC output with a constant 2A load current.

The input voltage (20 VDC) is fed through input-side MSTB. The 1N5822 diode ensures that if polarity is accidentally reversed, the circuit won’t be damaged;it blocks reverse current flow. The voltage after D2 (VIN) becomes the main input supply to the LM2596 converter and the indicator LED section. C1 filters the input voltage to the LM2596S-ADJ IC.
Then, LM2596 operates by rapidly switching its internal transistor to control energy delivered to the inductor. During the ON phase, current flows through the inductor and stores energy. During the OFF phase, D1 provides a path for inductor current to flow to the load. The voltage divider (R1, R2) feeds back a portion of the output voltage to the FB pin to regulate output. The feedback equation is:
                                      V_OUT = VREF×(1+R1/R2)
 where VREF=1.23 V
 Plugging in values of R1=8.66k ohm and R2=1k ohm
                                      V_OUT = 1.23×(1+8.66/1) ≈ 12 V 
 Hence, the output voltage is properly set to 12 V.
The inductor L1 and capacitor C2 ensure low ripple voltage by acting as the output filter section.
R3 of 10k ohm and R4 of 2k ohm is selected so that 3.3V appears at the junction, which is perfect for the LED. Also a resistance of 220 ohm is added in series to the LED so that limited current flows through the LED.

I have used the following components:
●	MSTB connectors of 5.08mm pitch for input and output ports so that input and output can be easily attached to or detached from the converter.
●	1N5822 Schottky diode for reverse polarity protection in the input side as well as for freewheeling during switching in the output side due to its current rating while also being cheap and available at the same time. 
●	Surface mount electrolytic capacitors of 150uF for input filter and 330uF for output filter primarily because of their smaller size than through hole capacitors while also being cheap.
●	A shielded inductor of 68uH for output filtering so that its electromagnetic interference is minimized and it does not affect the output power. 
●	Resistors of 0805 metric and <= 1% metal film so that they can be assembled easily in-house.
●	Feedforward capacitor of 390pF of 0805 metric as our output voltage is greater than 10V.
●	LM2596S-ADJ so that we can get a freedom of adjusting output voltage. 

All the values mentioned above have been taken from LM2596 datasheet tables and formulae given in the datasheet. I have also designed and simulated the circuit using WEBENCH Power Designer and TINA-TI. 

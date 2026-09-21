Arduino Light-Based Morse Code Communication

Two Arduinos send a text message using light instead of wires. The transmitter flashes an LED in Morse code. The receiver watches the flashes with a photoresistor and prints the decoded message to the Serial Monitor.

How it works
The transmitter blinks an LED using standard Morse timing: short flashes for dots, long flashes for dashes, and longer pauses between letters and words.
The receiver reads a photoresistor on an analog pin, decides ON or OFF against a threshold, times each flash, and classifies it as a dot or a dash.
The receiver decodes the dot/dash sequence into letters and prints the message over serial.
Hardware

Transmitter

Arduino
LED (white or green works best)
220 ohm resistor
Breadboard + jumper wires

Receiver

Arduino
Photoresistor (LDR / CdS cell)
10k ohm resistor
Breadboard + jumper wires
Wiring

Transmitter

Pin 8 → 220Ω resistor → LED long leg (anode)
LED short leg (cathode) → GND

Receiver (voltage divider)

5V → photoresistor → A0 → 10k resistor → GND

Point the LED at the photoresistor, 1-2 cm apart, and shield both from room light. A dark box works well.

Setup
Upload LED Morse code transmitter Tx to one Arduino. Edit the MESSAGE constant to whatever text you want to send (letters and spaces only).
Upload CdS photocell Morse Code Rx to the other Arduino.
Power the transmitter first so it's already flashing.
Open the receiver's Serial Monitor at 9600 baud. It calibrates itself for about 6 seconds, then prints Ready. Listening... followed by the decoded message.

UNIT (flash timing, in ms) must match in both sketches. It's set to 200 by default.


Troubleshooting
Symptom	Likely cause
"No flashes seen" during calibration	LED not aimed at the sensor, or too much room light
Random ? characters	Threshold too close to noise; move the LED closer
Letters run together or split apart	UNIT doesn't match between the two sketches

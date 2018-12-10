# FischellFancyFlashLight

## Mechanical
A 3D printed case was designed to minimize the size of the device while maintaining a comfortable shape and relative stability. The dimensions are 1.2"x1.8"x2", with a 0.33" deep alcove for the 3 LEDs. The button is flush with the surface of the case, and debounce is performed in software, not hardware. The case is in two parts. The bottom is larger, containing conical holes to for ease of insertion of the LEDs and buttons, and four corner standoffs for the PCB. There are also two alcoves in the bottom for clips to attach the top to the bottom, and two semicircular holes of 0.4" diameter for pinching the top of the case to release the clasps. The top is smaller, with 0.01" of clearance on all sides to fit in the 1.3"x1.5" hole. The clips themselves have 0.05"x0.01"x0.01" clearance on all sides. Printed with 0.8mm wall thickness, 0.2mm layers, and 8% infill, the fit is incredibly tight, making the case very durable without any connective materials. The PCB cannot rattle around in the case due to the tightness and the conical standoffs, and neither can the top relative to the bottom. The case is so durable that it can be thrown at an 8 foot ceiling and fall on to linoleum without any damage. 

## Electrical 
The PCB is 1.25"x1.1" with a 0.05" hole in each corner for the standoffs. The three white (roughly 3.1V voltage drop) LEDs are driven by a MOSFET and connected in series with 10 Ohm resistors. The entire system is controlled by an ATTiny85, which is put into sleep mode for power conservation in the off state. Finally, there are 6 pins connected to the 6 programming pins on the ATTiny so that it can be reprogrammed at any point. A voltage regulator drops the voltage from roughly 6V to 3V, but the system works with a single 3V battery as well. The flashlight has current draws and theoretical battery lives are as follows:

						Battery Life (2 series,	Battery Life 
State:	Current Draw:	320 mAh CR2430):		(1, 1 Ah CR2477): 
Off		34.81 uA		9193 hr = 383 days		28727 hr = 1197 days = 3.28 years
Low		7.300 mA		43.8 hr = 1.83 days		137.0 hr = 5.71 days
Med		22.515 mAh		14.2 hr = 0.59 days		44.41 hr = 1.85 days
High	62.198 mAh		5.14 hr = 0.21 days		16.08 hr = 0.67 days
Flash 	4 mA - 62 mAh	9.70 hr = 0.40 days		30.30 hr = 1.26 days

## Software 
The code is incredibly simple, with interrupts for the button presses, PWM to controll LED brightness, and simple time difference calculation to prevent two button presses within 50 ms (to prevent button bouncing). To reprogram the flashlight, disconnect the batteries and connect the pins on the ribbon cables as follows:


Color: 		ATTiny Pin (PB pin, Mech.):		Arduino Pin:
Red 		Reset (NA, 1) 					Pin 10
Orange 		SCK (2, 7)						Pin 13
Yellow 		MISO (1, 6)						Pin 12
Green		Vcc	(NA, 8)						Power (3.3V or 5V)
Blue 		MOSI (0, 5)						Pin 11
Purple		Ground (NA, 4)					Ground

## Testing 
Every flashlight case ever printed was immeadiately drop tested. The electronic hardware was tested on a breadboard, and the current was tested using a high precision multimeter and an laboratory power supply (see above).
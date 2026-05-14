Reach out to andrew.crook@usu.edu with any questions. 

Use 1 Oz copper
Green soldermask preferred

Most parts have links to both Digikey and JLCPCB. JLCPCB is the preferred supplier, but the big capacitors will need to come from digikey. 
UPDATE: due to cost, I'm only getting the top side assembled, and I'm not getting the ESP32 put on because that will drive up cost. Planning to put the ESP32 with solder paste and the reflow oven at work, and hand solder the back side. 



This section is so I can keep track of what's for what. 
Component purpose/notes:

R11,R12: 	Tell usb to send over 5V
C11,C13,C14,C15:Clean up power to sensors and some ESD protection
C7,C3,C6,C5: 	Clean up power from AMS1117
AMS1117: 	Linear voltage regulator to convert 5V to 3.3V (This is isn't as efficient as a buck converter)
D1: 		Probably not necessary, but this is back current protection. It was in the example. 
R5,R8:		Pull up resistors for the buttons

ESP32: 		This is the brains. Pushing the enable button should reset the board, The IO0 button should make it enter boot mode. 

TMP117: Maybe add in a zero ohm resistor option later so gpio16 can be used for either temperature interrupts or broken out for general IO depending on the assembly? 
	Verify that tying ADD0 to GND gives I2C address 0x48.
	Using recommended 4.7Kohm pull up resistor for SDA and SCL. One source said 2.2K may be better?  

BH1750: Tie ADDR to GND for I2C address 0x23

BME280 Tie CSB to VDDIO for I2C (tie to GND for SPI) With I2C selected, tie SDO to GND for I2C address 0x76 

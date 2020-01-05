# EEPROM-I2c
# Reading and Writing from EEPROM through I2C Signals
 
# Writing a byte of memory to the EEPROM:
1. Send the Most Significant Byte of the memory address that you want to write to.
2. Send the Least Significant Byte of the memory address that you want to write to.
3. Send the data byte that you would like to store at this location.
 
# Reading from the EEPROM:
1. Send the Most Significant Byte of the memory address that you want to write to.
2. Send the Least Significant Byte of the memory address that you want to write to.
3. Ask for the data byte at that location.

# SEPS
All of the bytes in a 512 Kbit EEPROM standing in a line from 0 to 64000, because there are 8 bits to a byte. There are 32000 possible places in a 256 Kbit EEPROM and because 255 is the largest number you can encode in one byte you dumbass will need to send this address in two bytes. So, first send the Most Significant Byte (MSB) aka the first 8 bits. Then send the Least Significant Byte (LSB) the second 8 bits. The EEPROM uses an internal counter that automatically increases the memory location with each following data byte it receives. Once a memory address has been sent we can follow it with up to 64 bytes of data. The EEPROM assumes (rightly) that an address of 312 followed by 10 bytes will record byte 0 at address 312, byte 1 at address 313, byte 2 at address 314, and so on.
 
# Most EEPROM devices have something called a "page write buffer" which allows you to write multiple bytes at a time the same way you would a single byte
 

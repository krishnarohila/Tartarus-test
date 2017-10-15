# Tartarus-test

1. Install latest version of Raspbian on Raspberry pi. The OS can be downloaded from the following [link](https://www.raspberrypi.org/downloads/raspbian/) .
2. Install swi-prolog on the system(as root user) using the command:<br>```% sudo apt-get install swi-prolog```
3. Download/Copy the WiringPi-Prolog tar file([provided here](https://drive.google.com/open?id=0B5fn-iVXebaTOFFPUUNtdUxTdXM)) onto the Raspberry pi.
4. Unzip the WiringPi-Prolog zip file using the command:<br>```$ unzip <file_name>```
5. Check the swi-prolog installation directory. Generally the location is ‘/usr/lib/swi-prolog’. To check otherwise use the following commands:
<br>```$ swipl```
<br>```?- file_search_path(swi, X).			//returns installation directory.```
6. Copy the wipi folder from the unzipped folder(step 4) to the folder returned in step 5.
7. Get out of superuser if still in it.
8. Go to your working directory(folder where you will be working with your project files).
9. Copy the ‘platform_pi.pl’([provided here](https://drive.google.com/open?id=0B5fn-iVXebaTR3hnYnpLc3RoRTQ)) file in this directory.
10. Now start prolog with sudo permission(very important):
<br>```$ sudo swipl```
11. Consult the `platform_pi.pl` using:
<br>```?- consult('platform_pi.pl').``` 
      <br>This will load all of the Tartarus predicates.
12. Execute the command:
<br>```?- start_peripherals.```
       <br>This will start the peripheral Interface. Make sure no errors occur during this step.
13. Now the peripheral interface is ready, and you can use WiringPi Prolog predicates to control the GPIO pins.
## GPIO pin mapping for WiringPi
![alt text]()
## Heading
# General Purpose Input Output
1. Set the mode of a pin to input or output using the pinMode command:
      <br>Syntax: pinMode(pin,mode)
      * pin: GPIO pin number according to WiringPi.
      * mode: INPUT(0) or OUTPUT(1) mode.
2. Use digitalWrite command to write a value to the particular pin.
      <br>Syntax: digitalWrite(pin,value)
      * pin: GPIO pin number according to WiringPi.
      * value: set value HIGH(1) or LOW(0) for the pin.
3. Use digitalRead command to read the value that a particular pin is set to
      <br>Syntax: digitalRead(pin,X)
      * pin: GPIO pin number according to WiringPi.
      * X: variable in which the response of the command is stored.
<align = "left"><br><b>Example for LED:</b></align>
      1. Connect positive of led to GPIO pin 1(see WiringPi pin mapping) along with a resistance in series.
      2. Connect negative of led to GPIO pin 0(see WiringPi pin mapping).
      3. Write the following code to light up the LED.
            <br>```?- pinMode(0,0).```                --set pinmode of pin 0 to 0 for output.
            <br>```?- pinMode(1,0).```                --set pinmode of pin 1 to 0 for output.
            <br>```?- digitalWrite(0,0).```           --set value of pin 0 to 0 for LOW/ground.
            <br>```?- digitalWrite(1,1).```           --set value of pin 1 to 1 for HIGH/(3.3v).
      4. This will light up the LED.
      5. To turn it off use the digitalWrite command to write value 0 to pin 1
# I2C
1. Connect the I2C device to the Raspberry pi.
2. Check if the device is connected properly using the command:
<br>```$ sudo i2cdetect -y 1```
      <br> It should show something like:
      ![alt text]()
3. The address of the I2C device that we interact with is the one that appears on the table in the above image.
4. The commands that can be used to interact with the I2C device are:
      * <b>wiringPiI2CSetup(addr,Fd): To setup a connection with the device.
            * Addr: The address of the device obtained in step 2. Example: 0x68 (refer image in step 2).
            * Fd: The value returned by the setup command for furthur referencing to the device.
      * wiringPiI2CWriteReg8(Fd,reg,val): To write a value in a particular register on the device.
            * Fd: The value of Fd obtained from the setup command.
            * reg: Address of the register to which the value is to be written.
            * val: The value to be written to the particular register (reg).
      * wiringPiI2CReadReg8(Fd,reg,Val): To read the output from a particular register on the device.
            * Fd: The value of Fd obtained from the setup command.
            * reg: Address of the register from which the value is to be read.
            * Val: The value stored in the register returned by the command.

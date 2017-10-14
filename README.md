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



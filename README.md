# Tartarus-test

1. Install latest version of Raspbian on Raspberry pi. The OS can be downloaded from the following link .
2. Install swi-prolog on the system(as root user) using the command:
		```% sudo apt-get install swi-prolog```
3. Download/Copy the WiringPi-Prolog tar file(provided) onto the Raspberry pi.
4. Unzip the WiringPi-Prolog zip file using the command:
		```$ unzip <file_name>```
5. Check the swi-prolog installation directory. Generally the location is ‘/usr/lib/swi-prolog’. To check otherwise use the following commands:
		```$ swipl
		?- file_search_path(swi, X).			//returns installation directory.```
6. Copy the wipi folder from the unzipped folder(step 4) to the folder returned in step 5.
7. Get out of superuser if still in it.
8. Go to your working directory(folder where you will be working with your project files).
9. Copy the ‘platform_pi.pl’ file in this directory.
10. Now start prolog with sud permission(very important):
		```$ sudo swipl```
11. Consult the `platform_pi.pl` using:
      ```consult('platform_pi.pl').``` 
      This will load all of the Tartarus predicates.
12. Execute the command:
       ```start_peripherals.```
       This will start the peripheral Interface. Make sure no errors occur during this step.
13. Now the peripheral interface is ready, and you can use WiringPi Prolog predicates to control the GPIO pins.



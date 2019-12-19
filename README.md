# PiSpec20_LED_stellarnet  
A Python interface for StellarNet spectrometers designed to provide the functions of a Spectronic 20 spectrophotometer including an LED light source
## Project Goals and Motivations  
The goal of this project was to replace the old Spec 20s in our teaching laboratories with equivalent functionality in modern equipment. Choices of hardware and software were driven largely by familiarity. The choice of the Raspberry Pi was to make an effectively disposable computer. I picked Python 3.x (works on Python 2.7 also) for simplicity in migrating to different hardware. What I created here is a simple frontend for the spectrometer suitable for use by relatively untrained undergraduate students.
## Project Audience  
The project was written to support undergraduate laboratories, so really this repository is for people looking for a frontend to run their spectrometer. However, the functionality of the project can readily be expanded to take advantage of the spectrometer features. This code takes care of collecting the spectra and controlling the light source, everything else is just manipulations in code. Simple changes in the code shift the interface from having lots of things chosen for you to needing to make lots of choices.
## PiSpec20_LED_stellarnet Requirements  
I wrote this on a Raspberry Pi 3b+. For Windows or Mac you will need to make small changes to the code to deal with OS peculiarities. You will need to possess a Stellarnet spectrometer.  The LED requires building a small circuit to allow pulse width modulation of the LED for brightness control.  The schematic is below.  I built this on a Pi-topPROTO board which made it even easier.  
![schematic of PWM circuit for Raspberry Pi](https://github.com/acpo/PiSpec20_LED_stellarnet/blob/master/LEDCIRCUIT.png)
## Libraries  
- pyusb 1.0.0a3  (Linux example:  sudo pip3 install pyusb==1.0.0a3)  this is version specific
- screen (if you want to hide the background processes)  
- numpy  
- python-matplotlib  
- pigpio
- stuff usually automatically included in python
  - json  
  - python-requests  
  - python-flask  
  - python-virtualenv  (if you want to run this in a virtual environment)
  - Tkinter  
## Files to install  
- 99-local.rules  needs to be copied to '/etc/udev/rules.d/' or updated to include rules for StellarNet devices.  Otherwise 
you would need to run as root to get USB access.
- the rest of the files in PiSpec20_stellarnet should go into the same directory
- Issue `sudo chmod -x spectroweb.py` in the project directory if on a Linux system 
- on a Windows system you will need the free 'SWDrivers.zip' or 'SWDriver64.exe' from https://www.stellarnet.us/stellarnet-downloads  instead of the driver included in this package  
- on Raspberry Pi remember to start the PWM daemon `sudo pigpiod`  
- use the 'run_hidden' bash script to start the project without showing the command line.  From the command line issue `sudo chmod +x run_hidden` to make the bash script executable. On Windows a batch file would substitute the bash script.  
## Other Hardware  
- a USB connected StellarNet spectrometer
- a PWM circuit and LED.  The easiest way to do this would be on a Raspberry Pi since it has PWM pins ready to use.  Other prototyping platfoms (Arduino, etc.) could be adapted easily.  From a 'standard' PC, a PWM circuit can be attached by USB (Yocto, etc.).  An acceptable LED for "white light" illumination can cost as little as $2.00.  
## Supported Devices  
### Directly tested 
| Manufacturer  | Spectrometer  | Works ?       |  
| ------------- | ------------- | ------------- |  
| Ocean Insight | HR 4000       |     yes       |  
| Ocean Insight | HR 2000 plus  |     yes       |  
| Ocean Insight | USB 2000      |     yes       |  

### Should work (supported by device libraries)  

## How to Help  
I don't write in Python for a living, nor particularly do a lot of programming. And it shows in the code.  
If you wish to contribute please contact me.
## License
Apache License 2.0. A Stellarnet module is included under the Apache License 2.0, so the whole thing is, too.

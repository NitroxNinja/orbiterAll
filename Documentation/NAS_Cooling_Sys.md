## Intro

A NAS or Network Attached Storage is a kind of thing I have at my house for an extrananeous storage for files if ya' know what I mean. This paired along with a remote access system can possible help us store a large amount of files. 

There are several parts to the system. Firstly, there is a Raspberry Pi 4, and then there is a sort of hat that is attached to it that has 4 solid state drives (Vulcan Z SSD) attached to it.
There is also an Arduino Uno R3 for fan control of the system, and an ESP32 for I2C/WiFi stuff going on or something. 

One of the goals of this project is to create an overly-effective cooling system to bring down the 60 degrees celcius worth of heat down to like 25-30 degrees for a standard operating temperature. 

THE PROBLEM IS the heat sync and the PCB "hat" restricts our cooling space significantly, 

## Testing 

So for a proof of concept, we ran the NAS as is, without any cooling systems, and found out after about 2 minutes of running it got to a temperature of 60 degrees C. 
For reference, normally you do not want your PCB to melt b/c it will result in reduced performance, long-term damage and such.

What I did next was mind blowing. I just got a fan, and then I pointed it at the NAS. It reduced temperatures to 30 degrees C, and that was with a bad angle on the fan. I believe with adequate cooling and an efficient heat exchanging process we can get the number even cooler, but we do not know how much. I do not know what the temperature reduction/fanspeed/airflow is proportional to, but it proportional to something, and we can do this project to understand that. 

I also wanted to test the natural CFM of a fan at different rates, and while I didn't have a pitot tube, I can alternatively CAD up the blades, imaginary spin it at a certain RPM of which I can approximate, and then run it all through CFD. 
This is b/c I wanted to add a sort of venturi effect to the cooling system since the heat sync is in a restricted place. But b/c we are pressuring this zone a lot, I think there should be a way for this air to pass by the system very quickly. We know that this compressed air will get hot, and then must be passed up through the system. So there is an another fan that is on top of the whole NAS which draws the hot, less dense air (in theory). 

## Softwares and Electronics 

This features 
- ESP32
- Ardunio Uno R3
- Raspberry Pi 4
- A Raspberry Pi 4 hat for the 4 Vulcan SSDs
- 4 Vulcan Z SSDs

ESP32 boards offer a lot of capabilities that allow this NAS to work. I am unsure how to program it, but I'll learn anyways. Embedded is cool. 

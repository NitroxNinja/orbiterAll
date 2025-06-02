# Intro 

NOVA Autonomous Car is a open-source research project for UTD students to make a fully autonomous car. (led by Dr. Justin Ruths, mechanical engineering professor here) 

### Read the docs here: https://nova-utd.github.io/navigator/

## Hardware Dev  

So at first I started out by 3D printing some cameras, and then getting it parametricized and stiched into an image so that our developers can do some cool stuff with it. 
Later, I want to improve the encoder mount that is currently being used to measure the rotation(s) of the steering wheel, since it is cantilevered and it is pretty jank. It looks cool but it isn't fully thought out, and I wanted to see if I could improve it. There is a lot of play between the pinion and the other gear for the readings, so let's see how I can improve it. 

I then started to CAD out some other things such as a raspberry pi holder and cleaned up some of the wires near the On Logic Computer (we refer to this as the OBC, or onboard computer). This sort of puts into place the CAN (controller area network), where there are various subcomputers and embedded things within the car that we use for a variety of sensors and systems on the car. This raspberry pi holder would later evolve into the NAS cooler I had made (you can read NAS_Cooling_Sys.md in this documentation folder). 

![image](https://github.com/user-attachments/assets/1e4b522d-62c4-4093-ba46-a8ae845c88d7)

I then started getting into localization and odometry some more. Essentially what it is, is just giving a physical non-sentient being eyeballs and teaching how to see. The technical definition of localization is "a method to identify a robot's or (autonomous) car's location relative to the environment in a specific manner". We used a method from the "Photogrammetry & Robotics Bonn" (from the University of Bonn) to localize ourselves with their SLAM-KISS-ICP or "Simultaneous Localization and Mapping Keeping-It-Simple-Stupid Iterative-Closest-Point".

Essentially, we are permitted the use of just a LiDAR, since they often have proven effective with little noise for localization, and keeps things simple for developers like us. We use information from the LiDAR to understand the environment by taking in multiple images of the environment and sort of stitching that together, as the car goes on and develops an understanding of "how it's moving" through the environment. 

However, when configuring with it we realized we had issues with updating the images to our small computer (NVIDIA AGX Orin), as it was supposed to upload at a theoretical 15 Hz, however it was doing less than 1 Hz, lol. So we not only needed to make the camera mounts better, but also improve the hardware or improve the code that is used to process all that data. It was also drifting somehow, so perhaps we put in the wrong constants, but we will try to get something to work eventually. 

![image](https://github.com/user-attachments/assets/b4d89711-5a3e-422b-a740-eb59b4545703)

## Newer Developments and Ambitions 

The bottleneck in development as in right now comes with localization systems. Previously we were using SLAM KISS-ICP, however this can be pretty ineffective with the vehicle is doing fast movements or sudden turns... well which all cars kind of do on a daily basis. This is b/c SLAM KISS-ICP purely relies on LiDAR readings (which the Ouster 128-channel LiDAR provides around 10 Hz or 10 frames of point clouds a second). This leaves a lot of room for interpolation, which is technically a bad thing. Although LiDAR point clouds are extremly accurate of themselves in terms of capturing the environment, it takes a lot of computational power from the computer. I'd also like to briefly shout out to Mr. Kevin Ge, a fellow student at UTD who had partially inspired me to take on this task. He did most of the work for SLAM-KISS-ICP and now it's time for me to take it on. 

One article I stumbled across evolves SLAM KISS-ICP and combines it with the usage of an 6-axis IMU (inertial measurement unit, x,y,z,roll, yaw, pitch). This method is called LIO-EKF (LiDAR Inertial Odometry
using Extended Kalman Filter). The advantage of using a IMU comes with having a higher frame rate of readings (think more than 1000Hz) so you can measure how far you went forward, how much you turned, etc. 

The problem comes with that using an IMU alone leaves localization prone to a lot of noise, or misrepresented readings from the environment. But if you have a LiDAR to sort of validate where you are, you can update the usage of a IMU per every point cloud generated. Thus, the interpolation of the various spots the car may have been is made a little more accurate, limiting drift and such. This is the part of what an "extended kalman filter" is, which takes a variety of sensors inputs and intreprets it to give a more accurate number/results for the computer. 

![image](https://github.com/user-attachments/assets/59ad359e-9392-4b84-ac53-b30b067497e6)

(credit goes to Yibin Wu and et al.)


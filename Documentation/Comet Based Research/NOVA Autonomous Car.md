# Intro 

NOVA Autonomous Car is a open-source research project for UTD students to make a fully autonomous car. (led by Dr. Justin Ruths, mechanical engineering professor here) 

### Read the docs here: https://nova-utd.github.io/navigator/

## Hardware Things  

So at first I started out by 3D printing some cameras, and then getting it parametricized and stiched into an image so that our developers can do some cool stuff with it. 
Later, I want to improve the encoder mount that is currently being used to measure the rotation(s) of the steering wheel, since it is cantilevered and it is pretty jank. It looks cool but it isn't fully thought out, and I wanted to see if I could improve it. There is a lot of play between the pinion and the other gear for the readings, so let's see how I can improve it. 

I then started to CAD out some other things such as a raspberry pi holder and cleaned up some of the wires near the On Logic Computer (we refer to this as the OBC, or onboard computer). This sort of puts into place the CAN (controller area network), where there are various subcomputers and embedded things within the car that we use for a variety of sensors and systems on the car. This raspberry pi holder would later evolve into the NAS cooler I had made (you can read `NAS_Cooling_Sys.md` in this documentation folder). 

You're essentially doing the dirty work, and then you'll find you may or may not like using a wrench or screwdriver when you do this. I see for other fellow engineering students they don't seem to be well acquainted with using tools, even though I think it's really intuitive and repeatable. 

When you are doing CAD for some small 3D prints or creating a new steering rack, you can have a lot of creative input into the design itself, but it'll feel boring at first, but after working with some of the electrical and software bits, you get to learn a little bit more about the car. Most of the making of this car will feel compartmentalized for no reason, but it doesn't have to be that way. Just ask questions and see how it's assembled, and you'll most likely gain an intuitive sense of how things work around the car, since there's a lot of "moving" parts. The best way to learn is to do stuff for the car. You'll know your passionate about autonomous cars when you start doing more and more as time progresses. 

![image](https://github.com/user-attachments/assets/1e4b522d-62c4-4093-ba46-a8ae845c88d7)

## Electrical Things 

We use a 48V battery to power all the systems in our car, while we do need to step it down for 12V for most computerized components, the high power and performance we get from a 48V is cool, albeit dangerous for a bunch of people whom don't know what they are doing. I learned how to use a NVIDIA AGX Orin and paired it along with a ZedX camera, this will hopefully be a part of the CAN (controller area network). I also made a SLA battery protection thing for all the embedded systems and voltage step down things on the 3rd scale car (we are building a mini car). You may hear a lot of the NVIDIA Jetson terms thrown around, and I think it's a very cool computer used for mobile robotics. Super intense and well designed for low level high performance applications. 

We use a solid state 128-channel Ouster LiDAR. No it does not spin like the ones on Waymo, but it basically serves the same purpose, just a little more inaccurate, but also slightly more cheaper. 

## Software Things

The NOVA car uses a lot of software and things. We primarily work in a Linux based environment for testing and development. You should perhaps familiarize yourself with it. We also utilize Python as our main language unfortunately, although familarity in C++ will be helpful. Having Python for your programming environment will take a large computational toll on your compiler in my experience. I am unsure if you can edit in real time and make sure the bridge to CARLA can also work instantaneously but honestly that's a nerdy CS question. 

I then started getting into localization and odometry some more. Essentially what it is, is just giving a physical non-sentient being eyeballs and teaching how to see. The technical definition of localization is "a method to identify a robot's or (autonomous) car's location relative to the environment in a specific manner". We used a method from the "Photogrammetry & Robotics Bonn" (from the University of Bonn) to localize ourselves with their SLAM-KISS-ICP or "Simultaneous Localization and Mapping Keeping-It-Simple-Stupid Iterative-Closest-Point". However this method proved to have a lot of drift, so we are in the process of switching to LIO-EKF, which combines the readings of the LiDAR and the IMU so we can get a good reference of where we are. 

Essentially, we are permitted the use of just a LiDAR, since they often have proven effective with little noise for localization, and keeps things simple for developers like us. We use information from the LiDAR to understand the environment by taking in multiple images of the environment and sort of stitching that together, as the car goes on and develops an understanding of "how it's moving" through the environment. 
- I also want to mention the necessity of point cloud sampling. LiDARs scan the room or environment (with light), and provide a set of points representing where things are, such as a wall, a stop sign, or even a person. However modern LiDARs also read a lot of information, and stores them in large csv files, but the car can't always use all that information. So what we have to do is process it (pointcloud desampling/upsampling), and get useful points from the point cloud.
- As you may guess, the autonomous car requires a hefty amount of CS, but I also want to make the connection to mechanical engineering stuff. A car is a mechanical thing that moves in space, we use what knowledge we get from the computer world to control a physical object of metal, rubber, and PCBs. An ok understanding of kinematics and dynamics could be helpful I guess, but overall one message I want to push out is that just because you aren't a programmer doesn't mean you can't work on autonomous cars. It's a fun game out here.

However, when configuring with it we realized we had issues with updating the images to our small computer (NVIDIA AGX Orin), as it was supposed to upload at a theoretical 15 Hz, however it was doing less than 1 Hz, lol. So we not only needed to make the camera mounts better, but also improve the hardware or improve the code that is used to process all that data. It was also drifting somehow, so perhaps we put in the wrong constants, but we will try to get something to work eventually. 

![image](https://github.com/user-attachments/assets/b4d89711-5a3e-422b-a740-eb59b4545703)

## Newer Developments and Ambitions 

The bottleneck in development as in right now comes with localization systems. Previously we were using SLAM KISS-ICP, however this can be pretty ineffective with the vehicle is doing fast movements or sudden turns... well which all cars kind of do on a daily basis. This is b/c SLAM KISS-ICP purely relies on LiDAR readings (which the Ouster 128-channel LiDAR provides around 10 Hz or 10 frames of point clouds a second). This leaves a lot of room for interpolation, which is technically a bad thing. I also want to mention the idea of "map-closures", where when a car arrives at the same spot it already hit, it will localize good or something. Honestly have no idea how it works I'll get back to you shortly. 

Although LiDAR point clouds are extremly accurate of themselves in terms of capturing the environment, it takes a lot of computational power from the computer. I'd also like to briefly shout out to Mr. Kevin Ge, a fellow student at UTD who had partially inspired me to take on this task. He did most of the work for SLAM-KISS-ICP and now it's time for me to take it on. 

Then we have path planning which is a whole 'nother fiasco of it's own. Dynamic occupancy grids, cost function following (NetworkX provides an algorithm to follow the cost function)

One article I stumbled across evolves SLAM KISS-ICP and combines it with the usage of an 6-axis IMU (inertial measurement unit, x,y,z,roll, yaw, pitch). This method is called LIO-EKF (LiDAR Inertial Odometry
using Extended Kalman Filter). The advantage of using a IMU comes with having a higher frame rate of readings (think more than 1000Hz) so you can measure how far you went forward, how much you turned, etc.

For more resoures on what a Kalman filter is, it essentially takes noisy readings from a multiple sensors around the car that read position, heading, etc., and estimates the true value by linearizing these readings, knowing that the system is dynamic. An extended kalman filter is just that but on steroids, knowing that the dynamic system is nonlinear, and it has to do a whole extra math of trying to linearize a nonlinear system.  

The problem comes with that using an IMU alone leaves localization prone to a lot of noise, or misrepresented readings from the environment. But if you have a LiDAR to sort of validate where you are, you can update the usage of a IMU per every point cloud generated. Thus, the interpolation of the various spots the car may have been is made a little more accurate, limiting drift and such. This is the part of what an "extended kalman filter" is, which takes a variety of sensors inputs and intreprets it to give a more accurate number/results for the computer. 

![image](https://github.com/user-attachments/assets/59ad359e-9392-4b84-ac53-b30b067497e6)

(credit goes to Yibin Wu and et al.)


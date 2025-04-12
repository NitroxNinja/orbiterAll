# Intro 

NOVA Autonomous Car is a open-source research project for UTD students to make a fully autonomous car. 

So at first I started out by 3D printing some cameras, and then getting it parametricized and stiched into an image so that our developers can do some cool stuff with it. 

![image](https://github.com/user-attachments/assets/1e4b522d-62c4-4093-ba46-a8ae845c88d7)

I then started getting into localization and odometry some more. Essentially what it is, is just giving a physical non-sentient being eyeballs and teaching how to see. The technical definition of localization is "a method to identify a robot's or (autonomous) car's location relative to the environment in a specific manner". We used a method from the "Photogrammetry & Robotics Bonn" (from the University of Bonn) to localize ourselves with their SLAM-KISS-ICP or "Simultaneous Localization and Mapping Keeping-It-Simple-Stupid Iterative-Closest-Point".

Essentially, we are permitted the use of just a LiDAR, since they often have proven effective with little noise for localization, and keeps things simple for developers like us. We use information from the LiDAR to understand the environment by taking in multiple images of the environment and sort of stitching that together, as the car goes on and develops an understanding of "how it's moving" through the environment. 

However, when configuring with it we realized we had issues with updating the images to our small computer (NVIDIA AGX Orin), as it was supposed to upload at a theoretical 15 Hz, however it was doing less than 1 Hz, lol. So we not only needed to make the camera mounts better, but also improve the hardware or improve the code that is used to process all that data. It was also drifting somehow, so perhaps we put in the wrong constants, but we will try to get something to work eventually. 

![image](https://github.com/user-attachments/assets/b4d89711-5a3e-422b-a740-eb59b4545703)

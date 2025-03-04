# Intro 

The development of educational competition robots started with Dr.Woodie Flowers at MIT, where he made a class which later evolved to what we know as the "FIRST Robotics Competition" or FRC for short, in 1992. Later, other competitions like VEX Robotics Competition (VRC) started. 
As a result, generations of high schoolers have made robots that would compete against each other in a game that would be designed every year- each game featuring some unique challenges to score more points than the opposing alliance to win. In my yapping session, I will talk about my experiences in VRC, since I have the most expertise on that.

My writing serves to for a newer person to get a general basis on what a robot designed-to-win may look like and will glance through technical details and/or validation mathematics that often is very difficult to generalize for a singular team. - By me. 

## The Competition 

Every single year, the game design committee reveals a new game every year, which often combines multiple elements of game objects, rules, and other nit-picky details. Matches are often played in a 2v2 format, where each set of 2 teams is called an alliance, red versus blue. Whoever scores the most points by placing the game objects in the right place, achieving certain tasks or whatnot, wins the match. There is a 15 second autonomous period, where the robot moves by itself and the 1 minute and 45 second driver/tele-operated period where the person on the controller takes control. 

![image](https://github.com/user-attachments/assets/f4164185-f21d-4300-ad47-02d37942f89d)

_Figure 1: 5408R's Turning Point Robot in the field. The game is played by flipping colored flags to your color by shooting balls. You can also score discs on poles facing the correct color, or flip them on the ground. Lastly you can climb the platform for bonus points, if you can stay on it. 
_
## Basic Rules 

There are a unique set of rules every single robot has to follow in order to compete in a competition. Here are some examples: 
- 18" x 18" x 18" size limit
- 88 watt motor limit (8 11W VEX motors)
- Sheet of plastic (polycarb, delrin, etc.) only to be from 24" x 12" sheet
- No welding, no mods to electronics
- Bunch of other stuff

## Subsystems and their Applications 

In competitive robotics, there are things we call subsystems that make up portions of a whole robot that contribute to it's function there are 
- Drivetrains. Some propulsion or wheeled-based movement to go around the field
- Intake. You need to be able to pick up random game objects in the field, so you can hopefully score points
- Scoring mechanism. Could be a catapult that shoots the objects or it could even be a lift and claw mechanism, depends on the context of the game.
- Extraneous mechanism(s). Some games may require to have a lifting mechanism, or like a unique "end-game" piece to score points, this often is known to be the "innovative factor" to robots, and varies wildly across games. 

![image](https://github.com/user-attachments/assets/3398470d-250a-4572-a8e4-f320209dc911)

_Figure 2: 5408D's Spin Up Robot, with all the mentioned subsystems. 
_
## Team Roles 

Obiviously, you'd need someone to be able to understand how all these subsystems come as a whole, but you'd imagine if a robot were to perform all the basic scoring capabilities well, it is enough for a winning robot. You'd also need to delegate or absorb some roles of being an mechanical dude, a programmer dude, a driver dude, and even a documentation dude. There may also be some marketing person/budget but we don't count those.
- **Mechanical dude**. This person is in charge of construction of the robot. They could use CAD, or if you're a pro, you use your brain to develop physical systems of the robot. They will use the VEX metal, motors, gears, and other gimmicks but also could custom design parts using polycarbonate or lexan.
- **Programmer dude**. This person is the most nerdiest, and will often use C++ and a thing called VEXCode or PROS (or the Purdue Robotics Operating System). They will be in charge of programming basic drive/controller functions of the robot, and how the robot will interact with the field through driver/autonomous periods. As you get more accustomed to programming you'd dive into things like GUI, PID, odometry, motion profiling, which involve a little bit more math and thinking.
- **Driver dude**. This person gets to have the most fun, but also takes up the brunt of responsibility to whatever happens to the robot (during the driver control period). They will often have a drive coach (usually one of their own teammates) help him guide on the next decision. They must get very well versed with their robot's dynamics through driving/behaviors.
- **Documentation dude**. This person is optional, but if you would like to win judged awards like Excellence or Design, this role is it. People can often look back to previous designs and "reiterate" but let's be honest the agile manifesto is kind of a bothersome task in the context of high school robotics. The best engineering design" is often sold through this person, and they must not only learn the technicalities of the robot but must explain it to a person who may know nothing about robots. They must lead through the interviews and learn how to be really good at it.
- **Marketing and/or Accounting dude**. This person is in charge of getting sponsors, making the team look cool on social media, and managing budget of the whole team. Generally this one is pretty easy, but you can learn some neat stuff like editing, or feasibility kinds of things. 

![image](https://github.com/user-attachments/assets/c416e047-aa99-4cf7-98ac-ca6cff74513f)

_Figure 3: 365X Invictus was a successful team. Credit: https://x.com/invictus365x 
_
## Building the actual robot: Drivetrain 

Yes, yes, yes, you've probably been bored of all the basic stuff but now it's time to get interesting. We'll start off with thinking how the robot should be built in accordance of the game. 

Firstly, we'll go over drivetrains. Most people build it with omni-wheels, c-channels, bearings, gears/sprockets, and motors. There's a great video by [Kepler Electronics](https://youtu.be/VfuA2EqaIso?si=oESpQ01EnPBtNxo1) explaining the types of drives, but teams may consider doing modifications to the kinds of drives they have. 

![image](https://github.com/user-attachments/assets/13af8570-80ad-4f3c-a0e0-72eac3fc75f6)

_Figure 4: 5408D's Over Under drivetrain that utilized the 600 RPM cartridge motors to 4:3 external gear ratio to make a 450 RPM 3.25" omniwheel drive. Extremely fast and evasive drivetrain.  
_
Typically you want to have a **high power and torque-y** drive to be able to manuver and perhaps encounter defensive shoving from the other alliance. You may want to consider your driver's and programming abilities as well when choosing what kind of drive you want to run. Your drive power and torque is generally determined by what kind of gear ratios you are running with your motors, and the size of wheel you're using. For starters, just build a basic tank drive with omniwheels- and experiment with different types of gearing and how you will link of the structure. In recent years it has become more acceptable to build high speed drives capable of going 6.43 ft/s. Many teams will run **a 450 RPM on 3.25" drive** like the picture above. There are options of 3.25" on 360RPM or 4.25" on 257 RPM or even 2.75" on 600RPM. Generally picking smaller wheels is prevalent due to less weight, but that comes at the cost of reducing tractive force, but in VEX it's almost negligble. 

You also want to take into consideration chassis design, and how structure you need it to be. Many new teams struggle on knowing what's a "durable" chassis, or they may sometimes overbuild it and take on extra weight they don't need or structures that ruin the packaging (the way how subsystems fit on the robot). The best way to know you've built it strong enough is to do a "torsion-test". Pick up your sandwiched drivetrain with both hands and twist in opposite directions. If it doesn't twist too much relative to the amount of force you're putting in (like if it bends less than 15-20 degrees) you're good. If not you may need to reconsider how you place your chassis bars across, or how much support you need. 

If you're robot needs to be able to climb an object, consider using sleds (curvy bent pieces of plastic/metal that glide up bumps), using bigger wheels, or moving any obstruction in the robot's underbelly. Consider how the robot will make traction with the ground/bump and you can decide how to layout a drive train. You could go low with benefits of better handling and less tippy-ness, at the cost of not being able to climb a 1" bump. Or you could go high with benefits of being to climb over most obstacles, at the cost of a less controllable/heavier driving dynamic. 

![image](https://github.com/user-attachments/assets/b5d502be-2902-4e64-b4d7-1b1443bb39c1)

_Figure 5: 8059A's Turning Point robot was a tanky-high robot that was hard to shake, but manuverable enough to cause a ruckus in the Dome. 
_
![image](https://github.com/user-attachments/assets/4c745965-9a7f-46a8-bd20-4bddff976b45)

_Figure 6: 5408D's Spin Up robot was basically touching the ground, and was incredibly fast with a 2.75" 600RPM drive, but could not climb over a 1 inch ledge. Low life or no life.
_

Past this I may get nit-picky if you leave the flange in or out, in a sandwiched drive train (where wheels are "sandwiched" in between 2 c-channels). Some people may also ask why you made your drive base 25 holes wide or 30 holes wide, and you could justify it with "reduced weight" or a "more nimble/smaller" robot. 

You must learn how to mess with gear ratios and your structure placement, keeping things square, and such to have a "successful" drive train.




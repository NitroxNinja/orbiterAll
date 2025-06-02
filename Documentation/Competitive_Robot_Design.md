# Intro 

The development of educational competition robots started with Dr.Woodie Flowers at MIT, where he made a class which later evolved to what we know as the "FIRST Robotics Competition" or FRC for short, in 1992. Later, other competitions like VEX Robotics Competition (VRC) started. 
As a result, generations of high schoolers have made robots that would compete against each other in a game that would be designed every year- each game featuring some unique challenges to score more points than the opposing alliance to win. In my yapping session, I will talk about my experiences in VRC, since I have the most expertise on that.

My writing serves to for a newer person to get a general basis on what a robot designed-to-win may look like and will glance through technical details and/or validation mathematics that often is very difficult to generalize for a singular team. - By me. 

## The Competition 

Every single year, the game design committee reveals a new game every year, which often combines multiple elements of game objects, rules, and other nit-picky details. Matches are often played in a 2v2 format, where each set of 2 teams is called an alliance, red versus blue. Whoever scores the most points by placing the game objects in the right place, achieving certain tasks or whatnot, wins the match. There is a 15 second autonomous period, where the robot moves by itself and the 1 minute and 45 second driver/tele-operated period where the person on the controller takes control. 

![image](https://github.com/user-attachments/assets/f4164185-f21d-4300-ad47-02d37942f89d)

*Figure 1: 5408R's Turning Point Robot in the field. The game is played by flipping colored flags to your color by shooting balls. You can also score discs on poles facing the correct color, or flip them on the ground. Lastly you can climb the platform for bonus points, if you can stay on it.*

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

*Figure 2: 5408D's Spin Up Robot, with all the mentioned subsystems.*
  
## Team Roles 

Obiviously, you'd need someone to be able to understand how all these subsystems come as a whole, but you'd imagine if a robot were to perform all the basic scoring capabilities well, it is enough for a winning robot. You'd also need to delegate or absorb some roles of being an mechanical dude, a programmer dude, a driver dude, and even a documentation dude. There may also be some marketing person/budget but we don't count those.
- **Mechanical dude**. This person is in charge of construction of the robot. They could use CAD, or if you're a pro, you use your brain to develop physical systems of the robot. They will use the VEX metal, motors, gears, and other gimmicks but also could custom design parts using polycarbonate or lexan.
- **Programmer dude**. This person is the most nerdiest, and will often use C++ and a thing called VEXCode or PROS (or the Purdue Robotics Operating System). They will be in charge of programming basic drive/controller functions of the robot, and how the robot will interact with the field through driver/autonomous periods. As you get more accustomed to programming you'd dive into things like GUI, PID, odometry, motion profiling, which involve a little bit more math and thinking.
- **Driver dude**. This person gets to have the most fun, but also takes up the brunt of responsibility to whatever happens to the robot (during the driver control period). They will often have a drive coach (usually one of their own teammates) help him guide on the next decision. They must get very well versed with their robot's dynamics through driving/behaviors.
- **Documentation dude**. This person is optional, but if you would like to win judged awards like Excellence or Design, this role is it. People can often look back to previous designs and "reiterate" but let's be honest the agile manifesto is kind of a bothersome task in the context of high school robotics. The best engineering design" is often sold through this person, and they must not only learn the technicalities of the robot but must explain it to a person who may know nothing about robots. They must lead through the interviews and learn how to be really good at it.
- **Marketing and/or Accounting dude**. This person is in charge of getting sponsors, making the team look cool on social media, and managing budget of the whole team. Generally this one is pretty easy, but you can learn some neat stuff like editing, or feasibility kinds of things. This person is often the mentor or coach of your team.

Even with these roles this doesn't mean one person is only allowed to do one thing. You can take up multiple roles and learn everything there is to robotics. Most teams go on seperating these tasks, becoming masters of one, but me personally I sort of took on all these roles on my team (since we didn't have that much people), and still ended arguably successful. 

![image](https://github.com/user-attachments/assets/c416e047-aa99-4cf7-98ac-ca6cff74513f)

*Figure 3: 365X Invictus was a successful team. (team in the middle with blue) Credit: https://x.com/invictus365x*

## Building the actual robot: Drivetrain 

Yes, yes, yes, you've probably been bored of all the basic stuff but now it's time to get interesting. We'll start off with thinking how the robot should be built in accordance of the game. 

Firstly, we'll go over drivetrains. Most people build it with omni-wheels, c-channels, bearings, gears/sprockets, and motors. There's a great video by [Kepler Electronics](https://youtu.be/VfuA2EqaIso?si=oESpQ01EnPBtNxo1) explaining the types of drives, but teams may consider doing modifications to the kinds of drives they have. 

![image](https://github.com/user-attachments/assets/13af8570-80ad-4f3c-a0e0-72eac3fc75f6)

*Figure 4: 5408D's Over Under drivetrain that utilized the 600 RPM cartridge motors to 4:3 external gear ratio to make a 450 RPM 3.25" omniwheel drive. Extremely fast and evasive drivetrain. *

Typically you want to have a **high power and torque-y** drive to be able to manuver and perhaps encounter defensive shoving from the other alliance. You may want to consider your driver's and programming abilities as well when choosing what kind of drive you want to run. Your drive power and torque is generally determined by what kind of gear ratios you are running with your motors, and the size of wheel you're using. For starters, just build a basic tank drive with omniwheels- and experiment with different types of gearing and how you will link of the structure. In recent years it has become more acceptable to build high speed drives capable of going 6.43 ft/s. Many teams will run **a 450 RPM on 3.25" drive** like the picture above. There are options of 3.25" on 360RPM or 4.25" on 257 RPM or even 2.75" on 600RPM. Generally picking smaller wheels is prevalent due to less weight, but that comes at the cost of reducing tractive force, but in VEX it's almost negligble. 

You also want to take into consideration chassis design, and how structure you need it to be. Many new teams struggle on knowing what's a "durable" chassis, or they may sometimes overbuild it and take on extra weight they don't need or structures that ruin the packaging (the way how subsystems fit on the robot). The best way to know you've built it strong enough is to do a "torsion-test". Pick up your sandwiched drivetrain with both hands and twist in opposite directions. If it doesn't twist too much relative to the amount of force you're putting in (like if it bends less than 15-20 degrees) you're good. If not you may need to reconsider how you place your chassis bars across, or how much support you need. 

If you're robot needs to be able to climb an object, consider using sleds (curvy bent pieces of plastic/metal that glide up bumps), using bigger wheels, or moving any obstruction in the robot's underbelly. Consider how the robot will make traction with the ground/bump and you can decide how to layout a drive train. You could go low with benefits of better handling and less tippy-ness, at the cost of not being able to climb a 1" bump. Or you could go high with benefits of being to climb over most obstacles, at the cost of a less controllable/heavier driving dynamic. 

![image](https://github.com/user-attachments/assets/b5d502be-2902-4e64-b4d7-1b1443bb39c1)

*Figure 5: 8059A's Turning Point robot was a tanky-high robot that was hard to shake, but manuverable enough to cause a ruckus in the Dome.*

![image](https://github.com/user-attachments/assets/4c745965-9a7f-46a8-bd20-4bddff976b45)

*Figure 6: 5408D's Spin Up robot was basically touching the ground, and was incredibly fast with a 2.75" 600RPM drive, but could not climb over a 1 inch ledge. Low life or no life.*

Past this I may get nit-picky if you leave the flange in or out, in a sandwiched drive train (where wheels are "sandwiched" in between 2 c-channels). Some people may also ask why you made your drive base 25 holes wide or 30 holes wide, and you could justify it with "reduced weight" or a "more nimble/smaller" robot. Length is often questioned to, and understanding your wheel base, and how it may affect movement. This is incredibly helpful to know as a programmer who may be programming an odometry system and may need to understand how to model a chassis's movements based off the location of it's rotating wheels. Some teams may opt to have a convex or concave opening at the ends of their drives to fit extra mechanisms or pieces.

In Kepler's video, he also mentioned different kinds of wheels and setups, that are rather "fully-holonomic" meaning there is active power movement in all directions on the 2D plane. Of these there are meccanum wheels (kind of like omni wheels, but they are angled and if you rotate certain wheels they go sideways), and X-drive 

![image](https://github.com/user-attachments/assets/ed143060-d43b-440c-b802-8600d97f770f)

*Figure 7: 7K's Tower Takeover robot used meccanum wheels to go side to side to score in tight corners*

![image](https://github.com/user-attachments/assets/fd5aaec3-8fdf-42ff-bfbb-bdff2f17ff8b)

*Figure 8: 4253B's X-drive with odometry tracking wheels to go side to side*

You must learn how to mess with gear ratios and your structure placement, keeping things square, and such to have a "successful" drive train.

## Building the actual robot: Intake Mechanism(s)

Normally every game would demand the robot to intake some sort of object and use it to score points. For example in the 2019-2020 game, Tower Takeover, the game objects were cubes that you had to pick up and make very large stacks into corners of the field. In the 2018-2019 game required you to interact with 2 game objects, which were balls you could throw at red/blue flags and discs(or caps) you can flip over. There are even some games which involve mobile goals (or scoring places where you can put game objects on to score points), This most notably happened in "Round Up (2010-2011)", "In The Zone" (2017-2018), "Tipping Point" (2021-2022), and most recently in "High Stakes" (2024-2025). 

![image](https://github.com/user-attachments/assets/ba6a309e-4ef1-4ee6-b67f-d9ff98ef736e)

*Figure 9: 365X vs 5408A In The Zone Scrimmage. Involved picking up of yellow cones and stacking them on moveable scoring bases (mobile goals, or mogos)*

Typically an intake could look like a **claw**, a **giant claw**, or a **set of rollers**. It even can look like a **plunger** for a toilet as well, you just need to be able to design the intake for whatever game is happening. I highly suggest doing your own research on what kind of intake you should use depending on the game (try to watch video on what the "meta" does or what is most commonly built). 

## Building the actual robot: Attaching the Towers

Towers are structures that are built off the chassis that normally hold the main scoring mechanisms of the robot, or could be branched off into parts of the intake (if you're a pro builder you can minimize the amount of towers since they generally make the CoG higher up, and add weight). Normally when you add a tower, You can screw in one part of the c channel to a part that is horizontally supporting the drive base (I'll add pics here). And then you would put a triangle support, and then perhaps another horizontal support to another tower. 

You can also do some cool tricks with tower attachments, this can involve using standoffs to add another c channel across the small part of your sandwich'd drive chassis, using a 1x1 or a 90 degree gusset off the side to make the towers look flush and reduce the amount of points of attachment (thus reducing weight and perhaps increasing the serviceability of the tower). 

## Serviceability

This topic isn't really talked about in competition, but eventually some day your parts will fail and break. Thus you need to be able to replace some parts when you need to. It is very common for parts to get loose such as the motors or attachments that are screwed in via nuts. It's important to understand what may cause these things to get loose, and this is mostly due to mechanical vibrations, usually from flywheels, moving back and forth, being pushed from another robot, and a whole lotta other factors. 

It has become commonplace to build chassis with 5 hole wide gaps for the sandwich part, and instead utilize a screwjoint. I argue that this boundary is way too thin most of the time for servicability, and this often requires taking out your wheels then tightening the motors on the drive base. It is much simplier to just have a 6 hole wide sandwich and then use like an axle perhaps, but this comes at the consequence of structure and perhaps performance (lower friction, less slop, you name it.)

Another important part to servicability, comes to parts you should NOT be servicing the day of the competition. This could be a PTO or a flywheel. I highly recommend using loctite and making sure the motors and whatever c-channels are torqued down properly, and utilize nylocks! Of course you don't want to be using nylocks everywhere as they increase weight, which is why some parts I will use zipties to hold in bearings (which already have pre built teeth that hook onto the metal's holes), or some bits of lexan. They seem to keep up and they have never failed on me. I would not recommend using zipties to hold metal together though. 

If you're seriously advanced and you definitely do not want to service some parts such as a catapult arm, I suggest learning a little bit about stress strain curves and yield strength kind of stuff. Get into FEA perhaps to understand high stress high cycle loads. Make sure some parts are the correct factor of safety so they can withstand weeks of abuse before needing to be replaced. I one time ran with the same catapult arm for 2 months before it started to crack (even with boxing techniques).  

## Programming Developments 

This will be put into 2 subsections: starting to program your robot, and newer skills/techniques in programming that could set you apart. 

### i. Starting to program 
For starters, the programming language you will most likely start learning with to program robots is C++. Rarely do teams ever use Python, but there have been some moves to make Rust a more programmable language. All languages have their bonuses, features, and problems as well. But to be honest, it's gonna be hard to explain why there are debates, so just use C++ for now. Familiarize yourself with program structures, the Visual Studio Code IDE, files, header files, how to print things, if else statements, while loops, how to print "Hello World" b/c all those basic programming skills (which can be learned in about 2 weeks) will be helpful when you're actually coding. The real bulk of the problem for programming is just understanding the mathy part of it.

Your program often will need to achieve but are not limited to these 3 major tasks: calibration/prep, teleoperation, and the autonomous. 
You will use a software template usually provided by VEXcode or PROS (Purdue Robotics Operating System), which has all these formats built in. You just need to start programming the actual robot. So first you'll have to define your motors, typically using a keyword in header files known as "extern" which globalizes that variable so all files in your program.

You want to start off with learning how to program a motor to move in accordance with your controller. Since you already know what an if else statement is, follow your API's instructions on how to do the rest. Bam you learned how to control a motor w/ the press of a button. 

You'll then want to try to program your drive base. There are multiple ways to do this, but since there are 2 joysticks, the most common way is to use a method called "Tank Drive" where the right joystick controls the right side of the drive, and the left joystick controls the left side of the drive (forward and backward). To turn you just move your fingers in the opposite direction. This way of programming technically gives you the most control of your drive base, but requires some thinking, and takes up a lot of brain space in your driving, also you only have 2 thumbs, and sometimes you need to press multiple buttons at once. 

Then we can dive into "arcade drive" where one joystick controls forward and backward movement and then the other joystick controls left and right turning. This sort of partially segregates the thinking of movement and makes it more intuitive for some drivers if they played games as a child. 

Then now there is the ultimate driving technique which requires a lot of finger control, but once you master it, you can multitask like a dream! It's called "single-stick arcade drive" where you use only one joystick, and the forward and backward is controlled by your stick going up and down, and turning is controlled by your stick going left and right. If your drive base consists of only omniwheels, to drift, just move your stick to the whatever corner of the joystick which combines any of those to, let go to intiaite the drift, and then blip the throttle to keep on going. 

In driver control there also may need be some tasks that need to be done which involve several subsystems of the robot moving in unison/at once/consecutively, and this may need to be automated with a press of a button. Luckily, you can easily do that, and what that's called is called a "macro". You can also choose to program this if a extra complicated movement is required that can't normally be done by a driver. Heck some people even use their autonomous skills program into a driver macro b/c they are bad drivers(or their programming skills is just overpowered). You can just program the set of instructions in a function block and make sure you can run it in parallel with all the other tasks you may want to do. In Tower Takeover, I had a button where I would automate the speed of tray that stacked many cubes. It would go fast for a few rotations, go less fast on the next few rotations, go slow towards the last, and when it reached it's target, it would stop (so I could stack my cubes). 

Apply these same principles but to the autonomous function and you could tell your robot to follow instructions in autonomous, and you may struggle a lot for it. That's why you should read the next subsection. 

### ii. Newer Software Techniques
PID is often a heavily talked about topic for people well versed in programming for competition. In the 15 second autonomous periods, people must accurately control their robot to complete tasks, and doing that with DC servo motors should seem possible but often inaccurate and sloppy movements are common for starter programs. 

Programmers often need to understand a robot's precise location and heading (or what direction the robot is facing) in order to navigate the field. This is called odometry or localization. Since VEX fields are flat, and they are squares, team 5225A had a strategy for localization by using a thing called tracking wheels, which were "dead wheels" (wheels without motors) that had quadrature rotation encoders that gave the microcontroller feedback on how much each wheel spun. There were lateral (forward and backward) and horizontal (sideways) tracking wheels. This is often paired with an IMU to detect heading and turns, and you could possible implement an extended kalman filter (combining the readings from other sensors to get a more clear reading)

This sort of comes at the consequence of losing space on your drive base, excess weight, and difficult serviceability (if you don't make it quick swap-able). 

A increasingly more popular method of localization, called "Monte-Carlo-Localization", utilizes distance sensors to measure your distance from certain walls, and most notably an IMU. Using this method of localization assumes that you know the space/arena you're in (it's a square box, with game objects). Based off the readings from the distance sensor and what your heading is, it uses a baynesian assumption (normal distribution) of possibilities of where you most likely will be on the field at a given point. As the robot moves through the environment, it picks up more data from the distance sensor saying like "Oh I detected a change this way, so that means I'm going forward/backward/left/right" and etc. It essentially reads the field like a book and is able to accurately guess where it is.
IMAGINE you're teleported in your room, but then you were blindfolded. You might not know where immedieately you are, but as you walk around and feel what objects you hit (i.e. your bed, or your computer), you can sort of guess that "Oh I'm touching by bed top left corner of my bed b/c I put my pillow there". 

The next level up from Monte Carlo Localization is something called SLAM (Simultaneous Localization and Mapping), but with VEX's current hardware, and lack of advanced sensors such as LiDAR, it's gonna be practically impossible to pull it off, and you're better off just doing MCL, which works pretty great for VEX. If you do want to learn about SLAM, you can read my document from the NOVA Autonomous Car document I wrote! Or use google. 

Overall, I highly suggest using something like EZ-Template or LemLib. Those 2 libraries provide a great chassis for you to start programming, and practically give you all the math to do what you need to do. However, it doesn't give you an end-all-be-all answer to programming and troubleshooting issues in VEX. I felt pretty proud for making my own PID code for VEX, but it is vastly outshown by the opensource development that LemLib users have b/c they have built in odometry, purepursuit, moveto/pose functions, and much more features which makes your routine more competitive. You still need to individualize your code to your own robot, and still need to understand vehicle dynamics of the robot, which is sort of another complicated issue in itself. 

## Design Methodology: The Toyota Way (5408) 

I normally build with a specific style that could not be mistaken with anyone else's. The key or general gist to how I build things is about using the designing the robot with as little "extra" bits of metal and using odd placements of motors, pistons. This way of thinking forces you to build with as little material as possible without sufficing on quality of the build. I will give some examples of what this may look like. 

I like to take on a very conservative approach when it comes to construction. I focus on doing *kaizen*, or **long continuous improvement over time**. Despite the short production times for teams, I still try to follow this motto, unless it's the summer. In the summer that is when the most R&D occurs b/c you normally don't have time during school year (unless you're a middle schooler) to focus on other things. When competition season starts to take place, it is better off with a simple but reliable design over a unique but untested one. When you do need to innovative rapidly (most likely b/c you are behind meta, and didn't do enough R&D earlier in the season), I suggest doing a couple of meetings and even debates on how to design for the future since your team may be making either the best or worst decision ever. 

Rebuilds and iterative design takes time, and it brings into question why do we whine? For nearly 5 months, I ran a slow 360 RPM 3.25" drive base that was at least 1ft/s slower than the competition. Regardless that robot was the most sturdy and reliable robot I have ever built, and it brought me to the finals competition. I focused on simplicity and driveability on that robot and it worked pretty well, espicially considering most teams had a very intense build but we focused on building what worked. The grass is always greener on the other side... however we did have our fair share of mess ups.

After the 2024 Texas R5 championship, I rolled the dice with my team for our last year where we sort of procrastinated on building a PTO-hang for the 2024 World Championship for Over Under. We previously discussed building a robot that was as short as 6 inches but can expand to climb a pole that was about 3.5' in the air. We also planned on utilizing it to descore the opponent goal whenever there was a chance, although I was unsure with my driving practice that I would be used to that aggressive driving style (what I really mean to say is that I never done it before). I was only able to get the hang working 4 hours after the competition began, and then it started to get more smoother 12 hours after that (during 2nd day of qualifications). Huge shoutout to my team for perservering through. 

![image](https://github.com/user-attachments/assets/4c0588e1-5eb1-4424-8a4c-633004f3e73d)

*Figure 10: Utilizing a triangular support instead of building another tower to attach a back roller mechanism. It also features motors mounted at a 45 degree angle for the drive base for clean packaging and biased CoG for better handling.*

![image](https://github.com/user-attachments/assets/3816e3a5-4a42-4b02-80c2-8f0e45756000)

*Figure 11: 5408D Spin Up Prototype. Building a PTO (powertakeoff) system with slim margins of a triangular support and also using it to attach a flywheel mechanism.*

![image](https://github.com/user-attachments/assets/0466fb9e-d56d-4dbb-9f65-18c305e535d1)

*Figure 12: 5408D Spin Up Worlds Robot. Notice how there are a lot of right triangles (specifically 45-45-90s). Notice how the clean packaging of the PTO is practically concealed within the robot.*

![image](https://github.com/user-attachments/assets/ae18c463-03bc-49e5-9728-007bc77df3b6)

*Figure 13: 5408D Over Under Worlds Robot (in construction). Notice how little metal and neat the packaging is on this PTO. I put it very low to the ground to lower CoG and to make it less noticeable on the final robot.*

![image](https://github.com/user-attachments/assets/d4719203-9937-4d83-834a-894101dfa59f)

*Figure 14: 5408D Over Under Worlds Robot. The night before Worlds.* 

![image](https://github.com/user-attachments/assets/ef266a11-665e-4346-8e5f-8e45a3fa59c3)

*Figure 15: 5408D Over Under Worlds Robot. It is hanging off a pole*

I ain't saying that I build the best, but what I am saying is that I build with a specific style that focuses on cleanliness of design and low material costs. This is b/c we are primarily a team that uses very old metal, and we sorta lacked funding as compared to other mainstream teams around the world. (that also explains why we did not go to any special events outside of the World Championship). 

Other build styles focus on innovative uses of lexan (a kind of plastic sheet). This means you would need access to advanced manufacturing techniques past a hacksaw, scissors, and sandpaper, and now you would need a CNC machine, a vice grip, a grinder, etc. I normally built with what I had on hand, and reused old plastic components from other teams. 

## Extra 

It doesn't just lead an industry, it inspires one. 















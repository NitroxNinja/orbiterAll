# Intro 

The 2022-2023 VEX Robotics Competition: Spin Up brought some interesting challenges for us when it came to designing a shooter to shoot discs into the basket. The creation of the VTSS + PTO or the "Variable Tensioning Slip System + Power TakeOff" was motivated by the need to shoot yellow VEX Spin Up discs at varying ranges (but with a slingshot). 
I wanted to take this season a little more chillax, kinda of like in Tipping Point, but due to shifting team dynamics, it influenced nearly everything.

[VTSS just kicked in yo!](https://youtu.be/iQ8Dl0ZhW8Q?si=6DI0xGdQAKx4U9IW)

## How it works vs others

We must first talk about what VTSS is for. In our case, we had a slingshot. In order for a slingshot to shoot things it must be 1. drawn back, 2. loaded, and then 3. released.

In order to draw a slingshot back we use a winch/pulley to bring the basket to a holding position, but you need to be able to hold the hopper/basket so you can load... so what we did was use a pneumatic piston to lock the sling into place. After which we would unwind the winch/pulley **BY AN AMOUNT** (this will be important later) since the piston was holding majority of the load. 
There are only 2 main sensors we use for the slingshot to function. The IMEs (integrated motor encoders), and a limit switch to detect when the slingshot arrived to be hooked to the piston. 

![image](https://github.com/user-attachments/assets/6c8910c8-f064-4933-91fe-85e7e89d5f46)

*Limit switch here*

You must note that now that hopper/basket is tensioned forward while in the stowed position. It is ready to fire while the piston is released. The amount of tensioning of the system would correlate to how far/how high the discs shot. This leads to one problem. You can control how far you can shoot only based off the number of rubber bands you have, and given the circumstances of VEX Spin Up, you needed to shoot from various distances at various times. What most teams did was a Tension Cutoff System (TCS), where they would break off some of the rubber bands off the basket so they would have a reduced shooting force. It accomplished the goal of shooting from far distances in the early game, and shooting from close distances in the late game (since this is when stakes got tough). This was the go-to solution for nearly all slingshot teams, however there are more neat elegant takes that allow a true, fully variable tensioning slip system, for shooting at all distances no matter what time it was in the game. 

We had the advantage of having our PTO (power-takeoff) being placed in conjunction with the drivetrain and shooter, so most of the time the motors would be powering the shooter, and only during times of defensive plays (not often), we could switch whenever we want to. This is advantageous as we don't need to worry about shuffling our intake, or utilizing extra pistons for a 2-way PTO (that we didn't have, and we didn't want extra moving parts on our system). 

![image](https://github.com/user-attachments/assets/8974baa6-295c-4873-8ae7-edb0f1683a73)

*Drivetrain to Shooter PTO, you can see the piston below one of the pneumatic tanks*

We utilized this advantage to adjust how much we can **UNWIND** the winch, and therefore we can manipulate how much rubberband potential energy goes into the shot, since the sling shot would **stop prematurely** based off how much we unwound our winch. Thus at we tuned our slingshot based off the furthest distances we would need to shoot for the goal, which was around 13-15 ft. 

I roughly calculated with crappy FEA and hand calcs that our slingshot withstood the boundary conditions of 6 rubber bands by 1.5, so just enough for competition reasons. There was a slight deflection (for mechanical engineering nerds it means it went past yield strength), but it was so negligble that we didn't have to worry about it. You may be wondering, why would I allow for deflection if it's made of 5052-H32 Aluminum (which supposedly has high fatigue strength), the answer is, for weight savings, and just that I knew this sling shot tensioning was feasiable.  

However, this ranging system only works assuming if you have 3 discs in the hopper. If you had any less than that, the discs will indeed overshoot due to less-than-expected weight on the system. Thus we had planned to build a disc counter, where a line sensor or limit switch would detect how much discs are in the hopper. If we know how much are the hopper, we can add more or less slack to the string (so if I lessen the slack, ie tighten the string, I would get less shooting distance). These calculations would all be ran on the microcontroller/brain. 

It is also important to mention that rubber bands will wear down significantly with use. We wanted to avoid replacing rubber bands during championship, and only did so every other hour, for consistency sake. However we did find a solution to beat this though. VEX V5 motors often draw a predictable amount of current. We some simple paths, the more current that is being drawn for the motors, we know how much torque the motors need, and therefore we can estimate the current force from the rubber bands on the hopper (we would expect they get weaker with every use). The program would use this estimated number for the force of rubber bands, and unwound accordingly to fit these details. At close ranges, changing the unwounding amount was negligble, but espicially for autonomous this was important, since most of long range shooting occured there, with some exceptions where I used long distance shooting to avoid defense and hog the corners of the field for points and a positive vantage ground (think a "King of the Hill" type situation). 
  + *I also realized this system had it's shortcomings because the robot wouldn't immedieately recognize the tension feel through current, aka it took some time for the robot to learn how much to unwind. For teams who want to build a similar mechanism, I highly recommend using an SD card to permanently store the settings of the current. Make the code write and read settings from the SD card, and have it wipe every old entry for the code whenever the robot is turned off/on etc. I am no software engineer, so I wouldn't be able to help you if there were some bugs happening on the miniscule level but I figure it'll be pretty easy.*

For those nerdy odometry/localization folks, yes there was a program in development for automatically targeting and detecting where and how far the goal relative to the robots position. That way I could fully automate where the system would shoot. However I didn't feel like running this program at worlds since I wanted mostly full manual control over the robot. I felt like having systems that are too automated makes the driving experience boring, and often I got distracted and felt anxious if there was a sensor that could've failed or a screw that may break apart. I really tried to keep this system as simple as it could be, while still keeping the advantages of a slingshot. 

Overall, VTSS is about controlling how the slingshot would shoot at multiple distances (variable), modifying how the slingshot would release (tensioning-slip), and having it all under one unified system (combined with the usage of integrated torque sensors, line sensors, and perhaps odometry).

## A long iterative history 

*This section can be skipped if you want, but I highly suggest reading it.* 

Due to a shift in team dynamics, it led to us testing and prototyping a lot of robots that sort of differentiated us from other teams in Texas (that were honestly just bluffing it). It consists of the flywheel stages (iter. 1-3), catapult days (iter. 4), and the slingshot madness (iter. 5-7). The flywheel we were able to prototype a lot since it was built during the summer, the catapult only needed one iteration (b/c it worked so well), and the slingshot took 2 iterations that spanned over 6 weeks, one without a PTO, then one with it (accelerated via CAD). 

We sorta knew what we wanted going into this game. We wanted to have atleast a 6 motor base, with a 1 motor shooter and a 1 motor intake. We also considered doing a 6 motor base, with a 2 motor shooter and 1 motor intake, but that's illegal. So that easily spells out "CATAPULT" but we were kind of weird so...

### Iteration 1 : The Turning Point Redemption Arc

- Then... we treated it like our "Turning Point Redemption Arc" (TP was a VRC game played from 2018-2019), and wanted to fulfill our flywheel dreams. We started off by building a flywheel, and put a lexan-shaped U, large enough to contain 3 discs, where the discs would wind around the wheel going nearly a full 180 degrees. 
- We did this with the expectation that the flywheel needed to be able to fully transfer it's rotational kinetic energy for linear kinetic energy of the yellow discs, but this was overkill, and was quite difficult to package since of how large as heck it was. We sorta begun experimenting with PTO packaging here, it wasn't super clean, but it was cleaner than most team's executions (not bragging).
- We also discovered via testing, that a single motor spinning a half pound flywheel struggled to spin up to speed, and also struggled at maintaining speed when 3 discs were shot in succession. We knew that if we shot one at a time slowly, it would not suffice in a competition setting. We needed speed. 

### Iteration 2 : Forwards and Backwards Mojo Dojo

- Inspired by other teams, we decided to do a reverse-intaking but forward-shooting flywheel. This time this accomplished the goal of reducing packaging, and now with the inspiration to build a 2 motor flywheel paired with a 4 motor drive + 2 motor PTO drive/intake, we built something we were pretty impressed with. Took around 3 weeks, and we utilized 1 part of the intake PTO to spin the intake/top roller and then the other part of the intake PTO to power a linear reverse puncher-indexer that put the discs into the flywheel.
- Little fun stupid story, we testing a 2 motor flywheel and wondered why it took so long to spin up. Long story short, we were using voltage control, and that like demands "I WANT ALLLLLL THE POWER NOWWWW" but in reality velocity control (provided by the VEX library) does a suprisingly good job at getting the flywheel to the correct target speed so more it's like "VRRRmmmmmm the power is delivered smoothly and effectively, drawing more current from the battery as necessary".

### Iteration 3 : In a fit of rage 

- However I was pretty disappointed with the driving experience. I didn't like the idea of having a super fast flywheel that I could shoot forward, but then I had to go into reverse every single time I wanted to intake (you could also say I was a bad driver at the time). So then, I suprised my team by taking the robot apart immediately after a meeting, then put it together within 2 days. 
- The catch was that now I literally turned the same assembly which was intially forwards, to reverse, to face the same direction as the intake. I took the whole assembly and somehow parts of the PTO and it all fit... From there it was a little tid bid tuning so now the path where the discs traveled on the intake (1/2 part of the intake PTO) increased, as it went up and through the flywheel assembly, and to a hopper where there would be an indexer (from the PTO'd motor of the intake). It sucked at moving the discs into the flywheel on it's own b/c it had no compression/friction. So I put a piston that would gently press the disc stack down. Overall, the complexity of the robot increased by A LOT: varying chain/gear lengths, dropped gear ratio and lucky cantilevered gear placement for the PTO/drive interface, and featured a lot of odd rubber linked rollers (an experimental technique I used back in Change Up, will be writing a document over the big red and blue wheel).
- We also added a string shooter, that was a catapult and then there would be a pneumatic nut attached at the end. This was very dangerous and we will not be doing this again, also the coverage sucked (there were only 3 catapults, and it was heavy). Shoutout to my teammate Ayden for CNCing the lexan attachments and cutting up the plates to mount the joints and stuff.
- Needless to say after some tuning, and some programming we got this robot to work pretty ok. It intaked and shot discs, it moved fine, and it was overall an ok robot. We went to Wylie High School (to work with 22204V and use their field) and tested it. It shot at far ranges and medium ranges very well, however it sucked at shooting close range, and we planned on adding a speed reducer, and pneumatic lexan deflector that would shoot the discs more up and into the goal. 
- We also came to realize that our shooting speed was extremly slow, and this was mostly due to not only the intake path, but also the design of the indexer. We could've tuned this to be a menance for the competition, but after dealing with the complexity and bull crap the whole flywheel situation, I decided to destroy it all and start over with something I adored... catapults.

### Iteration 4 : The Golden Days

- My teammate (notice how it's in the singular form, only 1) got upset at me, but I knew I was correct. A fully connected simple 6 motor 600 RPM 2.75" drive, with a 1 motor 1 to 3 to 5 catapult, with a 1 motor intake and top roller. It was super simplistic and lightweight, and also fast, unlike our old prototyped robots. It was inspired by Ayush Palse (or Boots from 1961Z/OWL).
- It featured a reverse-intake, forward shooting catapult. This contrasts to what I said from iteration 3, but since it was a one shot one go, and I got better at driving, this catapult feature was justified. The discs loaded into the mechanism like a sandwich being ready to get shot and there it did. It did have a slight issue of the discs diverging after it got shot but for now it wasn't a worry.
- We took this one to our first 2 competitions (in 2022), where it took named, and qualified us for State. Our driving dynamics was so out of touch to other teams that it didn't make sense for other teams to strategize against us since it was so fast. It was simple, it was fast, it was *made* fast (didn't take that long to build), and most importantly it was reliable, like a Toyota. 
- My teammate argued that b/c it didn't have a good grouping (it couldn't shoot the discs over the line without them going everywhere in the vertical axis of motion). This is due to tangential velocity, where discs at a further radius from the joint will experience more linear velocity than the inner ones. This feels weird to know, knowing the the arm that hoisted all the discs experienced the same angular velocity.
- This was also when we switched to a "jelly" string shooter, where rubber bands would be released via piston and attached was some strings. My teammate struggled to build this, but when I came in, and fixed it, reducing the friction the rubber band had on the standoff by using a ziptie, he was suprised. Zipties for the win!
- He suggested we copy a team, 9257C, the Housecats, who have been experimenting with a slingshot style shooter, something of which not many teams built due to it's sheer complexity. He also argued that I drove sloppily, which was sorta true, but I didn't have that much driver practice at that high of RPM (I felt confident that I would get better on the coming months). At first, I rejected hard, but my other teammates argued for his point, and then I felt pressured to build something new and unique, and thus, the 2-3 weeks of winter break which I planned to enjoy turned into a nightmare.

### Iteration 5 : Darkday I

- I first started off by going back to a 4 motor 360 RPM on 3.25" drive. It was sad, and slow. I followed the common formula to building all 5408 bases, yada yada yada. Then came to mounting the towers and standoff linear slide for the slingshot. Then came the gearbox for the winch (which did not have any PTO), and then building the slingshot hopper and mounting it to the 2 standoff rails. It was also stabilized with another 2 25 hole full c-channels on both sides (**this will be important later to remember as it changes on iteration 7**), just b/c I knew the factor of safety and the shear brunt of blows this sling shot was going to be unbearable. The geometry was super sick though since I had intended to use many right triangles to compliment the overall theme of what I hope the robot to become: not a random cube. 
- From there I built the intake, which my teammate claimed I copied someone else, and in reality I didn't, it's just mere coincidence but he's being a little jerky. This featured a series of reversing flex wheels, and a custom omni-roller set up where I had to rip apart a 4" omniwheel, and put an axle through it. I used a 3" flexwheel for the final bit.

![image](https://github.com/user-attachments/assets/f5ebdd64-5015-482c-a7cb-84bf284c8264)

*I didn't copy anyone, I just made this after hours of building*

- I mounted all the pneumatics and the hooks and packaging which was sorta neat (and remained in the final iteration) 
- I had trouble with torque and tuning, and banding, since everytime the sling shot went up, the hopper would whiplash itself on the rails, bending the standoff rails, and also the hopper standoffs themselves. This required a lot of grease, and tuning to get it just right so it wouldn't tear itself apart. What was more annoying was the string getting stuck inside the motor ribcage of the gearbox (it'll make sense once I show pics). I started experimenting with a PTO and pneumatic shifting forks but this was thrown out for the sake of time and needing a working robot within a month.
- I got everything to shoot, move, and intake, and now it was time to test it.
- I often look upon these days as the darkest times for me in my time in robotics. I often spent my waking hours sitting down and thinking at this robot, wondering if it'll actually get anywhere. My team wasn't always there to help me, even though they had essentially pushed me into building this. I didn't know what to think. 

### Iteration 5.5 : Darkday II

- Iteration 5.5 exists b/c this was an odd transitional period between a non-PTO robot and a PTO robot. My teammate, in a feeling of disdain, and emotional-trolling, CADed up something which he thought would work and line up. However one thing I know about engineering, is that just b/c it works on the computer doesn't mean it works in real life. And espicially if you aren't good at using a computer, you'd expect the model of the robot to be pretty bad, and building that in real life... was not that great...
- My mentor once he saw this robot gave us an ultimateum. We were working so well with our catapult, and now had downgraded to a robot of somewhat lesser quality. My teammate gave me the "nudge-nudge-this is your fault" kinda look. And he (my mentor) was right. We weren't going to get anywhere with a normal 4 motor drive and a 2 motor shooter (which was incredibly slow). Our competiiton was coming in 3 weeks and we needed something soon, and something fast. So I sorta took the bait.
- He (my teammate) started experimented with a 2 motor intake to 2 motor shooter PTO, and the packaging for this was hell. It resembled more of factory conveyor belt system rather than a robot. The jungle of metal towers and triangles also made it difficult to work on (in practice). The difficult to access motors was even worse, and we would have not been able to create our VTSS.
- When we actually built it, none of the gears meshed properly. It would either mesh too much causing friction, or mess too little causing slippage. He (my teammate whom intiated the slingshot in the first place), undersupported our drivetrain, utilized too many washers for niche and uncomptaible spacing, and bent the very c-channels he promised not to bend.
- UGH, now it's up to me to fix everything!

![image](https://github.com/user-attachments/assets/70e5321d-74c8-4377-b10f-d3e71b0697d4)

*Gear shaft overmeshing resulting in misalignment.*

![image](https://github.com/user-attachments/assets/5a64b58b-7a55-48e6-8e96-8cb9af0d8729)

*Divorced gear set up. None of the gears meshed properly so this resulted in either too much friction in some places, or slippage in some other places.*

![image](https://github.com/user-attachments/assets/60955822-a5ef-4683-80b7-180deff29fa5)

*Gutted the sling-winch assembly for rebuild*

- 

### Iteration 6 : COROLLA

- I successfully argued that building a 2 motor shooter PTO to drive would be better since the packaging for a winch gearbox and the drive train were so close together, we could take advantage of the lower center of gravity
- I got to work on fixing his (my teammate) old CAD by neglecting it completely and building by my heart. Instead of having a divorced C-channel set up which required a lot of nitpicky adjustments, I added another c channel (adding a 0.03 lb extra weight) on each side, and kept the gears unified in a line, so the compound gear ratio would work. By the way, it was a 600 RPM powered 36 tooth gear, which spun a 48 tooth gear that was inline with a 24 tooth gear which spun a 60 tooth gear winch. If you do that math you get a 180 RPM final speed for the winch (600 RPM * 3/4  = 450 RPM -> 450 RPM * 2/5 = 180 RPM final speed).
- Sidenote, I use driver:driven for my gear ratios and not driven:driver. When I think about a gear ratio I think aboout fractions of sizes. Using driver:driven methodology, if I have a 1:5 gear ratio, my expected output speed would be 1/5 the speed of the input. However I say the other way, it sorta doesn't make sense and I have to flip the fractions and this means that but that means this yada yada math, THE WAY I WAS TAUGHT JUST MAKES MORE SENSE!
- I then added a PTO which would shift the gears, and a lexan backplate to sort of hold it in place. The pneumatic tanks were packaged in a way that fit the intakes. A rubber linked lexan ramp would be attached to this, and this concentrated by weight a lot in the middle of the robot.
- VTSS was being created for the first time when I realized I can control how much unwinding I want and therefore adjust the power. The variable tensioning slip system was something originally inspired by Toyota VVTI and Honda VTEC, but it sorta morphed into something of it's own.
- I added back on the string shooter from last last iteration, and brought this robot to a competition.
- It didn't work to well. I'll explain the rest later...

### Iteration 7 : GAZOO COROLLA 

- After the state championship, we qualified for worlds and realized our robots acceleration was really darn slow. This was due to the shear weight and complexity of the slingshot.
- I took insane weight saving measurements, I swapped out the main triangles of the thing to be half cuts, and the top structure to be half cuts. This would bring the CoG down and reduce weight by nearly 0.75 lbs. I also got rid of many of the screws and nuts on the bearings of the base and opted for using zipties, a technique which I had bastardized and shunned in the previous season (tipping point) for being unreliable. It seemed to function well
- I also found as much spots to use smaller c channels, and general weight savings. Overall, the weight reduction program made the robot go from 15 pounds to 14 pounds, which is a huge victory in terms of acceleration and finally having a manuverable robot.
- With this I could rely a little less on the 6 motor drive base and purely focus on a 4 motor drive and shooting. It got a little annoying for me to switch back and forth anyways, and plus I found my driving style to not really play defense that much. I also want to mention this drive had omnis only and promoted the idea of drifting to score. Something I got really good at (Initial D).

## Remarks and end of Spin Up 

- After Spin Up, I was drained mentally of most of my creative ability. I pushed myself past the limit and my Over Under robot would go to pay on that debt. I may be talking about this robot in another article. But overall it was a year of meaning and challenge, and it shaped me into the person I am today. I am the result of a lot of unique circumstances, and it made a robot that didn't just lead the competition, but it inspired it.

![image](https://github.com/user-attachments/assets/f144d78d-bd3b-4e88-ad28-ae28eaf646a7)




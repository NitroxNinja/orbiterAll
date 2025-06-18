# Intro 

The creation of the VTSS + PTO or the "Variable Tensioning Slip System + Power TakeOff" was motivated by the need to shoot yellow VEX Spin Up discs at varying ranges. The 2022-2023 VEX Robotics Competition: Spin Up brought some interesting challenges for us when it came to designing a shooter to shoot discs into the basket. 

## A long iterative history 

*This section can be skipped if you want, but I highly suggest reading it.* 

Due to a shift in team dynamics, it led to us testing and prototyping a lot of robots that sort of differentiated us from other teams in Texas (that were honestly just bluffing it). It consists of the flywheel stages (iter. 1-3), catapult days (iter. 4), and the slingshot madness (iter. 5-6). The flywheel we were able to prototype a lot since it was built during the summer, the catapult only needed one iteration (b/c it worked so well), and the slingshot took 2 iterations that spanned over 6 weeks, one without a PTO, then one with it (accelerated via CAD). 

We sorta knew what we wanted going into this game. We wanted to have atleast a 6 motor base, with a 1 motor shooter and a 1 motor intake. We also considered doing a 6 motor base, with a 2 motor shooter and 1 motor intake, but that's illegal. So that easily spells out "CATAPULT" but we were kind of weird so...

### Iteration 1

- Then... we treated it like our "Turning Point Redemption Arc" (TP was a VRC game played from 2018-2019), and wanted to fulfill our flywheel dreams. We started off by building a flywheel, and put a lexan-shaped U, large enough to contain 3 discs, where the discs would wind around the wheel going nearly a full 180 degrees. 

- We did this with the expectation that the flywheel needed to be able to fully transfer it's rotational kinetic energy for linear kinetic energy of the yellow discs, but this was overkill, and was quite difficult to package since of how large as heck it was. We sorta begun experimenting with PTO packaging here, it wasn't super clean, but it was cleaner than most team's executions (not bragging).

We also discovered via testing, that a single motor spinning a half pound flywheel struggled to spin up to speed, and also struggled at maintaining speed when 3 discs were shot in succession. We knew that if we shot one at a time slowly, it would not suffice in a competition setting. We needed speed. 

### Iteration 2

- Inspired by other teams, we decided to do a reverse-intaking but forward-shooting flywheel. This time this accomplished the goal of reducing packaging, and now with the inspiration to build a 2 motor flywheel paired with a 4 motor drive + 2 motor PTO drive/intake, we built something we were pretty impressed with. Took around 3 weeks, and we utilized 1 part of the intake PTO to spin the intake/top roller and then the other part of the intake PTO to power a linear reverse puncher-indexer that put the discs into the flywheel.

- Little fun stupid story, we testing a 2 motor flywheel and wondered why it took so long to spin up. Long story short, we were using voltage control, and that like demands "I WANT ALLLLLL THE POWER NOWWWW" but in reality velocity control (provided by the VEX library) does a suprisingly good job at getting the flywheel to the correct target speed so more it's like "VRRRmmmmmm the power is delivered smoothly and effectively, drawing more current from the battery as necessary".

### Iteration 3

- However I was pretty disappointed with the driving experience. I didn't like the idea of having a super fast flywheel that I could shoot forward, but then I had to go into reverse every single time I wanted to intake (you could also say I was a bad driver at the time). So then, I suprised my team by taking the robot apart immediately after a meeting, then put it together within 2 days. 

- The catch was that now I literally turned the same assembly which was intially forwards, to reverse, to face the same direction as the intake. I took the whole assembly and somehow parts of the PTO and it all fit... From there it was a little tid bid tuning so now the path where the discs traveled on the intake (1/2 part of the intake PTO) increased, as it went up and through the flywheel assembly, and to a hopper where there would be an indexer (from the PTO'd motor of the intake). It sucked at moving the discs into the flywheel on it's own b/c it had no compression/friction. So I put a piston that would gently press the disc stack down. Overall, the complexity of the robot increased by A LOT: varying chain/gear lengths, dropped gear ratio and lucky cantilevered gear placement for the PTO/drive interface, and featured a lot of odd rubber linked rollers (an experimental technique I used back in Change Up, will be writing a document over the big red and blue wheel). 

- Needless to say after some tuning, and some programming we got this robot to work pretty ok. It intaked and shot discs, it moved fine, and it was overall an ok robot. We went to Wylie High School (to work with 22204V and use their field) and tested it. It shot at far ranges and medium ranges very well, however it sucked at shooting close range, and we planned on adding a speed reducer, and pneumatic lexan deflector that would shoot the discs more up and into the goal. 

- We also came to realize that our shooting speed was extremly slow, and this was mostly due to not only the intake path, but also the design of the indexer. We could've tuned this to be a menance for the competition, but after dealing with the complexity and bull crap the whole flywheel situation, I decided to destroy it all and start over with something I adored... catapults.



## How it works

How it works is that we built a 6-rubber-tubes-tensioned linear slingshot that would be drawn/pulled back by a 180 RPM stringed winch held via highstrength plastic collars. Once it's completely pulled back and it is hitting the physical stop (and thus a limit switch), a pneumatic piston (minimum 25 psi) would engage to lock the sling holder into place. However this 180 RPM string winch would need to unwind, so then it did, ONLY TO A CERTAIN AMOUNT (based upon the current drawn by the motors). Once it is fully unwind, I (the driver) would press a button and whatever discs are in the hopper would shoot at a 4" range from the target (this assumes there are 3 discs in the slingshot hopper). 

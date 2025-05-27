## Preface
Below is kind of me documenting my time working at this company that makes roofing products. I am mostly writing this to keep track of how far and what kind of things I've done over the 13-14 weeks I will be doing this job. The information in this file is not to be a 1:1 match of real, high quality, machines for roofing products. 

INTRODUCTION: 
The creation of an asphalt shingle starts with a dry mat or fiberglass roll that goes through a thing call an accumulator. The accumulator acts as a way to continually hold a large volume of the fiberglass rolls as production must be continuous. The dry mat is then continually switched throughout the day by an operator(or person) that rotates on a stand and is spliced on a machine as it passes through. 
Next it is coated with a very hot mixture of mineral fortified asphalt (around 440 degrees F) is layered onto the accumulated fiberglass sheet. It is then slated with asphalt/limestone mixture and is packed/pressed into the roll. This then goes to be cooler which uses air and water sprayers to reach a desired temperature. The setpoint and the temperature of the shingle roll is taken into account and 3 to 4 sprayers may be used depending on the speed (thermodynamics). 
This then goes to the FPL (finished product looper), which takes 20-35% capacity of the accumulated sheet (you’ll hear the loud banging, simply from the speed of it curling up and rupturing after reaching a suddenly slow speed) from all the shingles lining up ready to go to it). 
 
FPL
Paint applicator and Mixing sys 
Laminator System 
Soap Applicator System 
Bundling Wrapper and Film Unwind stand
 
1st week analysis:
-	Every part added to the SOP complicates tasks for workers and requires time and money to train. 
-	ESSA model (Eliminate, simplify, systematize, automate) … part of lean mfg., which is a part of the Toyota Production System.  
-	Genchi genbutsu (go see for yourself) has been practiced. 
-	5S, Set in order, shine, standardize, and sustain. 
-	Every little imperfection gone unchecked during the manufacturing process could lead to a tear in the shingle line, wasting time and production numbers. 
-	Thus preventative maintenance is done, I supposed they already have this figured out by the engineers on when it might need replacing (based off past manufacturing). I have yet understand how PdM (predictive maintenance) is done, I’d imagine there’s some sort of calculator based off the quadrature encoders of the system. As my supervisor suggests, the shingle is essentially a roll of sandpaper that passes through a bunch of rollers, and wears out to time. (Read the blue screen of the front FPM and the coater FPM and it may determine the overall speed of the whole line. 
-	Sometimes the torque numbers and process can change over time, and those numbers need to be continually updated regardless of the PID/control systems. 
-	Please note that sometimes it’s important to just have a simple system, not every operator understands how blah blah blah machine learning algorithm bang-bang PLC works and it’s easy to be make it bang-bang if possible.  (keep it simple, stupid)
-	There does seem to be a general knowledge on what “setpoint” is or what I like to call “desired value”. It can be adjusted using a panel, and there’s some text on it indicating what temp is good. 
-	I’d imagine this a multiple input multiple output (MIMO) system, 
-	5/23/25. Issues with space for pallet placement due to logistics with placing pallets on a hill. Also noticed that a mechanic was paying attention to how there was a some kind of a missing roll of tape on the shingle. So not all stops are attributed to tears but if there is one minor detail that’s off the mechanic can shut off the entire line. 
-	For the staging conveyor(where the shingles are about to be put on the chain pushers), the automation engineering sort of implemented a temporary solution(or maybe something broke) of turning the motor clutch on and off again, there’s a horrible clanging sound every single time the motors rolls but it does solve the problem of the shingle groupings not hitting each other. 
-	Some electric motors have clutches b/c they need to quickly disengage.
-	Some electric motors could paired with brakes. Braking applies strain on not only the motors torque, but also the system’s as a whole, especially on a part that is always cantilevered. 
-	Sometimes solving the problem of pallets not being straight doesn’t even require engineering. It requires management. 
-	Major failures are always recorded on IKO’s DNA thingy. Every thing is scrutinized and questioned, and a seemingly random event can be tracked and understood, and this may lead to engineering improvements so that production can be improved in the long term. They go through some sort of evidence process and highly intensive investigation with mechanic/electrician witness reports! One incident costed 100k to fix… But 100k to fix is also 100k spend investing towards a better system, so not all investments are the same. 
-	A corrective action list has been developed, for these kinds of issues. A best practices is filled out, I.S.O., procedures work instructions and PM. No PdM has been read about yet so I’m still learning about that. 
-	PdM via a machine learning model and sensor readings may be helpful, but to connect the HMIs (or computers that are in production) may require some networking skills and IoT ideas that may not get approved.
-	Perhaps create a LAN through switches and routers although I am not sure if that will get approved.  
-	Talk to Abel on how to see data from the computer. 
-	Understanding from the variety of quality tests, shingles must meet certain standards set by the ASTM. There is a temperature tests, a sort of asphalt boiling test that I can’t remember, a tear test, a sand granule fine mesh sieve test. 
2nd week analysis: 
-	PROJECT ASSIGNED: Something in regards to the granule system, requiring a size 14 granule size, why can’t we break up the granules a little more(?). I am asked to define the problem first, very clearly, and this is to be presented on a weekly basis. (I have to get to know the PowerPoint format and the excel progress document.  )
Tips for this: Read OEM’s manuals, read theory of operation, in fact just read everything in regards before making a crazy decision to change a major part of the system. 
-	As in right now I am reading Aravind’s presentation over how to set up the presentation and things like that. 
-	It seems to me that Brampton (the plant) seems to have a lot of standards set in place for production. For example the scraper that they use is bronze, and we use spring steel but we are considering switching to reduce costs, but maintenance cycles could be more expensive so that needs to be studied. 
-	One of the goals as engineers is to make production as cheap as possible without sufficing quality of the shingles (as they are now) or perhaps even improving the quality of the shingles. 
-	Granule system starts off with the trucks dropping off materials such as andesite (rocks and stuff), into silos. 
OVERALL THE Technician Work IS ABOUT 
Size 14 granule separator. 
How can we increase the rate of granule separation that is happening? 
Can we ensure the reliability of the SWECO separator? If so, how can we do so in order to maintain? Are there any wear indicators or maintenance we should do on the system? 
Should we measure the rate of production for the size 14 granules? 
How can we ease the process for operators? 
So in order to understand the parts of the round separators we must come and see the 
It is something done to keep something running. Although my skillset has been given an underutilized task, I think it will be ok for now. 


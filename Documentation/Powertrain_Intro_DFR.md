# Intro 

This is an account of events that happened with my time in Dallas Formula Racing (DFR) on the powertrain subteam and how might a new team member may expect to succeed or not. 
To ask why a person may want to join my establishment is quite pecuilar as we all find our own reasons to join, regardless if we like it or not. 

![image](https://github.com/user-attachments/assets/02ffd9e7-2b50-43b0-bb51-556088a62ff3)

Contents are 
- What's the experience like?
- Why study racecars?
- Parts of the Powertrain
- What's so significant about exhaust?
- What we did.
- Experimentation and Tuning
- Manufacturing
- Conclusion

## What's the experience like? 

The leadership structure of DFR is rather left to intuition and accountability of the individual members. It will feel hierachal at first and you must bridge across! You'd be able to have a lot of "freedom" with how your schedule runs as long as you complete your delieverables or tasks to be done. These are checkpoints called "Gate 1, Gate 2, Gate 3, Preliminary Desgin Review, Complete Design Review" and if failed, you'd get to "Final Design Review". Update: In the newer 2025 development cycles, the powertrain lead hinted that some of thse gates would be removed in order to promote the development of the car over the defense and politics of design. 

Oh yeah did I mention you could "fail" a delieverable? This meant that whatever you are designing or making, it must be defended and validated often with mathematical and physics proof, or through simulations and CAD, and whatnot. For every delieverable, you don't always have to be 100% ready to go, and it's meant to be a "learning experience" and is supposed to closely mimic what happens in the real world. I'll admit, it'll feel pretty slow, and the higher ups most likely will give you a lot of work to do.

However this work may normally grunt work in the beginning, but as you gain more experience and "get trust" you may get to work on more interesting topics. If you're a freshman and want to take an endearing task like rebuilding a differential mount, or running 1000 simulations on the new intake manifold to validate X, Y, and Z, try talking to the older members to see if you could help. If you do want a change in pace, and want to be more involved with the design process of a whole product, rather than improving on what exists, then maybe racecar development isn't for you. **Try doing robotics instead!**


## Why do we study and engineer racecars to this day?

FSAE is a student-based engineering competitions for students to build the best racecar they can according to rules, budget, and other factors. They must be able to create a "selling point" to the judges along with competing in dynamic events such as endurance, skidpad, and other things to evaluate which university has built the best car. While racecars and automotive development has existed for over a century, there are still many learning opportunities that students can learn from competitive racecar development.

For starters, most people who join this club already have a passion for racecars and automotive things, and would like to get more involved. In the real world, as a mechanical engineer you won't be able to work on the whole car itself, but rather you are constrained to making one part of the car the best you can, in accordance to other parts, as your lead may desire "harmony". You may be stuck making 4 metal pipes that merge into 1. You may be stuck making metal tabs, you may be stuck doing yada yada yada, but that's sort of the beauty in it. 

## Parts of the Powertrain

In powertrain, our job is to develop and finetune engine-related and power-transferring (like the limited-slip-differential) components, or the "heart of the engine". In DFR, we have sub-subteams in our powertrain subteam. That features **intake, exhaust, radiator, diff mount/final drive, and fuel**. This covers majority of the topics in mechanical engineering when people say they want to do mechanical engineering (just wait until you hit controls and systems). What I mean by that is computational fluid dynamics, finite element analysis, heat transfer, thermodynamics, statics + mechanics of materials. This by definition makes powertrain the most diverse team and prone to the most learning opportunities, since b/c our team is relatively underdeveloped there's potential for newbies to grow.

For me I worked on the exhaust with a couple of my friends. At first we had to understand the "scope" of the project or what we're aimming to do. So the goal was the reduce weight and improve vehicle dynamics, and what better way to do that by making a side-exit exhaust? 
At first we ran into some trouble learning how to CAD, then it was debating if we should justify this length of pipe or a 4-1 collector, selecting titanium or stainless steel, and estimating where our powerband will be based off resonance and fluid hand calculations. 
We also learn how to design with the human trait + regulations in mind, thinking of a DFMEA (Design Failure Modes Effects Analysis) where we evaluated risk on certain parts of an engine.

Oh yeah, hand calculuations will be important and will be mentioned later on when it comes to creating test cases and "boundary conditions" for your simulations. 

![image](https://github.com/user-attachments/assets/245d0abc-3c07-44e4-874a-91a5e8b84463)

## What's so significant about exhaust?

When it comes to designing the exhaust of a car, it is impactful b/c it shifts how your engine behaves and delivers power. For example, an exhaust with a very long-headers suffer on low-end-RPM torque, but has great power at high-end-RPM. 
So what that means in the context of racing, is that it'll be slow from a standstill, or tight corners, but once the car gets going, it's fast and reactive. Another example, an exhaust with a larger diameter may also suffer low-end-RPM torque but also breathe a lot better at higher RPMs, and I think you can get what I'm saying but why is that? 

It's b/c in order to make power you need to put a lot of oxygen+gasoline into the cylinder, so that when it compresses and *hopefully* combusts, it will leave the cylinder so that newer fresh oxygen+gasoline may combust and produce even more torque. However this is only assuming a perfect world, where gas moves where you want it to move and it's instantaneous and fast. You can do some simple hand calculations to prove that air does not move that fast (think the speed of sound). 
In an 4-stroke Honda 600 F4i engine (and many engines like it), have a thing called valve overlap, which allows a cylinder to create a pressure differential from the intake's plenum (think an oxygen storage), to the cylinder itself, while the exhaust port is opening and letting the already-combusted-gases out. 

Pressure differentials allow us to understand how gas will move from one place to another (think about what you learned in school about osmosis, high pressure likes to settle down by going into lower pressure). There's also things like heat to consider and most suprisingly... SOUND! 

Engines are really loud. So loud to the point where it disrupts the air and a thing we call "pressure waves" in the atmosphere. But within an exhaust pipe, it's intesified even more. You see, in an hot exhaust, energy is being expelled in the form of heat, sound, and kinetic moving gas. From here we can calculate the speed of sound within the pipe.
As the sound already disrupts the medium of air inside the pipe it goes down like a pressure wave until it encounters a change in the diameter in the pipe, from there, some of the pressure wave will refract back from the point and BACK into the exhaust port! Think about how you clap or speak into a very long pipe. It ECHOS back to you!

![image](https://github.com/user-attachments/assets/0e966204-bf32-47b2-90b2-abc19769281c)

*Person plays saxophone in front of long open pipe, echos*

In summary, since the speed of sound is faster than the exhaust gas itself, we can use that phenomenon of the "disruption of air" to help us build the exhaust, since it basically creates a pressure differential. In F1, engineers are able to tune the behavior of their exhausts, by using "stepped" headers which are incremental increases in diameter of the exhaust which helps draw more air out of the cylinder earlier, based off the change in the diameter of exhaust itself.

![image](https://github.com/user-attachments/assets/0fe34de8-7438-4ff4-af65-a58922f5ce1b)

*Stepped headers allow the engine to make more power at higher engine RPM"*

From this speed of sound, there's a lot of general equations to work off of, and that's up to your own research and findings through sims and such. It is also helpful to understand what the firing order of your engine is, if it's even firing or odd firing, as that may affect how you design the lengths of each individual header. 
Since we use a Honda inline-4 motorcycle engine, every combustion cycle happens at every 180 degrees the crankshaft rotates. Some other engines are weird and explode at different rotates like 90-270-180-blah-blah for every cylinder but we can ignore that for now. Based off that we can calculate how much gas is being expelled from the engine, and we can justify a length from there. 

TLDR: As a result, the common formula for exhausts on race cars, is to literally **TUNE** the exhaust diameter and length. 

## What we did. 

Me and my friends designed a lowered side-exit titanium exhaust manifold. This was to **reduce weight** of the car (even by an itty-biddy amount of 1 lbs), and **lower the center of gravity** to allow for less body roll and overall less strain on suspension components. We essentially aimed to make the exhaust predictable and optomized for the driver, and not just "OH MY GOODNESS 1000 HP SUPRA GTR!!", because we believe posterchild numbers aren't the only defining characteristics of an exhaust. 
We also were able to justify the usage of a titanium exhaust over a stainless steel one, b/c the 40% reduction in weight in comparison to the old exhaust system was fair. It was also b/c titanium tends to retain more internal heat. The more internal heat you have, the more kinetic energy you'd expect to have inside the exhaust, helping bring the exhaust gases out of the engine. This also help mitigated possible safety risks of fuel vaporization (b/c the exhaust was close to the fuel tank), and handling, as titanium can cool down a lot faster after usage. 

Based off the mathematics we did and research papers, we ran a basic CFD simulation that was... admittedly ran with trash b/c Solidworks CFD uses k-ɛ model for the meshing kind of situation (?). The thing is that we must account for heat and sonic flow. As a result, when we showed this, we got roasted and were told to throw it away. However we were able to justify, even with a trash simulation, taking into consideration the friction of the walls, and the complex geometry due to the packaging constraints justified our equal length runners (or EL runners for short). 
That means there is very little cross-disruption in how pressure waves will behave at the collector (where all the 4 pipes merge from the engine into 1), meaning the internal flow won't generate too much backpressure, and will be less turbulent. 

![image](https://github.com/user-attachments/assets/0d397baf-f395-47a9-9028-dbe17f5b4aad)

*Learning CFD for the first time*

As a newer member, we are very far from understanding if it's important to care if there's turbulent or assuming laminar flow, b/c if we did not understand the physics of it, we could not **defend** or justify the design to the boss (Chief Engineer). Running simulations DOES NOT give you a easy "Yes or No" answer and it's rather more complicated than that. You must consider the validity of your boundary conditions, the model you're using, or even if your numbers seem real. From there it will provide a multitude of results on what to expect on a designed part - otherwise it's back to the drawing board. 
I can't provide any more mathematical/technical details on sonic-to-supersonic flows and Reynolds values of an exhaust pipe, so I recommend reading up on that. 

## Experimentation and Testing 

Perhaps the most fun thing I did as a powertrain engineer was visit the DYNAMOMETER (can't believe they named it after my team) or dyno for short to get our car's wheel horsepower (WHP) and torque. This is helpful as it justifies certain design decisions from intake and exhaust when it comes to predicting or improving the next design. 

You can adjust things and learn about air-fuel-ratios(AFR) with the O2 sensor, adjusting fuel tunes, adjusting when the fuel shoots (typically by read into relation in accordance to crankshaft position sensor). 

Also literally no one knew what a closed-feedback-loop on the tunes. When we were trying to adjust the AFR to 13.5 or 14.7 (stochiometric), our team was busy manually tuning the car for every RPM. I told them why would they do that to themselves when you have an ECU and a O2 sensor that can automatically straighten the AFR for you? Just let it run and let it do it's math to control how long the fuel injector was open?!? 
After awhile, they were convinced and finally put it in. I guess that's one thing I'm proud about. 

![image](https://github.com/user-attachments/assets/99d1b1ff-d359-4773-8c01-4bff11853e54)

*Fuel injection testing* 

![image](https://github.com/user-attachments/assets/f6e8d7e7-3ec9-4f0c-a975-245b802d11ac)

*Dyno Testing*

## Manufacturing 

I know nothing about welding, TIG, MIG or whatever. In manufacturing, I have to understand what it may be like for the person making my horrid creation, and see if I can make it easier for him. I can do this by doing GD&T with my engineering drawings, making jigs (things that you can lie your metal on to straighten/square up parts), or simplifying the design from the get-go. 

As far as I understand, and I will be taking from Noah H. from Long Horn Racing, he taught me that in order to weld, you need a lot of tools and gases for the job. TIG means Tungsten Inert Gas For example titanium is very suspectible to oxygen contamination, so as a result you need plenty of argon gas to purge the insides and outsides of the pipe. You must also be careful with how hot you're going. 

![image](https://github.com/user-attachments/assets/ce13337d-423e-4d2c-a3f8-0fe391c384db)

If you want to read more about welding and manufacturing in general, please read his document, it's very helpful and compiles more sources. 

Noah's good tips: https://cloud.wikis.utexas.edu/wiki/external/YTRhMDdmNjlhZjZkNGM3YThjMDUyOGExN2YwODBhMjk 

## Conclusion 

So in summary, in order to be successful/or to make the most out of your time in DFR is to try to talk with older members and see if you can contribute a lot at your project. Take small, but necessary steps to where you want to be. Do you want to take on more endearing projects? You'd have to prove it to them. It doesn't matter how small your project is, you need to perform your absolute best on selling your part and in return you will gain more positions in this rather bureaucratic organization. DFR served as a rough albeit necessary way for me to grow as an engineer, and I plan on contributing for awhile.

I do wish to change and transform on what being DFR member means though, something where politics is not a worry-some-point but learning is fostered more. Rather than doing independent research, why can't we run short meetings on knowing each other and sharing on knowledge on race cars? There seems to be a massive knowledge retension issue, and I hope my writing gets to you, and inspires something to change. There's a lot of smart people here, but do they know how to win? Not precisely, and I want to bring that culture of learning and friendship. Yes you'll feel like trying to break into a clique, but just be friendly and move on if you need to.

## Gallery

![image](https://github.com/user-attachments/assets/0dfad92b-781f-4797-9fec-1ade491aa5a5)

![image](https://github.com/user-attachments/assets/ee58dd08-31ac-4858-9e4c-b1b4778d631a)

![image](https://github.com/user-attachments/assets/8d1e77cc-cdce-49cd-bf26-d599c157c7bf)

![image](https://github.com/user-attachments/assets/13d00503-84a8-4c6e-93e9-f6d84f7c46cf)








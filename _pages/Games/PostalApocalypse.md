---
permalink: /Postal-Apocalypse/
layout: splash
author_profile: false
title: "Postal Apocalypse"
# toc: true
# toc_label: "My Games"
# toc_sticky: true


Contributions:
  - image_path: Photos/GameScreenShots/Homer.gif
    alt: "placeholder image 2"
    title: "Player"
    excerpt: "I lead all development related to mechanics and controls of the playable character."
  - image_path: Photos/GameScreenShots/Homer.gif
    alt: "placeholder image 2"
    title: "Cameras"
    excerpt: "I implemented all camera systems and configured them to allow for interesting cinematic shots, dynamic follow cameras, and first person shooting perspectives."
  - image_path: Photos/GameScreenShots/Homer.gif
    alt: "placeholder image 2"
    title: "Game Systems"
    excerpt: "I designed and maintained the Delivery System, the main gameloop system present in Postal Apocalypse."
---
{% include video id="YL3SATmfDdM" provider="youtube" %}

- **Release**: April 2025  
- **Studio**: Postal Productions  
- **Platforms**: PC, Linix. Controller support  
- **Skill Focus**: Player Controls, Cameras, Game Systems.  
- **Engine and Tools**: Unity  
- **Time Spent on Project**: 8 months   

---

# Evolution of the Delivery Truck
The final product of the delivery truck came after many iterations, adjustments, scrapping ideas, and entirely reworking systems.

## Initial Idea
I knew right from the get go that the truck was going to hover, we designed the game this way to create contrast between the pirates and the delivery truck.
The first iteration of the truck was a simple block that could hover above the ground. The feeling I was aiming for were the speeder bikes from StarWars.
The hovering was acting as intended, but I wouldn't compare it to the speeder bikes... more like the slow bikes.

Gif here

## Shooting!
The player was never going to leave the vehicle, so we decided to shoot packages at our unsuspecting customers instead! Nothing like a broken parcel!
My first prototype of shooting was clunkly, controls were wasd to move, arrow keys to aim the cannon, and spacebar to fire. Players could shoot packages or bullets by changing what gun they had mounted by pressing tab.
It wasn't great, but nothing is when you start!

Gif of shooting packages and bullets

## SICK FLIPS
The next feature to the vehicle I added was the ability to perform flips in the air. Completing backflips or frontflips would accumulate extra points exponentially (for consecutive flips) to add to your final score.
We received really good feedback during our testing sessions on this feature, something that players still comment on every time they play!

Gif of flips

## More Speed Please!
As our map was expanding, testers began to comment on how long it would take to traverse the length of the map. We did some testing and realized it took roughly 2 minutes to get from one side to the other. If a player was assigned a delivery on each corner of the map, it would take them upwards of 6 minutes to complete these deliveries. The game was only meant to last 10 minutes so this issue needed to be addressed immediately.

To solve the made two changes: 
1. I increased the speed, simple enough right? Wrong, traversing the map was a lot faster now, however, testers were still complaining about moving too slow. To remedy this, I...
2. Implented a booster. The booster had a cooldown so players couldn't spam it, however this event gave players more options to move around the map now.

## Lateral Forces!
The new changes to speed presented some new problems. The delivery truck was falling off the road constantly. Testers were spending more time getting back onto the roads than they did driving on them. Additionally, as plots of land became more populated with houses and tree's, the only place players could drive anymore were the roads.
To fix this, I added lateral forces to the vehicle. The lateral forces that tires exert with the ground are what allows a car to turn, the force is calculated using multiple variables and constants, however I would just use speed and left and right input to affect how sharp we can turn for now. With these new lateral forces, the vehicle now begins to slow down when we make sharp turns, which in turn (pun), allows for tighter turning, i.e better handling. 

Now you're probably asking "How is there friction with the ground if this is a hovering vehicle?". Great question, sometimes not everything needs to be realistic, especially if the unrelaistic version feels better!

## Cooler Shooting
The major change implented here was how the player aims. Changing the direction of the cannon to always point towards the mouse cursor made aiming so much easier, shooting the Porch Pirates became much easier to do while driving. 
I also added some lasers coming out of the barrels, and particles effects to the bullets when we fired them. It looks cool now!

The package cannon would now shoot the packages in a smooth arc towards their target. Looks great!

## System Rework
Christmas break was coming up, and so was our development checkpoint set in mid december. Due to mismanagement with our time and deadlines, the state of our game wasn't anywhere near where we wanted to be. For the player mechanics, testers were still complaining about poor handling, buggy shooting, and unintuitive controls. Our team headed into the 2024 christmas break knowing we needed to bounce back when we returned in 2025. 

Over the break I took it upon myself to learn the physics behind driving. I created multiple prototypes and prepared myself to overhaul the entire driving system come January 2025. 
Once we returned, that's exactly what I did. One goal I was set on achieving was creating a customizable system, something where I could tweak constants very easily. I wanted to speed up the development process. 
I had achieved this system by the second week back after break. The vehicle wasn't driving great, but because of the customizable system it was easy to understand why and easier to change those values.

## Drifting
I always intended on eventually adding drifting to the delivery truck, now with this new system, I could! I added the ability to oversteer and understeer during the drift. Additionally, drifting would charge a boost that would be exerted once the drift was completed.

## Removing Shooting
Once driving required less focus to stay on the roads, we found that testers were eliminating pirates with too much ease. We wanted the player to be afraid of the pirates, and try to avoid them so to not get their inventory stolen. So, we removed the cannons that shot deadly projectiles entirely. Now the player only had the package cannon to fire their parcels at customers homes.

Along with this removal, I added an aiming state to the cannon. Aiming would change the camera into a first person perspective behind the cannon. Aiming the cannon felt more like a minigame inside of the game now. Most importantly, the aiming became intuitive.

## Final Tweaking!
The mechanics were all there and working now, the only thing left to do was to tweak values.
I made the truck faster, allowed it to turn while stationary, added more lateral slip, and countless other small adjustments to get to where it is now.  

One major change to affect the driving wasn't done on the truck's code at all, but in physics bodies of every object the truck could hit. This major change was to the physics material placed on the objects. The default material reacts to collisions by absorbing forces and creating lots of friction which brings any object that touches it to a full stop very quickly. I changed these values so the truck would slip off of the buildings and bounce off them upon collision. This allowed players to keep a larger portion of their speed if they fell off the road.

## Audio and Visual Effects
Functionally, the delivery truck was in it's final state. It was time to emphasize all of it's features using visuals and audio.
I noticed a lot of complaints about the feel of the truck went away once the effects were added in. These queues confirmed to the player that their input was having an affect on the truck.

## Final Version
The video you see below is gameplay of the final version of the delivery truck. In total this project lasted 8 months, I'd say a half my time went towards this truck, while the rest was split amongst the other area's I was in charge of.
I'm very pleased with this final product, and I learned so much along the way.

Fun fact: While learning about how friction on tires work. I found out that realistic driving simulations have to guess the values of different constants in tire force calculations. This is because tire manufacturers keep constant values under lock!



{% include feature_row id = "Contributions" %}







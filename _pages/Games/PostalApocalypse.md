---
permalink: /Postal-Apocalypse/
layout: single
author_profile: false
title: "Postal Apocalypse"

sidebar:
  nav: "willyiam"

toc: true
toc_sticky: true

initialIdea:
  - url: /Gifs/Postal/InitialIdea1.gif
    image_path: /Gifs/Postal/InitialIdea1.gif
  - url: /Gifs/Postal/InitialIdea2.gif
    image_path: /Gifs/Postal/InitialIdea2.gif

initialWorld:
  - url: /Gifs/Postal/InitialWorld1.gif
    image_path: /Gifs/Postal/InitialWorld1.gif
  - url: /Gifs/Postal/InitialWorld2.gif
    image_path: /Gifs/Postal/InitialWorld2.gif

flips:
  - url: /Gifs/Postal/FrontFlip.gif
    image_path: /Gifs/Postal/FrontFlip.gif
  - url: /Gifs/Postal/BackFlip.gif
    image_path: /Gifs/Postal/BackFlip.gif

shootingBullets:
  - url: /Gifs/Postal/Shoot1.gif
    image_path: /Gifs/Postal/Shoot1.gif
  - url: /Gifs/Postal/Shoot2.gif
    image_path: /Gifs/Postal/Shoot2.gif

shootingPackages:
  - url: /Gifs/Postal/Package1.gif
    image_path: /Gifs/Postal/Package1.gif
  - url: /Gifs/Postal/Package2.gif
    image_path: /Gifs/Postal/Package2.gif

moreSpeed:
  - url: /Gifs/Postal/IncreasedSpeed.gif
    image_path: /Gifs/Postal/IncreasedSpeed.gif
  - url: /Gifs/Postal/Boost.gif
    image_path: /Gifs/Postal/Boost.gif

lateralForce:
  - url: /Gifs/Postal/LateralForces.gif
    image_path: /Gifs/Postal/LateralForces.gif

packTrajectory_Laser:
  - url: /Gifs/Postal/PackageTrajectory1.gif
    image_path: /Gifs/Postal/PackageTrajectory1.gif
  - url: /Gifs/Postal/LaserShooting.gif
    image_path: /Gifs/Postal/LaserShooting.gif

newShooting:
  - url: /Gifs/Postal/NewShooting.gif
    image_path: /Gifs/Postal/NewShooting.gif
---
{% include video id="YL3SATmfDdM" provider="youtube" %}

- **Release**: April 2025  
- **Studio**: Pixel Parcel Productions  
- **Skill Focus**: Player Controls, Cameras, Game Systems, Audio.  
- **Developed In**: Unity  
- **Developed For**: 8 Months   

---

# Evolution of the Delivery Truck {#intro}
The final product of the delivery truck came after many iterations, adjustments, scrapping ideas, and entirely reworking systems.

## Initial Idea
I knew right from the get go that the truck was going to hover. We designed the game this way to create contrast between the pirates and the delivery truck. The first iteration of the truck was a simple block that could hover above the ground. The feeling I was aiming for were the speeder bikes from StarWars. The hovering was acting as intended, but I wouldn’t compare it to the speeder bikes… more like the slow bikes.

{% include gallery id="initialIdea" %}
{% include gallery id="initialWorld" %}

## Shooting!
The player was never going to leave the vehicle, so we decided to shoot packages at our unsuspecting customers instead! Nothing like a broken parcel! My first prototype of shooting was clunkly, the controls were WASD to move, arrow keys to aim the cannon, and spacebar to fire. Players could shoot packages or bullets through pressing tab and changing what gun they had mounted. It wasn’t great, but nothing is when you start!

{% include gallery id="shootingBullets" %}

{% include gallery id="shootingPackages" %}

## SICK FLIPS
The next feature to the vehicle I added was the ability to perform flips in the air. Completing backflips or frontflips would accumulate extra points exponentially (for consecutive flips) to add to your final score.
We received really good feedback during our testing sessions on this feature, something that players still comment on every time they play!

{% include gallery id="flips" %}


## More Speed Please!
As our map was expanding, testers began to comment on how long it would take to traverse the length of the map. We did some testing and realized it took roughly 2 minutes to get from one side to the other. If a player was assigned a delivery on each corner of the map, it would take them upwards of 6 minutes to complete these deliveries. The game was only meant to last 10 minutes so this issue needed to be addressed immediately.

To solve the made two changes: 
1. I increased the speed, simple enough right? Wrong, traversing the map was a lot faster now, however, testers were still complaining about moving too slow. To remedy this, I...
2. Implented a booster. The booster had a cooldown so players couldn't spam it, however this event gave players more options to move around the map now.

{% include gallery id="moreSpeed" %}


## Lateral Forces!
The new changes to speed presented some new problems. The delivery truck was falling off the road constantly. Testers were spending more time getting back onto the roads than they did driving on them. Additionally, as plots of land became more populated with houses and trees, the only place players could drive were the roads. To fix this, I added lateral forces to the vehicle. The lateral forces that tires exert with the ground are what allows a car to turn, and the force is calculated using multiple variables and constants. With that said, I would just use speed along with left and right input to affect how sharp we can turn. With these new lateral forces, the vehicle now begins to slow down when we make sharp turns, which in turn (pun), allows for tighter turning (i.e better handling).

Now you’re probably asking “How is there friction with the ground if this is a hovering vehicle?” Great question! Sometimes not everything needs to be realistic, especially if the unrealistic version feels better!

{% include gallery id="lateralForce" %}


## Cooler Shooting
The major change implented here was how the player aims. Changing the direction of the cannon to always point towards the mouse cursor made aiming so much easier and shooting the Porch Pirates became much easier to do while driving. I also added some lasers coming out of the barrels and particle effects to the bullets when we fired them. It looks cool now!

The package cannon would now shoot the packages in a smooth arc towards their target. Looks great!

{% include gallery id="packTrajectory_Laser" %}

## System Rework
Christmas break was coming up, and so was our development checkpoint (set in mid December). Due to mismanaging our time and deadlines, the state of our game wasn’t anywhere near where we wanted it to be. For the player mechanics, testers were still complaining about poor handling, buggy shooting, and the lack of intuitive controls. Our team headed into the 2024 Christmas break knowing we needed to bounce back when we returned in 2025.

Over the break I took it upon myself to learn the physics behind driving. I created multiple prototypes and prepared myself to overhaul the entire driving system come January 2025. Once we returned, that’s exactly what I did. One goal I was set on achieving was creating a customizable system, something where I could tweak constants very easily. I wanted to speed up the development process. I had achieved this system by the second week back after break. The vehicle wasn’t driving great, but because of the new system, understanding what needed to be adjusted was easier than ever.

{% include video id="sl9eacqvoAc" provider="youtube" %}

## Drifting
I always intended on eventually adding drifting to the delivery truck, and with this new system, I could! I added the ability to oversteer and understeer during the drift. Additionally, drifting would charge a boost that would be exerted once the drift was completed.
{% include video id="MShEycVbJ9g" provider="youtube" %}

## Cannon Changes
Once driving required less focus to stay on the roads, we found that testers were eliminating pirates with too much ease. We wanted the player to be afraid of the pirates and to try to avoid when possible. To achieve this, we removed the cannons that shot deadly projectiles entirely. Now the player only had nothing to protect themselves, these porch pirates were becoming more of a threat!

Along with this removal, I added an aiming state to the cannon. Aiming in would change the camera into a first person perspective behind the cannon. Aiming now felt more like a minigame, giving the player a short break from driving. Most importantly, the aiming became intuitive.

{% include gallery id="newShooting" %}

## Final Tweaking!
All mechanics were implemented at this point. All I needed to do was adjust values.
I made the truck faster, allowed it to turn while stationary, added more lateral slip, and countless other small adjustments to get to where it is now.  

{% include video id="5QKcaePiu8Q" provider="youtube" %}

One major change to affect the driving wasn't done on the truck's code at all, but in physics bodies of every object the truck could hit. This major change was to the physics material placed on the objects. The default material reacts to collisions by absorbing forces and creating lots of friction which brings any object that touches it to a full stop very quickly. I changed these values so the truck would slip off of the buildings and bounce off them upon collision. This allowed players to keep a larger portion of their speed if they fell off the road.

## Audio and Visual Effects
Functionally, the delivery truck was in its final state. It was time to emphasize all of its features using visuals and audio. I noticed a lot of complaints about the feel of the truck went away once the effects were added in. These queues confirmed to the player that their input was being received.

## Final Version
The top video is final version of the truck. In total this project lasted 8 months. The majority of my time went towards creating this truck, while the rest was split amongst the other areas I was in charge of. I learned so much (maybe too much for game development) about the physics behind all the moving parts that make up a vehicle. A special thanks to the playtesters and the other devs on this project that influenced and supported my development process!







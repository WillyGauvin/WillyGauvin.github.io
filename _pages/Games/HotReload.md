---
permalink: /Hot-Reload/
layout: single
author_profile: false
title: "Hot Reload"

sidebar:
  nav: "willyiam"

toc: true
toc_sticky: true

walking:
  - image_path: https://ik.imagekit.io/willgauvin/HotReload/Walking.gif?updatedAt=1785508936343

CommandBlockInteraction1:
  - image_path: https://ik.imagekit.io/willgauvin/HotReload/LookAt.gif?updatedAt=1785508934936
    alt: "Look At"
    title: "Look At"

  - image_path: https://ik.imagekit.io/willgauvin/HotReload/PickingUp.gif?updatedAt=1785508936317
    alt: "Picking Up"
    title: "Picking Up"

CommandBlockInteraction2:
  - image_path: https://ik.imagekit.io/willgauvin/HotReload/Throwing.gif?updatedAt=1785508935633
    alt: "Throw"
    title: "Throw"

  - image_path: https://ik.imagekit.io/willgauvin/HotReload/Dropping.gif?updatedAt=1785508934834
    alt: "Drop"
    title: "Drop"

CommandBlockInteraction3:
  - image_path: https://ik.imagekit.io/willgauvin/HotReload/Swapping.gif?updatedAt=1785508936399
    alt: "Swap"
    title: "Swap"
---

![image-center](/Photos/GameScreenShots/HotReload.png){: .align-center}

**[Play the game on itch!](https://willygauvin.itch.io/hotreload){:target="_blank"}**

# About the game
Hot Reload was my submission for the 2025 GMTK Game Jam. We had 96 hours to create a game based on the theme "Loop". **The game placed <u>90th</u> in creativity against <u>9654</u> entries.**

Hot Reload is a 3D puzzle adventure where you play as the operator of a robot companion. Rearrange command blocks within its looping execution track to solve challenges and navigate the environment. Use blocks found throughout the level to program your robot, but be careful: any commands left behind will repeat, sometimes with unintended consequences.

- **Release**: August 3rd 2025    
- **Skill Focus**: Gameplay programming, FMOD Audio Integration, Team management.  
- **Made in**: Unity  
- **Development Time**: 4 Days!  

I put together a team of 5 for this jam:
* [BirchTree](https://birchtree.itch.io/){:target="_blank"}: 3D Assets, visual effects, level design
* [Izaak Aidid](https://coolguy3267.itch.io/){:target="_blank"}: Gamestate programmer
* [Tristan Blaskowitz](https://tristanblaskowitz.itch.io/){:target="_blank"}: Sound and Music
* [Don-Tnowe](https://don-tnowe.itch.io/){:target="_blank"}: UI/Menus
* Will Gauvin: Gameplay programmer, audio programmer, team lead

# My contributions to the game:

## Character Controls
### Movement  
I wanted the movement for this game to feel snappy and be fairly simple, so I chose a simple position displacement method to move the player around. This allowed me to quickly finalize the movement and not have to deal with the overhead that comes with using physics-based movement in Unity.
![image-center](https://ik.imagekit.io/willgauvin/HotReload/Walking.gif?updatedAt=1785508936343){: .align-center}

### Command Block Interaction  
  Command Blocks were a core part of the game's main mechanic, they are the instructions that the robot uses to navigate the level. Blocks inherited from a custom interaction interface I created, which defined behaviors for looking at or away from the object, and interacting with them.
  * Looking At/Away 
![image-center](https://ik.imagekit.io/willgauvin/HotReload/LookAt.gif?updatedAt=1785508934936){: .align-center}
  * Picking up  
![image-center](https://ik.imagekit.io/willgauvin/HotReload/PickingUp.gif?updatedAt=1785508936317){: .align-center}
  * Throwing
![image-center](https://ik.imagekit.io/willgauvin/HotReload/Throwing.gif?updatedAt=1785508935633){: .align-center}
  * Dropping
![image-center](https://ik.imagekit.io/willgauvin/HotReload/Dropping.gif?updatedAt=1785508934834){: .align-center}
  * Swapping
![image-center](https://ik.imagekit.io/willgauvin/HotReload/Swapping.gif?updatedAt=1785508936399){: .align-center}

## Robot
### Conveyor Belt
The looping track in the robot's brain are made up of Conveyor Belt objects. The belts were programmed as nodes, each able to give reference to the next belt in line. Conveyor Belts also inherited from my custom interaction interface. You could place, pick up, and swap blocks from the belt.
  * Placing / Picking Up
![image-center](https://ik.imagekit.io/willgauvin/HotReload/BeltPlaceAndPickup.gif?updatedAt=1785508934321){: .align-center}
  * Swap
![image-center](https://ik.imagekit.io/willgauvin/HotReload/BeltSwap.gif?updatedAt=1785508935105){: .align-center}

### Input Reader  
The input reader is the brain of the robot, it travels to each conveyor belt, reads command blocks, and sends a command to the robot to execute.  
Playtesting revealed players were spending too much time waiting for the input reader to loop around to again, so I added the ability to speed it up.
* Normal Speed vs Sped up by Player
![image-center](https://ik.imagekit.io/willgauvin/HotReload/BeltSpeed.gif?updatedAt=1785508933537){: .align-center}

### Movement
The robot was able to execute three types of commands: Move forward, rotate clockwise, rotate counter-clockwise.
![image-center](https://ik.imagekit.io/willgauvin/HotReload/RobotMovement.gif?updatedAt=1785508934979){: .align-center}

I also added a check to determine whether the robot would collide with anything when moving forward. In the case that it would hit something, a short animation (created using DOTween) would play along with the robot making an "ouch!" sound effect.
![image-center](https://ik.imagekit.io/willgauvin/HotReload/HittingWall.gif?updatedAt=1785508935379){: .align-center}

### Entering and Exiting the brain  
The player needed to enter and exit the brain to rearrange command blocks. I created two scripts: one attached to the robot to handle entering the brain, and another attached to the brain room to handle exiting.
* Player Entering/Exiting
![image-center](https://ik.imagekit.io/willgauvin/HotReload/EnteringAndExitingBrain.gif?updatedAt=1785508934699){: .align-center}

Command blocks were also able to be thrown in and out of the brain. Upon entry, thrown command blocks would have their inputs immediately processed and sent to the robot, after which they were placed onto the command track. This added a new way to create and solve puzzles in the game.
* Command Blocks Entering/Exiting
![image-center](https://ik.imagekit.io/willgauvin/HotReload/BlockEnteringAndExitingBrain.gif?updatedAt=1785508934413){: .align-center}

## Puzzle Elements
### Draw bridge / Pressure plate  
Both the player and robot were able to step onto pressure plates to raise and lower draw bridges. Pressure plates and draw bridges were programmed to accept multiple callers and receivers, giving designers more freedom when creating puzzles.
* Player Triggering Draw Bridge
![image-center](https://ik.imagekit.io/willgauvin/HotReload/PlayerDrawBridge.gif?updatedAt=1785508935991){: .align-center}
* Robot Triggering Draw Bridge
![image-center](https://ik.imagekit.io/willgauvin/HotReload/RobotDrawBridge.gif?updatedAt=1785508936027){: .align-center}

### Key & Gate  
Fairly simple mechanic, when a key is collected the gate correlated with said key unlocks.
![image-center](https://ik.imagekit.io/willgauvin/HotReload/KeyAndGate.gif?updatedAt=1785508936264){: .align-center}

### Command Block Spawners  
These were used to free up space on levels that required a large amounts of blocks to complete, but didn't have enough real estate to pre place them around the level.
![image-center](https://ik.imagekit.io/willgauvin/HotReload/Spawners.gif?updatedAt=1785508935969){: .align-center}
### Explosion Command Block  
This was a special type of block given to the player in later levels. Upon entry of the robot, the explosion block would travel to the center of the brain room and force all blocks off the conveyor belts.
![image-center](https://ik.imagekit.io/willgauvin/HotReload/ExplosionBlock.gif?updatedAt=1785508934937){: .align-center}

## Audio Integration (FMOD)
I had been wanting the opportunity to learn FMOD and this project was a great time to do so. Our Sound and Music designer, [Tristan Blaskowitz](https://tristanblaskowitz.itch.io/){:target="_blank"} would work in FMOD Studio and upload his banks to the projects repository, where I would then integrate them into the project.  
I did so by creating an Audio Manager class that was responsible for playing one-shots, creating and cleaning up instances for looping sounds (music, ambience, footsteps), and controlling said instances (changing parameters, strating/stopping).  
I also created a singleton class that stored the path to each sound in the bank, allowing me to reference the singleton instead of hard-coding or storing the path in every class needed.

The video below shows the result of using FMOD to dynamically change and alter music, ambience, and sound effects at runtime in our game. 
{% include video id="tC4EIRrdBrQ" provider="youtube" %}

## Final Cutscene
To wrap up the game, I created a short cutscene using Cinemachine and animation tracks. In the scene, we see the character you play as leaving by boat, while the robot welcomes a different character back at Level 1.  
I intended this cutscene to further drive the jams theme "Loop", hinting that multiple characters have guided the robot through these puzzles before, and more will come after you.

{% include video id="4xdlTSRv5_M" provider="youtube" %}
---





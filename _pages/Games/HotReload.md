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
  - url: /Gifs/HotReload/Walking_Med.gif
    image_path: /Gifs/HotReload/Walking.gif

CommandBlockInteraction1:
  - url: /Gifs/HotReload/LookAt.gif
    image_path: /Gifs/HotReload/LookAt.gif
    alt: "Look At"
    title: "Look At"

  - url: /Gifs/HotReload/PickingUp.gif
    image_path: /Gifs/HotReload/PickingUp.gif
    alt: "Picking Up"
    title: "Picking Up"

CommandBlockInteraction2:
  - url: /Gifs/HotReload/Throwing.gif
    image_path: /Gifs/HotReload/Throwing.gif
    alt: "Throw"
    title: "Throw"
    
  - url: /Gifs/HotReload/Dropping.gif
    image_path: /Gifs/HotReload/Dropping.gif
    alt: "Drop"
    title: "Drop"

CommandBlockInteraction3:
  - url: /Gifs/HotReload/Swapping.gif
    image_path: /Gifs/HotReload/Swapping.gif
    alt: "Swap"
    title: "Swap"
---

![image-center](/Photos/GameScreenShots/HotReload.png){: .align-center}

**[Play the game on itch!](https://willygauvin.itch.io/hotreload)**

# About the game
Hot Reload was my submission for the 2025 GMTK Game Jam. We had 96 hours to create a game based on the theme "Loop". **The game placed <u>90th</u> in creativity against <u>9654</u> entries.**

Hot Reload is a 3D puzzle adventure where you play as the operator of a robot companion. Rearrange command blocks within its looping execution track to solve challenges and navigate the environment. Use blocks found throughout the level to program your robot, but be careful: any commands left behind will repeat, sometimes with unintended consequences.

- **Release**: August 3rd 2025    
- **Skill Focus**: Gameplay programming, FMOD Audio Integration, Team management.  
- **Made in**: Unity  
- **Development Time**: 4 Days!  

I put together a team of 5 for this jam:
* [BirchTree](https://birchtree.itch.io/): 3D Assets, visual effects, level design
* [Izaak Aidid](https://coolguy3267.itch.io/): Gamestate programmer
* [Tristan Blaskowitz](https://tristanblaskowitz.itch.io/): Sound and Music
* [Don-Tnowe](https://don-tnowe.itch.io/): UI/Menus
* Will Gauvin: Gameplay programmer, audio programmer, team lead

# My contributions to the game:

## Character Controls
### Movement  
I wanted the movement for this game to feel snappy and be fairly simple, so I chose a simple position displacement method to move the player around. This allowed me to quickly finalize the movement and not have to deal with the overhead that comes with using physics-based movement in Unity.
![image-center](/Gifs/HotReload/Walking.gif){: .align-center}

### Command Block Interaction  
  Command Blocks were a core part of the game's main mechanic, they are the instructions that the robot uses to navigate the level. Blocks inherited from a custom interaction interface I created, which defined behaviors for looking at or away from the object, and interacting with them.
  * Looking At/Away 
![image-center](/Gifs/HotReload/LookAt.gif){: .align-center}
  * Picking up  
![image-center](/Gifs/HotReload/PickingUp.gif){: .align-center}
  * Throwing
![image-center](/Gifs/HotReload/Throwing.gif){: .align-center}
  * Dropping
![image-center](/Gifs/HotReload/Dropping.gif){: .align-center}
  * Swapping
![image-center](/Gifs/HotReload/Swapping.gif){: .align-center}

## Robot
### Conveyor Belt
The looping track in the robot's brain are made up of Conveyor Belt objects. The belts were programmed as nodes, each able to give reference to the next belt in line. Conveyor Belts also inherited from my custom interaction interface. You could place, pick up, and swap blocks from the belt.
  * Placing / Picking Up
![image-center](/Gifs/HotReload/BeltPlaceAndPickup.gif){: .align-center}
  * Swap
![image-center](/Gifs/HotReload/BeltSwap.gif){: .align-center}

### Input Reader  
The input reader is the brain of the robot, it travels to each conveyor belt, reads command blocks, and sends a command to the robot to execute.  
Playtesting revealed players were spending too much time waiting for the input reader to loop around to again, so I added the ability to speed it up.
* Normal Speed vs Sped up by Player
![image-center](/Gifs/HotReload/BeltSpeed.gif){: .align-center}

### Movement
The robot was able to execute three types of commands: Move forward, rotate clockwise, rotate counter-clockwise.
![image-center](/Gifs/HotReload/RobotMovement.gif){: .align-center}

I also added a check to determine whether the robot would collide with anything when moving forward. In the case that it would hit something, a short animation (created using DOTween) would play along with the robot making an "ouch!" sound effect.
![image-center](/Gifs/HotReload/HittingWall.gif){: .align-center}

### Entering and Exiting the brain  
The player needed to enter and exit the brain to rearrange command blocks. I created two scripts: one attached to the robot to handle entering the brain, and another attached to the brain room to handle exiting.
* Player Entering/Exiting
![image-center](/Gifs/HotReload/EnteringAndExitingBrain.gif){: .align-center}

Command blocks were also able to be thrown in and out of the brain. Upon entry, thrown command blocks would have their inputs immediately processed and sent to the robot, after which they were placed onto the command track. This added a new way to create and solve puzzles in the game.
* Command Blocks Entering/Exiting
![image-center](/Gifs/HotReload/BlockEnteringAndExitingBrain.gif){: .align-center}

## Puzzle Elements
### Draw bridge / Pressure plate  
Both the player and robot were able to step onto pressure plates to raise and lower draw bridges. Pressure plates and draw bridges were programmed to accept multiple callers and receivers, giving designers more freedom when creating puzzles.
* Player Triggering Draw Bridge
![image-center](/Gifs/HotReload/PlayerDrawBridge.gif){: .align-center}
* Robot Triggering Draw Bridge
![image-center](/Gifs/HotReload/RobotDrawBridge.gif){: .align-center}

### Key & Gate  
Fairly simple mechanic, when a key is collected the gate correlated with said key unlocks.
![image-center](/Gifs/HotReload/KeyAndGate.gif){: .align-center}

### Command Block Spawners  
These were used to free up space on levels that required a large amounts of blocks to complete, but didn't have enough real estate to pre place them around the level.
![image-center](/Gifs/HotReload/Spawners.gif){: .align-center}
### Explosion Command Block  
This was a special type of block given to the player in later levels. Upon entry of the robot, the explosion block would travel to the center of the brain room and force all blocks off the conveyor belts.
![image-center](/Gifs/HotReload/ExplosionBlock.gif){: .align-center}

## Audio Integration (FMOD)
I had been wanting the opportunity to learn FMOD and this project was a great time to do so. Our Sound and Music designer, [Tristan Blaskowitz](https://tristanblaskowitz.itch.io/) would work in FMOD Studio and upload his banks to the projects repository, where I would then integrate them into the project.  
I did so by creating an Audio Manager class that was responsible for playing one-shots, creating and cleaning up instances for looping sounds (music, ambience, footsteps), and controlling said instances (changing parameters, strating/stopping).  
I also created a singleton class that stored the path to each sound in the bank, allowing me to reference the singleton instead of hard-coding or storing the path in every class needed.

The video below shows the result of using FMOD to dynamically change and alter music, ambience, and sound effects at runtime in our game. 
{% include video id="tC4EIRrdBrQ" provider="youtube" %}

## Final Cutscene
To wrap up the game, I created a short cutscene using Cinemachine and animation tracks. In the scene, we see the character you play as leaving by boat, while the robot welcomes a different character back at Level 1.  
I intended this cutscene to further drive the jams theme "Loop", hinting that multiple characters have guided the robot through these puzzles before, and more will come after you.

{% include video id="4xdlTSRv5_M" provider="youtube" %}
---





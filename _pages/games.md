---
permalink: /games/
layout: single
author_profile: false
title: "Games"
toc: true
toc_label: "My Games"
toc_sticky: true
---

My interest in creating video games started in 2021. I've used multiple engiens to create them such as:

* Unreal Engine 5
* Unity
* Custom Engine (**created by me!**)
* GameDev2D (**Created by one of my professors**)

Here's all the game's I have created since 2021!

## Unreal Engine

### Dirty Dogs

Dirty Dogs is the most recent game I have created using Unreal Engine 5.  
This game was created in 4 months for a Mini-Capstone project that took place during my 4th semester in Game Development.  

In our group of 6, I took on the role of Networking the game.  During this time, I learned how to implement standard Server-Client architecture through proper replication, all hosted on a dedicated server through Steam.  

Countless hours were spent reading [Unreal's Network Compendium][Unreal Network Compendium]{:target="_blank"}!

### Super Mario Remake

This is my Super Mario reamke, my second game I created in Unreal Engine 5!  
I developed this remake independently in around 2 weeks.

Some key features include

* Shooting and Jumping
* Two types of Patrolling NPC Goombas:
  1. Regular Patroller
  2. Shooting Patroller (Player Detection using RayCasts)
* Togglable Blocks
  * Hitting a "Off" block with your head or shooting it toggles the collision boxes of blue blocks.
* Checkpoint flags
* Moving Platforms

{% include video id="994538487" provider="vimeo" %}

### Pong

This was my first time using Unreal Engine. Starting with a 2D game took off a lot of the pressure that three-dimensional physics brings to the table. I spent around a week making this.  

This is a Single Player game. You control the left paddle while the game controls the right.  

For my first time using Unreal Engine 5, it turned out pretty well.

{% include video id="994538462" provider="vimeo" %}

## Unity

### Librarian Simulator

In May of 2024 I took on a personal project and built a librarian simulator in Unity.

I worked independently on the backend of the game, implementing features such as:

* NPC's using Behaviour Tree's  
(A concept I learned while developing my [Roller Derby Game](#roller-derby))
* Interactable and placeable objects
* Inventory system
* Random Events
  * Noisy citizens
  * Book checkout requests
  * Book check in requests

Along with the backend development, I also worked on the front end with help from Sean Nichol; a friend of mine who is majoring in the art side of my college program.

### Roller Derby

Roller Derby was the first game I built inside of Unity.  
This game ties together two conepts I had recently learned: Behaviour Tree's and Flocking

## Custom Engine

Throughout my second year studying in Game Development I built a 3D game engine. Here are some of the concepts and features I had implemented during my time on this project:
* ECS Architecture
  * GameObjects to act as the Entities
  * Components for Lights, Physics, Rendering, and Transforms
  * Component Managers to house update systems for each component.
* Event Systems
* Scenes
* Light rendering
* Mesh File Loading
* Customizable Camera
  * Follow Cam
  * 1st/3rd Person
  * Orbit
* Multiple integrated libraries
  * bgfx
  * Box2D Physics
  * Jolt Physics
  * ImGUI

Here's a few games to show off the capabilties of the engine I created.

### Bat Maze
{% include video id="994538390" provider="vimeo" %}
This two player game showed off my newest addition of a follow camera. The follow camera was built to position itself at the average of each alive players position while keeping both players in frame with padding.

You can see this feature in action in **the video below**. When Player 2 dies, the camera focuses on just the player that is alive.
{% include video id="994538368" provider="vimeo" %}


This stage of the engine was entirally 2D and pre physics components. All bodies were simply assigned a 2D texture read through a JSON file reader that was integrated into the engine.

I also had recently integrated the IMGUI libary to help with debugging purposes as well as add some UI to the games I created.
{% include video id="994538402" provider="vimeo" %}


### Golf
This short demo of a mini golf game was to exhibit my newest addition to the engine, lighting! I learned to calcuate specular and diffuse reflections, attenuation (falloff), and then how to mix it all together to calculate the light color and level for each pixel in the scene based on the camera's position.

### Lunar Lander
My lunar lander game was created after I implented Box2D physics, an open source phsyics engine into my engine. the 3 main parts of the lander (2 engines, main body) each have their own rigidbody and collision box attached to simulate real physics and interactions with the terrain below. The terrain is randomly generated poly's with a handlefull of flat landing spots.

### Sokkoban
An early stage in the development of this engine, Sokkoban was recreated to help test a new virtual controller class as well as a sprite animator class.
{% include video id="994538478" provider="vimeo" %}

## GameDev2D
GameDev2D is an engine developed by professors in my program. It was used to introduce students to creating and using custom game engines. Here are a couple games I created while learning this engine.

### Asteroids
{% include video id="994538352" provider="vimeo" %}
### Brick Breaker
{% include video id="994538420" provider="vimeo" %}


[Unreal Network Compendium]: https://cedric-neukirchen.net/docs/category/multiplayer-network-compendium/

---
permalink: /Custom-Engine/
layout: single
author_profile: false
title: "Custom Game Engine"

toc: true
toc_sticky: true

sidebar:
  nav: "willyiam"

Games2:
  - image_path: Photos/GameScreenShots/BatMaze.png
    title: "Bat Maze"
    url: "/Bat-Maze/"
    btn_label: "Bat Maze"
    btn_class: "btn--danger"

  - image_path: Photos/GameScreenShots/LunarLander.png
    title: "Lunar Lander"
    url: "/Lunar-Lander/"
    btn_label: "Lunar Lander"
    btn_class: "btn--danger"


Games3:
  - image_path: Photos/GameScreenShots/3DGolf.png
    title: "3D Golf"
    url: "/3D-Golf/"
    btn_label: "3D Golf"
    btn_class: "btn--warning"

  - image_path: Photos/GameScreenShots/Sokoban.png
    title: "Sokoban"
    url: "/Sokoban/"
    btn_label: "Sokoban"
    btn_class: "btn--warning"
---
- **Project Life Time**: September 2023 - April 2024
- **Skill Focus**: Engine Architecture, Resource Management, Real-Time rendering.
- **Technologies Used**: C++, OpenGL, IMGUI, Box2D, JoltPhysics.

---

# Overview
This engine is a custom-built game development framework written in C++, created to explore the fundamentals of engine architecture, resource management, and real-time rendering. The engine features a modular, extensible core and uses OpenGL for rendering with basic shader-based lighting. This project was both a technical challenge and a learning opportunity, especially in graphics programming and system design.

# What I Learned
Building this engine helped me:
- Understand how different systems in a game engine interact
- Manage memory and resources more efficiently
- Get hands-on with OpenGL and shaders
- Improve my ability to design flexible, reusable systems.


# Key Features
## Modular Engine Core
At the heart of the engine is a flexible FWCore system that manages initialization, the main update loop, and rendering. By decoupling these responsibilities, the system is easy to expand with new subsystems like input, audio, or physics.

## Efficient Resource Management
A centralized resource loader handles all textures, models, and shaders. This prevents redundant memory usage and speeds up asset access at runtime, a key optimization in larger projects.

## Component-Based Architecture
Game objects are built using simple components (like transforms or mesh renderers), allowing for reusable behavior and clean separation of logic. This makes gameplay systems easier to build and test independently.

## OpenGL Rendering with Shaders
The engine uses OpenGL to handle rendering. While built with learning in mind, it includes:
- Vertex and fragment shaders for basic lighting
- Geometry submission using VBOs
- A customizable render loop

This gave me practical experience working with GPU-side operations and the modern graphics pipeline.

## Physics Engine Integration
The engine includes support for both Box2D and Jolt Physics, integrated through a custom PhysicsComponent. This component allows users to choose between 2D and 3D physics systems depending on the needs of the game object. The abstraction ensures that the physics logic is decoupled from other engine systems, enabling easy testing and future expansion. Some of its features include:
- Runtime selection of physics engine (Box2D or Jolt)
- Shared interface for physics behaviors (e.g., forces, collisions)
- Modular structure that keeps physics logic independent from rendering and game logic

This dual-integration approach provided valuable experience working with third-party libraries, setting up physics worlds, and synchronizing transforms between physics bodies and visual representations.

# Games built
Checkout the games I built using this engine.
{% include feature_row id="Games2"%}

{% include feature_row id="Games3"%}


# Download the repository
**[Download the repository here](https://github.com/WillyGauvin/GameEngine){:target="_blank"}**
---
permalink: /Risk-It-For-Biscuit/
layout: single
author_profile: false
title: "Risk It For Biscuit"

sidebar:
  nav: "willyiam"

toc: true
toc_sticky: true
---

![image-center](/Photos/GameScreenShots/RiskItForBiscuit.png){: .align-center}

**[Play the game on itch!](https://willygauvin.itch.io/risk-it-for-biscuit){:target="_blank"}**

# About the game
Risk It For Biscuit was my submission for Brackeys 2025.2 Game Jam. I led a team of 8 to create a game in 7 days based on the theme "Risk It For The Biscuit".

Risk It For Biscuit is a strategic dock diving game where you play as a fearless pup trying to save your buddy Biscuit from the crushing debt he owes to the Italian Dog Mafia.

Build and arrange floating obstacles to set up high-scoring dives, chaining tricks for massive payouts. Train with expert coaches to boost your stats and unlock new aerial moves. “Risk it” and take out high-interest Mafia loans to invest in better gear, but remember, every loan pushes you deeper into dangerous waters.

Can you out-dive the debt and save Biscuit before the Mafia sends him to the farm?

- **Release**: August 31st 2025
- **Skill Focus**: Team Lead, Gameplay Systems Programming, FMOD Audio Integration.
- **Made in**: Unity  
- **Development Time**: 7 Days!
  
  
# My contributions to the game:

## Shop System

The progression in Risk It For Biscuit is built around several interconnected shops and upgrade systems. Each system is powered by ScriptableObjects, which let me separate data from logic and keep player choices persistent across different scenes.

### Debt Shop
The Debt Shop allows players to take out and pay back high-interest loans from the Dog Mafia. These loans are stored in ScriptableObjects so the player’s debt balance carries seamlessly from the shop scene into the gameplay scene. This makes every financial decision long-lasting, not just a one-off menu choice.

![image-center](/Gifs/RiskItForBiscuit/Shops/DebtShop.gif){: .align-center}


* Each loan is stored in a list held by a master ScriptableObject
* This allows for the player's debt balance to be persistent across scenes.
* The master ScriptableObject applies interest to each loan at the end of every day.
* This system makes every financial decision long-lasting and not just a one-off menu choice.

### Obstacle Shop
In the Obstacle Shop, players can buy floating obstacles to use in dives to earn more score.

![image-center](/Gifs/RiskItForBiscuit/Shops/ObstacleShopInteraction.gif){: .align-center}

* Each obstacle’s cost and price-scaling are stored in a ScriptableObject list.
* When the shop loads, I create a runtime clone of that data, so prices and purchases can change without altering the original asset.
* This means players can leave the shop, dive, and return later, and their obstacle prices will still reflect their past choices.

### Trainer Shop
Trainers are built using the same ScriptableObject approach:

![image-center](/Gifs/RiskItForBiscuit/Shops/TrainerShopInteraction.gif){: .align-center}

* Each trainer stores its icon, name, price, permanent upgrades, and special perk in a TrainerDataSO.
* When a trainer is purchased, the data gets flagged as unlocked in the runtime copy.
* If equipped, the trainer’s activated upgrade is passed to the UpgradeManager, which applies it globally.

This keeps trainer unlocks and perks consistent across scenes without relying on save files or PlayerPrefs.

### Upgrades

Upgrades are also ScriptableObjects (UpgradeDataSO) and can represent anything from stat boosts to ability unlocks to environmental modifiers.  
The Upgrade Manager handles them by:
* Tracking all unlocked upgrades in a runtime list (UpgradeListSO)
* Applying them every time a new scene loads. This allows us to not need the infrastructure to be able to save every script affected by upgrades. Instead scripts affected will be called upon by Upgrade Manager during the initialization phase of the scripts lifetime.
For example, upon loading the dock scene:
  * If you bought a jump height upgrade in the shop, the UpgradeManager calls upon the Dog script to increase this stat.
  * If you bought a dock upgrade, the UpgradeManager calls upon the DockManager to increase the size of the dock.

![image-center](/Gifs/RiskItForBiscuit/Shops/DockSizeIncrease.gif){: .align-center}


### All Together

By using ScriptableObjects as the single source of truth, all of these systems (Debt, Obstacle Shop, Trainer Shop, and Upgrades) talk to each other without needing complex save/load systems.
* Debt Shop: changes your available money and debt.
* Obstacle Shop: updates obstacle prices and availability.
* Trainer Shop: unlocks and equips trainers, applying their upgrades.
* Upgrade Manager: ensures all upgrades are active across every scene.

This approach makes the system modular, scalable, and persistent, while keeping data-driven design at its core. Adding a new trainer, obstacle, or upgrade doesn’t require new code, just creating a new ScriptableObject.

## Obstacle System

In my game, players can place obstacles on a grid-based map to influence gameplay. This system is designed to be intuitive for players while remaining highly modular and data-driven behind the scenes. It relies heavily on ScriptableObjects to store persistent data, allowing the state of the obstacles to survive scene changes without needing a full save/load system.

### Grid and Placement Logic
The world is divided into a grid where each cell can be occupied by an obstacle. 
![image-center](/Gifs/RiskItForBiscuit/BuildMode/GridSize.gif){: .align-center}

Each obstacle has a size and occupies multiple cells if necessary. 
![image-center](/Gifs/RiskItForBiscuit/BuildMode/ObstacleSize.gif){: .align-center}

The system checks for valid placement to ensure obstacles don’t overlap and respect any allowed/blocked rows.
![image-center](/Gifs/RiskItForBiscuit/BuildMode/validAndInvalidPlacement.gif){: .align-center}

### Obstacle Inventory and Shop Integration
Obstacles are stored in an inventory with counts for each type. Players can acquire obstacles via the Obstacle Shop, which uses ScriptableObjects to save which obstacles are available and their prices.  
Placing an obstacle automatically reduces its count in the inventory, and removing it adds it back.
![image-center](/Gifs/RiskItForBiscuit/Shops/ObstacleShopInteraction.gif){: .align-center}

### Visual Feedback
The system uses a PreviewSystem to show a ghosted version of the obstacle before placement. It changes color to indicate whether the placement is valid (white) or invalid (red). A separate cell indicator shows which grid cells will be occupied.

![image-center](/Gifs/RiskItForBiscuit/BuildMode/ghostObject.gif){: .align-center}


### Placement and Removal States
The system uses a state pattern (IBuildingState) to separate placement logic (PlacementState) from removal logic (RemovingState). This keeps the system modular and easy to extend with other build modes had I chosen to add them.  
**Placement State**
![image-center](/Gifs/RiskItForBiscuit/BuildMode/placingObstacles.gif){: .align-center}
**Removing State**
![image-center](/Gifs/RiskItForBiscuit/BuildMode/removingObstacles.gif){: .align-center}

### Object Management
ObjectPlacer handles spawning and destroying the actual GameObjects in the world, while GridData keeps a logical representation of their positions for validation and persistence. This ensures that the visual scene always matches the internal game state.

### Input Handling
ObstacleInputManager abstracts mouse input and grid selection. It includes UI detection to prevent placing obstacles when interacting with the UI, creating a smooth user experience.

### Persistent Data with ScriptableObjects
Both the obstacle inventory (ObstacleDataSO) and the object database (ObjectsDatabaseSO) are ScriptableObjects. This allows:
* Obstacles to retain their counts between scenes.
* The grid state to persist while the player moves between menus and gameplay.
* Shops and placement systems to read from the same data source without duplicating information.

### Integration With Other Systems
This system ties directly into other parts of the game:
* Obstacle Shop: Controls which obstacles are available and at what price.
* Trainer Shop/Upgrades: Players can enhance gameplay mechanics that indirectly affect how they place or use obstacles.
* Audio Feedback: Placement and removal events trigger sound effects for tactile player feedback.

{% include figure popup=true image_path="/Photos/Diagrams/ObstaclePlacementDiagram.png" alt="Diagram" caption="Diagram of how the Obstacle System is interacted with" %}

### All Together
By combining ScriptableObjects for data persistence, a grid-based logical system for placement validation, and a state-driven approach for handling placement and removal, the obstacle system is both flexible and robust. Players always see a responsive, intuitive interface, and the game keeps track of every object without manual scene management or complex save systems.

## FMOD Audio
For the FMOD audio integration of this project, I reused the code from my previous project Hot Reload. This is a simple class that uses the singleton pattern to allow audio to be played, stopped, and changed from any other class. Additionally, it was set up to keep music playing as the scene transitioned to keep to players immersed.
Tracks were created by [Tristan Blaskowitz](https://tristanblaskowitz.itch.io/){:target="_blank"} to match the atmosphere of each shop.

{% include video id="pDZKfQrpe3M" provider="youtube" %}

---





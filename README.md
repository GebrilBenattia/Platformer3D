# Platforner UE5
The goal of the project is to develop a 3D platformer coded in blueprint in Unreal Engine 5.

# Looks of the game
* ![Screenshot](https://cdn.discordapp.com/attachments/1020661630700355676/1166319383472259163/Capture_decran_2023-10-24_121615.png?ex=6639ff92&is=6638ae12&hm=8a470e10c5f6dfbfbc1297257893642e3674b89af0840edd5ad17607a45df623&)

## Summary
* [Inputs](#inputs)
* [Architectury](#architectury)
* [Features](#features)


## Inputs
-Look: Mouse / Gamepad Right stick

-Move: ZQSD / WASD / Gamepad Left stick

-Jump: space bar / Gamepad A button

-Run: Left shift / Gamepad Right trigger

-Crouch: Left CTRL / Right CTRL / Gamepad Left trigger

-Interact: E / Gamepad X button


## Architectury
<pre>   
├── Assets
|   ├── MyAssets 
|   |   ├── Materials ...
|   |   ├── StaticMesh ...
|   |   ├── Textures ...
|   |   └── VFX ...
|   |
|   ├── CartoonWaterShader ...
|   ├── DreamscapeSeries1 ...
|   ├── DreamscapeSeries2 ...
|   ├── StarterContent ...
|   ├── UndeadPack ...
|   └── LearnKit ...
|
├── Blueprint 
|   ├── Enemy 
|   |   ├── BP_Enemy 
|   |   ├── BP_NavLinkProxy_Test 
|   |   ├── BP_NavLinkReached 
|   |   └── Enemy_PatrolPathPoint 
|   |
|   ├── LevelBlueprint 
|   |   ├── Curve
|   |   |   └── CF_ImpulseScaleFromDist
|   |   |  
|   |   ├── BP_Bumper 
|   |   ├── BP_CheckPoint 
|   |   ├── BP_Door 
|   |   ├── BP_Heart 
|   |   ├── BP_Key 
|   |   ├── BP_Killzone 
|   |   ├── BP_Obstacle 
|   |   ├── BP_Platform 
|   |   ├── BP_SpikeTrap 
|   |   └── BP_SplineMesh 
|   |
|   ├── PlayerCharacter
|   |   ├── ControlRig
|   |   |   └── CR_PlayerCharacter_IKFoot
|   |   |  
|   |   ├── Input
|   |   |   ├── Actions
|   |   |   |   ├── IA_Crouch
|   |   |   |   ├── IA_Interact
|   |   |   |   ├── IA_Jump
|   |   |   |   ├── IA_Look
|   |   |   |   ├── IA_Move
|   |   |   |   └── IA_Run
|   |   |   |
|   |   |   └── IMC_Player
|   |   |  
|   |   ├── BP_LastSeenIndicator 
|   |   ├── BP_PlayerCharacter
|   |   ├── BP_PlayerGameMode 
|   |   ├── BPA_LastSeenPos 
|   |   └── BPI_Character 
|   |
|   └── Other 
|       ├── BP_MacroLibrary
|       └── BP_Interactable
|   
├── HUD 
|   ├── GameHUD
|   └── WBP_PlayerHUD
|
├── Level
|   ├── Map_Game
|   |   └── Map_Game
|   |
|   └── Map_Test
|       ├── Map_Test_Gebril
|       └── Map_Test_Lenny
|
└── PhysMats
    ├── PM_Dirt
    └── PM_Grass
</pre>


## Features
### Player
- Additional movements: The player can move, run, jump, crouch and interact
- Interaction: Whene the player interacts, he adds impulse into physical objects, accompanied by a particle effect
- Inverse Kinematic: In the animation blend space, we add inverse kinematic to set the position of the feet on the surface of the ground
- Surface Detection: The player detect the type of the surface when he walk, with physical materials (it can be used to play different sounds or VFX) 

### Enemies
- Type of enemies: We have two differents enemies (one with one life and another with two life and who can heal himself)
- Enemy Patrolling: Each enemies can have a random patrolling or can follow a path
- Enemy animation: The enemy plays different animations depending on the enemy's current behavior
- Player Snapshot: When an enemy detect the player, a snapshot of this last is created in the game 

### Other Featers
- Base Features: Bumper / Heart / Killzone / Platform / Traps
- Additional features: CheckPoint / Door / Key / Obstacle / SplineMesh

# Session 1 - Introduction to Godot

## Agenda

1. **[Godot Now](#godot-now)**
2. **[Nodes and Scenes](#nodes-and-scenes)**
3. **[Scene Tree](#scene-tree)**
4. **[Handling Input](#handling-input)**
5. **[Task](#Task)**
6. **[References](#references)**

## Godot Now

- How to Create project in Godot
- Quick look inside in:
  - Scene editor
  - Script editor
  - Inspector

## Nodes and Scenes

- Identify Nodes and Scenes:

  - **`Nodes`** are the fundamental building blocks in Godot. They are objects that can perform a variety of specialized functions. Each node can contain multiple child nodes, forming a tree structure.
  - **`Scenes`** are collections of nodes that can be saved and reused.

- How to use nodes

- Some Nodes

```
Node2D: Basic Node of 2D
|
├── Sprite2D: For displaying images
├── Area2D: For collision detection
├── Camera2D: For controlling the game view
└── CollisionShape2D: Defines collision areas
```

## Scene Tree

- The Scene Tree is the hierarchical organization of nodes in your game. It defines how nodes relate to each other in parent-child relationships. This hierarchy determines:

  - How nodes inherit transformations
  - The order of processing
  - How signals and groups work
  - Scene instancing and organization

- functions:
  | Function | Description | When It's Called |
  |----------|-------------|------------------|
  | `_init()` | Constructor | Object creation |
  | `_enter_tree()` | Setup | Node enters scene tree |
  | `_ready()` | Initialization | All children are ready |
  | `_process()` | Game loop | Every frame |

### HandsOn

Make playable character using the nodes we saw, and using the order of scene tree

## Handling Input

- What is Input?
- How to define new Inputs?
- Using the defined Inputs

## Task

1. Create a new scene with Node2D as root
2. Add Sprite2D for visuals
3. Add CollisionShape2D for physics
4. Implement basic movement controls (define new inputs and use it)

## References

- **[Official Godot Documentation](https://docs.godotengine.org/)**
- **[Godot Community Hub](https://godotengine.org/community/)**
- **[Brackeys - How to make 2d Game with Godot(Nodes & Scenes)](https://youtu.be/LOhfqjmasi0?si=0M95npbsypR-ebCT&t=332) (from 5:32 to 16:56)**
- **[Brackeys - How to make 2d Game with Godot(Input Handling)](https://youtu.be/LOhfqjmasi0?si=0M95npbsypR-ebCT&t=3275) (from 54:35 to 56:09)**

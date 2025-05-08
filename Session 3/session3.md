# Session 3 - Physics, Tilemaps, and Instantiation

## Agenda

1. **[Physics System](#physics-system)**
2. **[Tilemaps](#tilemaps)**
3. **[Hands-on Exercise](#hands-on-exercise)**
4. **[Instantiation](#instantiation)**
5. **[References](#references)**

## Physics System

### 1. Physics Bodies

1. **Area2D**

   - Detect overlapping bodies
   - No physical response
   - Used for triggers and detection zones

2. **StaticBody2D**

   - Immovable objects
   - Used for platforms, walls
   - No physics simulation

3. **RigidBody2D**

   - Full physics simulation
   - Affected by gravity
   - Responds to collisions

4. **CharacterBody2D**
   - Controlled physics body
   - Custom movement logic
   - Best for player characters

### 2. Physics Process

```gdscript
func _physics_process(delta):
    # Runs at fixed time steps (default: 60 times per second)
    # delta is constant (typically 1/60)
    velocity = calculate_movement()
    move_and_slide()
```

#### Process vs Physics Process

| Function             | Usage              | Description                              |
| -------------------- | ------------------ | ---------------------------------------- |
| `_process()`         | Frame-dependent    | Runs as fast as possible, variable delta |
| `_physics_process()` | Physics simulation | Fixed timestep, consistent delta         |

#### When to Use Each

| Use Case            | Best Choice         | Why?                                |
| ------------------- | ------------------- | ----------------------------------- |
| Player Movement     | \_physics_process() | Movement should sync with physics.  |
| Collision Detection | \_physics_process() | Detect collisions reliably.         |
| Gravity and Jumping | \_physics_process() | Gravity is part of physics.         |
| UI Animations       | \_process()         | UI doesn't rely on physics updates. |
| Camera Follow       | \_process()         | Smooth motion, frame-dependent.     |
| Mouse Tracking      | \_process()         | Needs to track continuously.        |
| Smooth Animations   | \_process()         | Interpolates smoothly over frames.  |

### 3. Physics Materials

- **Friction**: Resistance between surfaces, higher on rough surfaces
- **Bounce**: Restitution coefficient, lower on absorbent materials

#### **Properties**:

```gdscript
# Physics material properties
physics_material_override = PhysicsMaterial.new()
physics_material_override.friction = 0.5
physics_material_override.bounce = 0.6
```

### 4. Layers and Masks

- **Collision Layers**: Define what an object is
- **Collision Masks**: Define what an object interacts with

```gdscript
# Setting up layers and masks
collision_layer = 1  # Layer 1
collision_mask = 2   # Will interact with layer 2
```

## Tilemaps

### Understanding Tilemaps

- Grid-based level design
- Efficient memory usage
- Quick level creation

### Working with Tilemaps

1. Create TileMap node
2. Import tileset
3. Configure tile properties:
   - Collision shapes
   - Navigation areas
   - Occlusion areas

## Hands-on Exercise

### **Task**: Create a Tilemap

> You can find the complete project in [`session 3 project.zip`](session%203%20project.zip).

1. **Add a TileMap**:
   - Create a new scene and add a `TileMap` node.
2. **Set Up Tileset**:
   - In the `TileMap` properties, create a new `TileSet`.
   - Import your tile textures.
3. **Add Collision**:
   - Assign collision shapes to tiles in the `TileSet` editor.
4. **Paint the Map**:
   - Use the `TileMap` editor to draw your level.

## Instantiation

### What is Instantiation?

- Creating objects at runtime
- Dynamic scene/node creation
- Memory-efficient object management

### Why Use Instantiation?

- Dynamic gameplay elements
- Resource management
- Procedural generation

### Implementation

```gdscript
# Loading and instantiating a scene
var bullet_scene = preload("res://Bullet.tscn")

func shoot():
    var bullet = bullet_scene.instantiate()
    add_child(bullet)
    bullet.global_position = global_position
    bullet.direction = get_shooting_direction()
```

## References

- **[Godot Physics Documentation](https://docs.godotengine.org/en/stable/tutorials/physics/)**
- **[Godot Tilemap Tutorial](https://docs.godotengine.org/en/stable/tutorials/2d/using_tilemaps.html)**
- **[Brackeys - How to make 2d Game with Godot(Tile Map)](https://youtu.be/LOhfqjmasi0?si=0M95npbsypR-ebCT&t=1018) (from 16:58 to 23:24)**
- **[Scene Instancing Guide](https://docs.godotengine.org/en/stable/getting_started/step_by_step/instancing.html)**

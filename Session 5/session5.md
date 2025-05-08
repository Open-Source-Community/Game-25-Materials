# Session 5 - Object Pooling and Global Scripts

## Agenda

1. **[Object Pooling](#object-pooling)**
2. **[Hands-on Exercise](#hands-on-exercise)**
3. **[Global Scripts](#global-scripts)**
4. **[References](#references)**

## Object Pooling

### What is Object Pooling?

Object pooling is a design pattern that pre-instantiates and reuses a fixed pool of objects rather than creating and destroying them on demand.

### Why Use Object Pooling?

- Improved performance
- Reduced memory fragmentation
- Better memory management
- Smoother gameplay experience

### When to Use Object Pooling?

- Frequently spawned objects (bullets, particles)
- Short-lived objects
- Resource-intensive instantiation
- Games with many dynamic objects

### How Object Pooling Works

#### Pool Structure

```gdscript
var pool: Array[Node] = []
var scene: PackedScene
var pool_size: int

func _ready():
    scene = preload("res://path_to_scene.tscn")  # Replace with your scene path
    pool_size = 10  # Set desired pool size
    initialize_pool()

func initialize_pool():
    for i in pool_size:
        var object = scene.instantiate()
        object.visible = false
        pool.append(object)
```

#### Object Lifecycle

1. **Spawn**

```gdscript
func spawn_object() -> Node:
    for object in pool:
        if not object.visible:
            object.visible = true
            object.position = get_spawn_position()
            return object
    return null  # Pool is exhausted
```

2. **Despawn**

```gdscript
func despawn_object(object: Node):
    object.visible = false
    # Reset object state
```

### Example: With vs Without Pooling

#### Without Pooling

```gdscript
# Expensive operations
func shoot():
    var bullet = bullet_scene.instantiate()
    add_child(bullet)
    # Bullet gets freed when it hits something or keep going out of bounds
```

#### With Pooling

```gdscript
func shoot():
    var bullet = bullet_pool.spawn_object()
    if bullet:
        bullet.reset()
        bullet.direction = get_shooting_direction()
```

### Advanced Object Pooling

#### Dynamic Pool Expansion

```gdscript
func expand_pool(additional_size: int): # additional_size can be change in future
    for i in additional_size:
        var object = scene.instantiate()
        object.visible = false
        pool.append(object)
```

#### Pool Cleanup

- Monitor object usage
- Remove unused objects
- Optimize pool size

#### Generic Pooling

Generic pooling is an advanced object pooling technique that allows for the management of multiple object pools in a centralized and reusable manner. Instead of creating separate pools for each object type, a generic pooling system dynamically handles pools for different object types using a shared structure.

#### Example Implementation

```gdscript
class_name GenericPool

var pools: Dictionary = {}

func get_pool(scene: PackedScene) -> ObjectPool:
    if not pools.has(scene):
        pools[scene] = ObjectPool.new(scene, 10)  # Initialize a new pool with a default size
    return pools[scene]
```

## Hands-on Exercise

Implement a pool specifically for bullets:

- Preload a bullet scene.
- Initialize a pool of bullets.
- Spawn bullets from the pool when the player shoots.
- Despawn bullets when they go out of bounds or hit a target.

## Global Scripts

### What are Global Scripts?

- Singleton pattern implementation in Godot
- Accessible from anywhere in the game
- Perfect for managing game state

### Why Use Global Scripts?

- Share data between scenes
- Manage global game state
- Handle persistent information
- Coordinate between different systems

### How to Create Global Scripts

1. Create a new script (e.g., `GameManager.gd`):

```gdscript
extends Node

var score: int = 0
var high_score: int = 0
var player_health: int = 100

func update_score(points: int):
    score += points
    if score > high_score:
        high_score = score

func reset_game():
    score = 0
    player_health = 100
```

2. Make it Global:
   - Project Settings → AutoLoad
   - Select script
   - Give it a name (e.g., "GameManager")

### Using Global Scripts

```gdscript
# In any other script
func collect_coin():
    GameManager.update_score(10)

func take_damage():
    GameManager.player_health -= 10
    if GameManager.player_health <= 0:
        GameManager.reset_game()
```

## References

- [Godot Documentation - AutoLoad](https://docs.godotengine.org/en/stable/tutorials/scripting/singletons_autoload.html)
- [Object Pooling](https://youtu.be/zyylMd6WEeQ?si=eQ_WGu2TB0k0pARd)

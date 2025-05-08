# Session 2 - GDScript and Animation

## Agenda

1. **[2D Perspectives](#2d-perspectives)**
2. **[GDScript Basics](#gdscript-basics)**
3. **[GDScript Hands-on ](#hands-on)**
4. **[Animation Systems](#animation-systems)**
5. **[Task](#task)**
6. **[References](#references)**

## 2D Perspectives

### Types of 2D Views

1. **Side-On (Side-Scrolling)**

   - Classic platformer view
   - Characters move left/right
   - Examples: Super Mario, Hollow Knight

2. **Top-Down**

   - Bird's eye view
   - Movement in all directions
   - Examples: Zelda, Hotline Miami

3. **Isometric**
   - 45-degree angle view
   - Combines 2D and 3D feel
   - Examples: Diablo, Age of Empires

## GDScript Basics

### Introduction to GDScript

- Godot's built-in scripting language
- Python-like syntax
- Object-oriented programming

### Creating and Attaching Scripts

1. Select a node
2. Click "Attach Script" button
3. Choose script location
4. Basic script template:

```gdscript
extends Node2D

func _ready():
    pass

func _process(delta):
    pass
```

### Variables and Types

```gdscript
var speed = 400           # Integer
var health = 100.5        # Float
var player_name = "Hero"  # String
var is_alive = true       # Boolean
@onready var sprite       # reference for node
@export var damage = 50   # Exported variable
```

### Control Flow

**`if`**

```gdscript
if health <= 0:
    game_over()
elif health < 50:
    show_warning()
else:
    continue_game()
```

**`loop`**

```gdscript
for i in range(5):
    spawn_enemy()
```

### Functions

```gdscript
func move_player(delta):
    var velocity = Vector2.ZERO
    if Input.is_action_pressed("ui_right"):
        velocity.x += speed
    return velocity
```

## Hands-on

1. Create a script and attach it to a node.
2. Define variables for speed, health, and player state.
3. Write a function to handle player movement using `if` statements.
4. Test the script by modifying variable values and observing the behavior.

## Animation Systems

### Understanding Sprite Sheets

- Collection of frames in a single image
- Organized in rows and columns
- Efficient for memory and loading

### Using AnimatedSprite2D

1. Create AnimatedSprite2D node
2. Import sprite sheet
3. Configure animation:
   - Set frame size
   - Set frame count
   - Adjust animation speed

### Creating Animations

1. Select AnimatedSprite2D node
2. Open Animation panel
3. Create new animations:
   - "idle"
   - "run"
   - "jump"

### Playing Animations

```gdscript
# Animation control
if is_on_floor():
    if direction == 0:
        animated_sprite.play("idle")
    else:
        animated_sprite.play("run")
else:
    animated_sprite.play("jump")
```

## Task

**With the given assets: [Brackeys Assets](https://brackeysgames.itch.io/brackeys-platformer-bundle)**

1. Create full animations for the player, including:

   - Idle animation
   - Running animation
   - Jumping animation

2. Implement player movement synchronized with the animations:

   - Ensure the player transitions smoothly between animations based on movement and state.
   - Test the animations on a platform to verify proper functionality.

3. Use GDScript to control the animations and player movement logic.

## References

- **[Godot Documentation - Animation](https://docs.godotengine.org/en/stable/tutorials/animation/)**
- **[Brackeys - How to make 2d Game with Godot(Animation)](https://youtu.be/LOhfqjmasi0?si=0M95npbsypR-ebCT&t=498) (from 8:18 to 12:10) and (from 57:46 to 1:00:14)**

- **[Godot Documentation - GDScript](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/)**
- **[Brackeys - How to make 2d Game with Godot(GDScript)](https://youtu.be/LOhfqjmasi0?si=0M95npbsypR-ebCT&t=830) (from 13:50 to 16:56)**

### Additional Content for GDScript

- **[Brackeys - GDScript Tutorial](https://youtu.be/e1zJS31tr88?si=Eft-RAzQKiuT6OzA)**

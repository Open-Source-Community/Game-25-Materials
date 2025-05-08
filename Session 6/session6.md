# Session 6 - Enemies and Save & Load

## Agenda

1. **[Enemy Types](#enemy-types)**
2. **[Save & Load System](#save-and-load-systems)**
3. **[References](#references)**

## Enemy Types

### 1. Stationary Enemy

- Simplest form of enemy
- Stays in one position
- Can perform actions like:
  - Shooting projectiles at fixed intervals
  - Activating when player is in range
  - Acting as a turret or defensive structure
- Example use cases: turrets, spike traps, laser emitters

### 2. Patrolling Enemy

- Moves between predetermined points
- Can use waypoints or fixed paths
- Often includes idle times at waypoints
- Can have different behaviors when spotting the player like chasing player

### 3. Chasing Enemy

- Actively pursues the player when detected
- Works with calculating the difference between the player and enemy or implements pathfinding (A\* or similar)
- Can have different behaviors when spotting the player like chasing player
- Can have different states (idle, chase, attack)

### 4. Obstacle-Aware Enemy

- Combines chasing behavior with obstacle avoidance
- Uses `Navigation2D` Node for creating meshes and `NavigationAgent2D` to handle pathfinding
- Can find alternate paths around obstacles
- More sophisticated AI behavior

### 5. Boss Enemy

- Complex enemy with multiple phases
- Usually combines multiple behavior patterns
- Often has special attacks and patterns
- May have weak points or specific conditions for damage

## Save & Load System

### Save Data in Godot

Godot provides several ways to save game data:

1. ConfigFile - For simple settings
2. JSON files - For structured data
3. Binary files - For complex or sensitive data

### Example Save/Load Implementation

### Example code (GDScript)

```gdscript
extends Node

const SAVE_FILE = "user://save_game.json"

func save_game():
    var save_data = {
        "player_position": player.position,
        "player_health": player.health
    }
    var save_file = FileAccess.open(SAVE_FILE, FileAccess.WRITE)
    save_file.store_string(JSON.stringify(save_data))

func load_game():
    if not FileAccess.file_exists(SAVE_FILE):
        return false

    var save_file = FileAccess.open(SAVE_FILE, FileAccess.READ)
    var save_data = JSON.parse_string(save_file.get_as_text())

    player.position = save_data.player_position
    player.health = save_data.player_health

    return true
```

## References

### Enemies

- **[Pathfinding Enemy](https://youtu.be/Lt9YdQ6Ztm4?si=yjlxFOorMGdL_Wo-)**
- **[Stationary Enemy](https://youtu.be/kBzV7vgdQfU?si=IE7iyLi63Zjladrx) (from 2:51 to 5:30 & from 10:35 to 13:51)**

### Save & Load

- **[Save & Load](https://youtu.be/lXO5Jt957BA?si=P5O0X1wtYQPLvMp7)**
- **[Advanced Save & Load](https://youtu.be/xG2GGniUa5o?si=ONxHw_fZdR4F_ApG)**

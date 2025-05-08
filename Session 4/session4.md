# Session 4 - Signals and Game Jam

## Agenda

1. **[Recap](#recap)**
2. **[Signals](#signals)**
3. **[Game Ideas](#game-ideas)**
4. **[Game Jam](#game-jam)**
5. **[References](#references)**

## Recap

- Movement
- Physics System
- Animation
- Tile Map
- Instantiation

## Signals

### Built-in Signals

- Pre-defined signals in nodes
- Example using Area2D:

```gdscript
func _ready():
    # Built-in signal connection
    $Area2D.body_entered.connect(_on_area_2d_body_entered)

func _on_area_2d_body_entered(body):
    if body.is_in_group("player"):
        collect_coin()
```

### Custom Signals

#### Defining Signals

```gdscript
# In Player.gd
signal health_changed(new_health)
signal score_updated(new_score)
signal game_over
```

#### Emitting Signals

```gdscript
# In Player.gd
func take_damage(amount):
    health -= amount
    emit_signal("health_changed", health)

    if health <= 0:
        emit_signal("game_over")
```

#### Connecting Signals

1. Using `@onready`:

```gdscript
# In UI.gd
@onready var player = $"../Player"

func _ready():
    player.health_changed.connect(_on_player_health_changed)

func _on_player_health_changed(new_health):
    update_health_bar(new_health)
```

2. Using References:

```gdscript
# In UI.gd
var player: Player

func _ready():
    player = get_node("../Player")
    player.score_updated.connect(_on_score_updated)

func _on_score_updated(new_score):
    update_score_label(new_score)
```

## Game Ideas

### Methods to Generate Ideas

1. **Start Simple and Expand**

   - Example: Ori and the Blind Forest
     - Started as a basic platformer
     - Added compelling story
     - Introduced enemy challenges
     - Enhanced mechanics (wall jump, etc.)

2. **Build from Personal Interests**

   - Example: Rebonbon Game
     - Inspired by music (Rebonbon)
     - Color mechanics
     - Unique gameplay elements

3. **Combine Different Concepts**

   - Example: Plants vs. Zombies
     - Tower defense + Humor
     - Unique character combinations
     - Unexpected genre mixing

4. **Research and Inspiration**
   - Play similar games
   - Study successful titles
   - Analyze game mechanics

## Game Jam

### What is a Game Jam?

- Time-limited game creation event
- Focus on creativity and completion
- Learning through constraints

### Game Jam Tips

1. **Planning**

   - Scope appropriately
   - Define core mechanics
   - Set realistic goals

2. **Development**

   - Start with prototype
   - Focus on core gameplay
   - Polish if time allows

3. **Testing**
   - Regular playtesting
   - Gather feedback
   - Iterate quickly

### Best Practices

1. Keep mechanics simple
2. Focus on one unique feature
3. Plan for the time constraint
4. Have backup plans
5. Don't forget basic necessities:
   - Main menu
   - Instructions
   - Basic UI
   - Sound effects

## References

- **[Godot Signal Documentation](https://docs.godotengine.org/en/stable/tutorials/scripting/signals.html)**
- **[Brackeys - GDScript Tutorial (Signals)](https://youtu.be/e1zJS31tr88?si=1pau_3r8o_I8Fquo&t=2437) (from 40:37 to 44:29)**

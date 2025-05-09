# Session 7 - Lighting, Shadows & Timers in Godot

## Agenda

1. **[2D Light](#2d-light)**
2. **[Shadows](#shadows)**
3. **[Timers](#timers)**
4. **[References](#references)**

## 2D Light

Godot offers several nodes for adding light effects in 2D games:

- `PointLight2D`: Emits light from a single point (e.g. torches, streetlamps).
- `DirectionalLight2D`: Affects the entire scene uniformly (e.g. sunlight).
- `CanvasModulate`: Alters the entire canvas color/tone.

### Setting up a PointLight2D

1. Add a `PointLight2D` node to your scene.
2. Assign a `GradientTexture2D` to the **Texture** property.
3. In the GradientTexture2D:
   - Set **fill** to `Radial`.
   - Reverse the white/black sliders.
   - Move the top-left point to the center.

### Customizing Light

- Adjust **Color**, **Energy (intensity)**, and **Scale** from the Inspector.
- Set **Blend Mode** to `Subtractive` to invert the light effect.

### DirectionalLight2D

- Affects the whole game scene.
- Simple settings: **Color**, **Energy**, **Scale**, and **Blend Mode**.

## Shadows

Godot implements 2D shadows using **Occluders**.

### Enabling Shadows

1. Enable **Shadows** in `PointLight2D`, .
2. `LightOccluder2D` **sibling** to texture or sprite.

### Custom Shadows

- Use `LightOccluder2D` to draw occlusion shapes manually.
- Create a new `OccluderPolygon2D` resource in the Inspector.
- Draw custom polygons for more precise shadow control.

## Timers

Used for:

- Countdowns
- Level/wave delays
- Ability cooldowns

### Timer Node

- **Wait Time**: Duration in seconds.
- **OneShot**: Whether it repeats.
- **Autostart**: Starts automatically.
- **Timeout Signal**: Triggers when the timer ends.

### GDScript Approach

Use Godot's scene tree to create and await a timer:

```gdscript
await get_tree().create_timer(2.0).timeout
# This line will pause execution for 2 seconds
``` 

## References

- **[Godot Documentation - 2D Lighrs and Shadows](https://docs.godotengine.org/en/stable/tutorials/2d/2d_lights_and_shadows.html)**
- **[2D Light and Shadows video](https://www.youtube.com/watch?v=AAPqEebFV-E)**

- **[Godot Documentation - Timers](https://docs.godotengine.org/en/stable/classes/class_timer.html)**
- **[Godot Node Timer video](https://www.youtube.com/watch?v=Zf6awHRr7bU)**
- **[Godot GDScript Timer video](https://www.youtube.com/watch?v=ZtKHZP2bRos)**



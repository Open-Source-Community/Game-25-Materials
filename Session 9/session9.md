# Session 9 - Introduction to 3D in Godot

## Agenda

1. **[Session Goals](#session-goals)**
2. **[3D vs 2D in Godot](#3d-vs-2d-in-godot)**
3. **[Navigating the 3D Editor](#navigating-the-3d-editor)**
4. **[Grey Boxing with CSG Nodes](#grey-boxing-with-csg-nodes)**
5. **[Lighting and Cameras](#lighting-and-cameras)**
6. **[Materials and Textures](#materials-and-textures)**
7. **[Basic Character Controller](#basic-character-controller)**
8. **[Resources](#resources)**

---

## Session Goals

- Understand 3D scene structure and navigation in Godot
- Learn the differences between 2D and 3D nodes
- Practice using the 3D editor and its controls
- Create simple levels using CSG nodes (grey boxing)
- Import and use 3D assets and materials
- Set up basic lighting and cameras
- Script a simple character controller
- Explore 3D physics basics

---

## 3D vs 2D in Godot

- Many nodes have both 2D and 3D versions:

  - `Area2D` → `Area3D`
  - `CollisionShape2D` → `CollisionShape3D`
  - `Camera2D` → `Camera3D`
  - `StaticBody2D` → `StaticBody3D`
  - `CharacterBody2D` → `CharacterBody3D`
  - `RayCast2D` → `RayCast3D`
  - `AudioStreamPlayer2D` → `AudioStreamPlayer3D`

- Some nodes are shared (e.g., `Timer`, `AnimationPlayer`).

---

## Navigating the 3D Editor

| Action                    | Description                    |
| ------------------------- | ------------------------------ |
| Middle Mouse Drag         | Rotate around object           |
| Shift + Middle Mouse Drag | Pan view                       |
| Right Mouse + WASDEQ      | Move camera freely (fly mode)  |
| Shift/Alt                 | Move faster/slower in fly mode |
| Scroll (with Right Mouse) | Change camera speed            |
| F                         | Focus selected object          |
| T                         | Toggle local/global transform  |

---

## Grey Boxing with CSG Nodes

Grey boxing is a fast way to block out a level using simple shapes before adding details. Use CSG nodes to create and combine shapes:

- **CSGBox, CSGCylinder, CSGSphere, CSGPolygon, CSGMesh, CSGTorus, CSGCombiner**

---

### Hands-on: Greyboxing a Simple Level

1. Create a new Godot project.
2. Add a new 3D scene and use CSG nodes (CSGBox, CSGCylinder, etc.) to block out a simple room or platform layout.
3. Experiment with combining, subtracting, and intersecting CSG shapes.
4. Try to create a basic level structure that a player could walk around in.

---

## Lighting and Cameras

Add a Camera3D and light to your scene or the default light (Sun), and the default environment.

---

## Materials and Textures

Materials define how a mesh looks. Key properties:

- **Albedo:** Color and transparency
- **Metallic:** How metallic the surface is
- **Roughness:** How rough or smooth
- **Ambient Occlusion:** Soft shadowing
- **Normal Map:** Adds surface detail
- **Emission:** Self-illumination

**ORM (Occlusion, Roughness, Metallic):** Used with ORMMaterial3D node.

---

## Basic Character Controller

- Decide: FPS or TPS? Camera follow or free?
- Add movement, jump, double jump, wall jump as needed.
- Make the camera move with mouse movement

---

### Hands-on: Basic Character Controller

1. Add a CharacterBody3D node to your scene.
2. Attach a Camera3D as a child of the character for a third-person or first-person view.
3. Script basic movement (WASD), jumping, and camera look with the mouse.
4. Test your controller in the greyboxed level.

> You can find the complete project in [`session-9-project.zip`](./session-9-project.zip).

---

## Resources

- **[Godot 3D Documentation](https://docs.godotengine.org/en/stable/tutorials/3d/index.html)**
- **[Brackeys - How to make 3D Game in Godot](https://youtu.be/ke5KpqcoiIU?si=crAQHQGP8ZxCE6m-) (from Start to 22:37)**

### Additional Resources

- **[GDQuest - Your First 3D Game From Zero in Godot 4](https://youtu.be/NJJNWGD25rg?si=zKpjcxa1bdRQWj5u&t=1550) (from 25:50 to 1:00:45)**

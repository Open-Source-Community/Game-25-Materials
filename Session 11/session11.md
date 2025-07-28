# Session 11 - Animation Player & Finite State Machines

## Agenda

1. **[Session Goals](#session-goals)**
2. **[Animation Player](#animation-player)**
3. **[Finite State Machines](#finite-state-machines)**
6. **[Resources](#resources)**

---

## Session Goals

- Learn about AnimationPlayer node in godot and difference between it and AnimatedSprite2D
- Learn and understand what Finite state machines are and why to use them
- Apply the session's topics in actual projects


## Animation Player

- `AnimationPlayer` is a node that is used for both 2D and 3D games, as it can access all types of nodes in Godot.
- `AnimationPlayer` allows for more complex animations, as it allows for more refined control over animation and manipulating values in any property for all nodes.
- So with this idea, animations are confined to only "frames" -  position, rotation, scale and more - can be part of the animations.

### Working with the `AnimationPlayer` node

- Once the `AnimationPlayer` node is added to the scene tree, we can access a new `Animation` tab in the lower part of the engine workspace.
- Here we can create and switch between animation, adjust animation length and properties, and add property tracks.
- To add a track, click on `+ Add Track` which will prompt to chose a node and then choose a property.
- This will create a new `Track` which we can add [`Keyframe`](#keyframes)s to.
- The `AnimationPlayer` will interpolae between the values of each keyframe in the track, making a smooth animation between them.
    - So for a position track with 2 keyframes (Vector2(0,0) and Vector2(50,0)) the AnimationPlayer will smoothly change the position of the node between these 2 points.  

#### Keyframes

- Keyframes are snapshots of a certain node's properties, which we can insert into the property track and the AnimationPlayer will intrpolate between the keyframes.
- Any node property that can be accessed from the insepctor can be inserted as a Keyframe
- Keyframess inserted can be clicked on to editted. Most importantly we can edit the `time` of the keyframe on the property track, and the value of the property the keyframe is holding.
- If 2 keyframes have a line white line between them, that indicates that the value of the property between the two keyframes is the same.
- To add a keyframe to the property track, either:
    - Right-click on the track and select `insert keyframe`, this will add a keyframe with the current value the property holds.
    - Or, while selecting the node from the scene-tree, click on the `key` icon next to each property to insert the current value as a keyframe.

---

## Finite State Machines (FSMs)

`Finite State Machines` are mathematical model of computation used to design and manage systems with a limited number of states.
In a less formal manner, FSMs are a way to organize a system's structure, by defining a set of "`states`", and these state can be changed from one another with certain actions called "`transitions`". In this design paradigm, each state will hold its own functionality and will not interfere with other states other than when transitioning states.

So, Finite State Machines consist of: 
- A finite number of `state`s
- An `initial`/starting `state`
- `Transitions` between `state`s
- `Input`/`Events` that cause a `state` `transition`

`Finite State Machines` are particularly useful to design code to be more modular.
For example, if we want to add a new feature to an already existing codebase, chances are we'll need to go and edit a lot of the code previously written, needing to retest the code and check for bugs in both old and new features.

In a codebase using FSMs, since each state holds it's own code, adding a new state will mean only adding it's functionality, and setting up the transitions between the new state and the old ones. This will guarantee that old code will not be changed and will stay correct, and makes adding new functionality much easier.

### Implementing Finite State Machines in Godot

First off, to start building our finite state machine, we'll need to define a state class in a script that won't be attached to any node. The state class will hold all base functions the states will use.

Then, for each state we have, we'll make a new node and attach a new script for that state. The script will extend from the state class and will override the defined fucntions. Each state will have it's own logic inside such as `enter`, `physics_update` and `handle_input` to name a few.

Lastly, there needs to be a Finite State Machine node and script, which will be responsible to see all available state and coordinate calling and transitioning between them. In the scene-tree the Finite State Machine will be of type `Node`, and will have the stat` nodes under it.

---

## References

- **[GD Quest - Finite State Machine (FSM) Article](https://www.gdquest.com/tutorial/godot/design-patterns/finite-state-machine/)**
- **[Chap.C Creates - State Machine](https://youtu.be/ExuzWQ077n4)**
- **[The ultimate introduction to Godot 4 - Animation Player](https://youtu.be/nAh_Kx5Zh5Q?t=20154) from 5:35:54 to 6:07:41**

### Additional Resources for Animation Player

- **[A Guide to the ANIMATION PLAYER - Animation Player](https://youtu.be/GMyw3eHDw7s)**

### Additional Resources for everything in Godot

- **[Godot Master Playlist](https://youtube.com/playlist?list=PLrT2fbyJrAIctd7zNUsdPakIllX2lhrzo&si=gzd-jxAP6R26IRuJ)**

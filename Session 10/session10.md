# Session 10 - 3D in Godot

## Agenda

1. **[Session Goals](#session-goals)**
2. **[3D Assets Recap](#3d-assets-recap)**
3. **[3D Collisions](#3d-collisions)**
4. **[Replacing Greyboxes](#replacing-greyboxes)**
5. **[Environment and Lighting](#environment-and-lighting)**
6. **[Resources](#resources)**

---

## Session Goals

- Recap 3D assets and learn different methods for importing/usage
- Set up collisions for 3D objects/assets in our game
- Be aware of difference betweeen adding manual collision shapes and generating from meshes
- Practice replacing greyboxes with actual level assets
- Explore and configure the WorldEnvironment node in the level scene
- Learn about different sky resource types and their differences
- Learn about Lighting nodes in 3D

---

## 3D Assets Recap

Depending on how you intend to use the assets in your game, there are multiple workflows to work with.

First off, when we drag an asset into the scene, it may appear as white, without any textures or materials.
- If the material resource isn't in the file-system:
    
    1. Double click the asset in the file-system.
    2. click the `Materials` tab and check if there's a material present, click it and make sure `Use External` is *not* enabled
    3. Click the `Actions` button and then choose `Extract Materials`, the click `Reimport`.

This should extract the material that the assets use into your file-system.

- If this doesn't work you can create a new material:
    1. Right click in yoru file system, choose `Create New` and then choose `Resource` 
    2. A Menu will popup, choose `StandardMaterial3D`
    3. Open the material from your file-system, and in the inspector, open the `Albedo` dropdown.
    4. Here you'll find you can choose a `Texture`, choose to `Quick Load` and you'll find all textures for the assets (assuming you have reimported them).
    5. Open the asset from the file-system and go to the `Materials` tab, click on the material file there and enable `Use External`.
    6. You will then be able to choose the `StandardMaterial3D` resource you made and have it work for this asset.

### Asset workflows 

- Method 1 (in case you won't need to edit or manipulate the asset itself or its components):
    1. Create a new 3D scene. (choose whatever node type you want; ex. StaticBody3D)
    2. Place you asset into the scene tree and save the scene.
    3. Use this scene as inplace of the asset.

- Method 2 (if you want to edit the asset or add extra functionality to it):
    1. Drop the asset into the scene.
    2. In the scene tree, click on the `scene icon` next to the asset.
    3. This will prompt the user to either `Open anyway`, or crate a `New Inherited` scene. Choose `New Inherited`.
    4. This will open a new scene with the asset, where you can freely edit the asset's components and work with it.
    5. Once done, save this new inherited scene, and use it inplace of the asset's scene in the main level scene.

> [!NOTE]
> You can also use the saved `New inherited` scene as part of any other scene, for example, you can add it in a `StaticBody3D` scene.

---

## 3D Collisions

Just like in 2D, 3D collisions can apply to any physics body, if we have a collision shape set to it.
To apply a collision shape we can either:

- Add a `CollisionShape3D` node to our scene tree, and manually set the shape, size and other paramters in the editor and inspector.
- When viewing a `MeshInstance3D` node/scene, click on the `Mesh` button in the toolbar, ad then choose `Create Collision Shape...`
    - This will open a popup window that let's us configure some aspects of the generated Collision Shape
    - After clicking `Create`, a `CollisionShape3D` node will appear in the scene tree which we cane move freely.

> [!NOTE]
> Collision Shapes automatically generated from a mesh will often be complex, which will result in having more performance cost.
> 
> If used carelessly, this can have a substantial negative effect on the game's performance, so use with caution.

---

## Replacing Greyboxes

So, we want to start putting our actual level assets into the level. We'll be using the greybox we made previously as a baseline and build on from there.

To start, we'll make the greybox transparent so we can work easier. to do that we will:
- Give the `CSGBoxCombiner` a new material, under `Geometry` -> `Material Override`
- Under `Transperancy`, we will set `Transparency` to `Alpha`
- Under `Albedo`, `Color`, set the color to taste, and decrease the `A` channel so the greybox becomes transparent.

And like that, we're ready to start putting in the level's assets.

Remember that all assets placed need to be a scene of an appropriate type with collision shapes set. Walls, ceilings and ground tiles should all be `StaticBody3D`s. 

Decoration assets can be other types, depending on the context.

---

## Environment and Lighting

### Environment 

The game's `WorldEnvironment` node is what has complete control over the _environment_ of the level and the overall feel and look.
We can configure ambient lighting, sky and horizon colors, set up skyboxes and much more.

We can either manually add the `WorldEnvironment` node, or from the toolbar, click the 3 dots and chose to the `Add Environment to Scene` button.
Once in the scene tree, in the inspector, we can create a new `environment` resource, which houses all the settings.

Inside the `Environment` resource there is:
- `Background`
- `Sky`
- `Ambient Light`
- `Reflected Light`
- `Tonemap`
- `Fog` & `Volumetric Fog`
- & more.

### Sky

The sky resource lets us setup the sky's colors, intensity and more.
Types:
- `PanoramaSkyMaterial`
    - Complete control over sky and ground colors, horizons, Sun and more.
- `ProceduralSkyMaterial`
    - Allows to input a skybox picture are the skybox.
- `PhysicalSkyMaterial`

### Lighting

Lighting works just like 2D. The types are:

- `DirectionalLight3D`
    - Acts as the sun. Can control color, direction and angle, and more.
- `OmniLight3D`
    - Acts as an orb of light. Can contorol color, size and more.
- `SpotLight3D`
    - A spotlight light source.

---

## Resources

- **[Godot 3D Documentation](https://docs.godotengine.org/en/stable/tutorials/3d/index.html)**
- **[Godot 3D Environment](https://docs.godotengine.org/en/stable/tutorials/3d/environment_and_post_processing.html#environment)**
- **[Brackeys - How to make 3D Game in Godot](https://youtu.be/ke5KpqcoiIU?si=crAQHQGP8ZxCE6m-) (from 18:48 to 47:18)**


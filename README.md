# Godot Third Person Controller
> Third Person Controller Tutorial and Demo

## Introduction
This is a short tutorial for implementing a third-person controller in the Godot Game Engine.
If you'd rather see in Godot, just clone this project and import into Godot. Otherwise, read on.

## Setting up the Scene
Let's start by creating a basic scene with a floor and a player object. In a new 3D scene, create
the following Node hierarchy (Name : Node Type):

 * Floor : MeshInstance (PlaneMesh)
 * Player : KinematicBody
   * PlayerMesh : MeshInstance
   * CollisionShape : CollisionShape
   * CameraGimbal : Spatial
     * InnerGimbal : Spatial
       * Camera : Camera

**Floor:** This is a plane that will act as the floor or ground. Scale it up about 40 times.
Add a texture so we can easily see the player moving--use `icon.png` that's included with
every new project by default.

**Player:** A KinematicBody is a special kind of body that is meant to be user-controlled.
Additionally, this node will act as a container for all player objects, so when we move this
node, all others will automatically move as well.

**PlayerMesh:**: The visual instance of the player. Set the Y-scale and Y-translation to 2.

**CollisionShape:** Collider for the KinematicBody above. The easiest way to create this is to
select the PlayerMesh, then in the editor click _Mesh -> Create Single Convex Collision Sibling_.

**CameraGimbal/InnerGimbal:** These handle rotation for the camera to keep it level. This will be
explained in greater detail when we implement camera rotation.

**Camera:** The third person camera. Set the translation to (0, 5, 6) and the rotation to
(-15, 0, 0) so that the PlayerMesh is visible. Adjust as needed.

## Keyboard Controls
We now add key bindings for our player movement. Add the following actions to the project's
Input Map:

 * `move_forward`: W
 * `move_back`: S
 * `move_left`: A
 * `move_right`: D

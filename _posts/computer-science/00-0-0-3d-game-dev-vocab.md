---
layout: post
title: 3D Game Development Vocab + Unity
date: 2018-05-20
tags: computer-science
---
## 3D Game Development
**Inheritance System**: All objects are types and these types exist on an inheritance tree. (a particular object could be an instance of zombie which is a child of hostile AI, which is a child of AI, etc.)

**Component System**: All objects have individual components that add functionality. (i.e movement component, hostile Ai component, health component, etc.)

*Unity uses a component system, but technically you can consider the component system as a generalization of the inheritance system. As such you could force yourself to use inheritance in Unity.*

<!--more-->

**The Three Transforms**: The camera used in the scene view as well as objects can all be transformed in 3 basic ways:
  * **Translation**: Translating an object means moving it across in 3D space.
  * **Rotation**: Rotating an object means rotating about an axis. If an object is at (0,0,0) then the object would rotate in place.
  * **Scaling**: Scaling an object means increasing or decreasing its size. You can either do this equally on all 3 axes (growing or shrinking the object) or scale each axis separately (stretching and squishing the object).
  * **Rect Tool**: In 2D, transformations are simple enough that the above three can be combined into a single tool. Thus when making 2D unity games, the *Rect Tool* is all you'll need.

Note That these transformations can all be done with respect to the global coordinate system or the objects own local coordinate system.

**Left-Handed vs. Right-Handed Coordinate Systems**: When manipulating objects in 3D space, it is important to be consistent in what axes we use. ![hands](https://upload.wikimedia.org/wikipedia/commons/b/b2/3D_Cartesian_Coodinate_Handedness.jpg?style=centerme){:width="400px"}

**3 Types of Light Sources**
  * **Point Light**: These sources emanate light in all directions around a single point. The farther away you are from this source, the dimmer it will be (the light rays are not as bunched up so to speak). It is analogous to a light bulb.
  * **Directional Light**: A directional light source emanates light uniformly everywhere in a scene. As such its position doesn't matter only the direction it is facing. This is analogous to the sun. (the sun is just a point light very far away, giving it the effect of a directional light). Typically, there is only one directional light per scene.
  * **Spot Light**: These lights are similar to point lights except they only emanate in a limited cone before their light is cut short. They're usually used to highlight an area of the scene rather than provide light to see your surroundings.

**Free Look**: Free look is the player's ability to move their mouse, joypad, control stick, etc. around and freely view the 3D world their character inhabits. For computer games this is referred to as *mouse-look*. (The N64 for example, didn't even have a full analog stick dedicated to the camera. It instead use a set of  directional buttons known as the c-buttons or camera buttons)

**Euler Angles vs. Quaternions**: When representing rotations in 3D space we can either use a set of 3 angles (1 for the rotation about each axis) or a single 4D number known as a quaternion. The quaternions $\mathbb{H}$ are a 4D generalization of the 2D complex numbers that are very apt in describing natural 3D rotations (similar to how the complex numbers are apt in describing 2D rotations).

**Frame Rate Dependent Code**:
All scripts have an update method that run at every pass of the object. If that update code happens to, for example, move the player, the player's speed would be dependent on the speed of the computer running the game. To remedy this we have to take into account the *frame rate* of the game and make sure that every update is spread out over a single frame rather than done all at once.

**Raycasting**: Raycasting is when a ray (an imaginary line that extends out form a point) is sent out at some angle and the location of the point it first intersects with, if it hits at all, is recorded. A first person shooter, for example, would use raycasting to tell whether a fired bullet hit an enemy or wall. In this case the ray would be perpendicular to the middle of the player's screen.

**Mouse Picking**: Mouse picking is finding the spot a mouse clicked on in 3D space. Doing this requires casting a ray from the user's point of view and seeing where it first collides.

**Rendering**: Computing the 2D array of pixels that corresponds to the current camera angle and 3D world it is viewing. This array is what is drawn onto the screen. (3D world -> 2D screen)

## Unity Game Development
**Core Parts of a Unity Game**
  * **Scenes**: All levels/areas/worlds are known as scenes in Unity. All games, 2D and 3D, are the result of the interactions between the objects in the current scene.
  * **Objects**: Objects (they are instances of `GameObject` in code) are the things the scene is made up of. All things in a scene are objects (the player, weapons, tools, cars, buildings, scenery, the floor, cameras, light sources) and so all Unity games are made of these. Even when implementing a component with non-tangible functionality (like a global timer) these can be added to an empty object (because all components and scripts must be part of an object).
  * **Components**: These are the things that give objects functionality. Unity comes prepackaged with general components for objects (cameras, collision, light sources, sound sources, etc.). By default all objects must have a position component (even if they are an empty object that do not physically exist in the scene). Scripts are the custom components that the developer adds to objects in order to create functionality in a game.
  * **Scripts**: Scripts are custom components that can be added to Unity objects. Unity allows for scripting in C# and JavaScript (although due to the difference in programming websites and 3D games, JavaScript is often called UnityScript when being used for Unity.) These scripts are at the core of programming a Unity game. Some basic things you might need to create scripts for are movement, UI, AI, collision behavior, etc.

**The Unity Editor**
  * **Hierarchy**: This tab (by default on the left) shows a text list of all the objects in the current scene. Note that objects can be linked together (by dragging them on top of each other in the hierarchy tab) in order to group them together.
  * **Scene View**: The scene view (in the middle of the screen) shows the current scene and all the objects within it. You can navigate the scene and transform objects in it with the mouse and keyboard. (`W`,`E`,`R` are the transformations, and `CTRL`,`ALT`,`SHIFT`,`MOUSE 1`,`MOUSE 2`,`MOUSE 3` move the camera around)
  * **Inspector**: When you click on an object in the scene view or hierarchy, all its properties (i.e the properties of its components) appear in the inspector tab (by default on the right). Here you can modify the different parameters of a component (the location of the object, what camera angle the object is using, the maximum speed of the objects movement, etc.)
  * **Game View & the Toolbar**: The game view (also in the middle of the screen) actually runs the game when you press play in the toolbar (at the top of the screen). It's important tot note that the game view actually updates in real time with changes in code/scene, so you can rapidly prototype.
  * **Project**: Located at the bottom of the screen, the project tab shows all the assets, scenes, and scripts for the current project. It's basically a file explorer. You can right click to create new scripts, scenes, and objects in this tab.
  * **Console**: This outputs whatever was programmed to be outputted there by the scripts that are currently running in the scene. Usually used for debugging or to output errors encountered while running the script.

**Coroutines**: ???

**Prefabs**: ???

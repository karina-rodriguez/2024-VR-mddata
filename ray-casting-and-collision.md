---
title: 'Ray casting and collision'
teaching: 30
exercises: 10
---

### Group 7: Tomas Diogo, Diogo Nero, Aron Smith, Ethan Hosford

:::::::::::::::::::::::::::::::::::::: questions 

- What are the basics of ray casting?
- What is collision detection?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explain the basics of ray casting to underpin various functionalities in VR
- Demonstrate how to create colliders and basic example of their use

::::::::::::::::::::::::::::::::::::::::::::::::

## The basics of ray casting 

Ray casting is an approach to projecting virtual beams of light in a game environment, travelling from the camera's focal point through each pixel in the visible area, determining what is visible along the ray. 

When a ray cast hits an object in a game scene, it finds out everything about that object, such as what object it hit, its distance from camera, surface normals, and so on. 

Typically, ray casting is used for physics implementations in games. 

### Ray casting in VR 

In Virtual Reality, ray casting has numerous applications: 
1. Object interaction - Rays are cast from the controller or view direction towards objects, allowing user's to locate and interact with objects, such as picking them up. 
2. Navigation - Ray casting enables teleportational movement by casting beams to points on the ground based on where the user points their controllers. 
3. UI interaction - Rays are cast from the controllers against UI buttons and controls, allowing users to press buttons. 
4. Physics interactions - Objects/surfaces detected by ray casts can be combined with forces or effects for gameplay physics, such as bullet trajectory. 
5. Environmental scanning and feedback: Ray casts can scan the environment for detecting obstacles, measuring distances, and highlighting interactive areas. 
6. Hand and controller alignment - Rays can align virtual representations of the player's hands/controllers in relation to the environment for accurate positioning. 

## What is collision detection? 

Collision detection is the process of detecting and intersection of two or more objects in a virtual space. It determines _if_, _when_, and _where_ objects intersect. It can also operate in 2D and 3D spatial spaces. 

### How can colliders be made? 

In Unreal Engine, object meshes can have colliders of various shapes and complexities, depending on the dimensions and purpose of the mesh. Some objects can come with collision meshes by default, although these aren't always accurate enough for the developer's needs. 

Below are some ways of possibly creating collision meshes for objects: 

#### Simple automated collision meshes 

- "Sphere Simplified Collision" generates a sphere surrounding the object 
- "Capsule Simplified Collision" generates a capsule around the object 
- "Box Simplified Collision" generates a box around the object 

This approach is ideal for meshes that can easily fit into one of these shapes, and for when precise collision doesn't matter. 

#### K-DOP bounding volumes 

K Discrete Oriented Polytopes (where K is the number of axis-aligned planes) can be used to create more complex collision meshes around objects. Planes are pushed as close to the static mesh as possible for a more precise collider model. 

#### Automatic collision convexing 

The Auto Convex Collision tool can be used to automatically generate a collision mesh, which can then be adjusted through the Convex Decomposition panel, where you can determine the following: 
- Hull Count - the number of primitives to represent the collision mesh 
- Max Hull Verts - Increases/decreases the number of vertices the collision mesh has 
- Hull Precision - Number of voxels to use when generating the collision mesh 

Higher values give better precision. 

#### Complex collision meshes 

A quick and simple way of enabling highly detailed collision meshes is by toggling the Collision Complexity of an object to "Use Complex Collision As Simple". This forces the default collider to use the actual mesh of the object, guaranteeing a perfect collider (so long as the mesh is clean). 

However, because of the increased number of polygons in this collider approach, it's typically only used for static objects, as it can sometimes be too taxing to calculate collisions between moving objects with such high detail. 

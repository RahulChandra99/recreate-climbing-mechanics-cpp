# 🧗 Climbing Mechanics (Zelda/Uncharted Style)

This is my approach to creating climbing mechanics similar to those in games like *The Legend of Zelda: Tears of the Kingdom* and *Uncharted*.

Climb physics, vaulting actions, and an IK control rig are used to shape exactly how the character moves, climbs, and interacts with the environment.

In this demo, the player dynamically performs a vault or climb action based on the object's height, distance, and other factors in front.

---

## A. Setting Up Climbing Movement

### To begin, I implemented a custom movement component that enables climbing mechanics.
This forms the basis of the climbing logic and is crucial for handling how the character moves while climbing.

---

### 1. Gathering Surface Information

In this step, I utilized various traces to detect climbable surfaces and gather the necessary data about them. This is essential for knowing where and how the character can climb.

**Explanation:**

- **Using Traces for Surface Detection:** By employing line traces and sphere traces, I could precisely determine the character’s position relative to climbable surfaces. This information is then used to calculate the approach angle and distance to ensure the character can properly engage with the surface.
- **Capsule Trace for Detecting Climbable:** `DoCapsuleTraceMultiByObject()` performs a multi-object capsule trace, gathering all hit results within a specified radius and height. It uses debug settings to visualize traces as needed.
- **Line Trace for Specific Surface Checks:** `DoLineTraceSingleByObject()` executes a single-object line trace, returning the first detected surface in the path. It includes options for visual debugging and persistent shapes.
- **Checking for Climbable Surfaces:** `TraceClimbableSurfaces()` calculates start and end points based on the character's forward vector, then performs a capsule trace to check for climbable surfaces. Returns true if any surfaces are detected.
- **Tracing from Eye Height for Precision:** `TraceFromEyeHeight()` casts a line trace from the character's eye level, extending a specified distance forward. This method helps determine climbable surfaces directly in front of the character.

---

### 2. Implementing Custom Climbing Physics

After identifying climbable surfaces, the next step was to handle the movement while climbing.

**Explanation:**

- **Custom Movement Modes:** Instead of using the usual movement modes, I created a custom climbing mode to manage gravity, friction, and surface angles. This gave me more control over how the character moves, making the climbing bit more smoother.

---

### 3. Calculating Climbing Velocity and Rotation

To complete the climbing movement, I used surface data to set the character's climbing speed and direction, making sure they align smoothly with the surface.

**Explanation:**

- **Velocity and Rotation Adjustments:** The velocity is calculated based on the angle of the climbable surface, making sure the character’s speed and direction match the incline or decline of the climb.

---

## B. Climbing Locomotion and Animation

### 1. Creating the Animation Instance Class

I started by defining a custom animation instance class in C++ to rebuild the animation blueprint from scratch. This provided finer control over the character’s animations, specifically tailored for climbing.

**Explanation:**

- **Custom Animation Blueprint:** By handling the animation blueprint in C++, I could directly manage animation states and transitions. This approach gave me the flexibility to blend climbing animations more smoothly and respond dynamically to in-game actions.
- **Retargeting Animations with Mixamo:** I used Mixamo’s animation library to streamline the animation process. By utilizing the Mixamo converter, I was able to retarget and adapt existing animations to fit the character model accurately.

---

### 2. Implementing Climb Locomotion Logic

This logic detects when the character reaches a floor or ledge, allowing for appropriate animation transitions.

**Explanation:**

- By calculating distances and angles from the character to surrounding surfaces, the system can accurately detect when to initiate climb animations, ensuring fluid transitions as the character moves from one surface to another.

---

## C. Hand and Leg IK with Motion Warping

### 1. Building the Control Rig for Hand and Leg IK

I began by creating a control rig to manage hand and leg IK, ensuring that the character’s limbs are accurately positioned on surfaces while climbing.

**Explanation:**

- **IK for Precise Limb Placement:** The control rig adjusts hand and foot positions dynamically, based on the surface's shape and orientation. This makes climbing look better looking as the character’s limbs align with the environment naturally.

---

### 2. Implementing Motion Warping

To enhance climbing interactions, I added motion warping for smoother transitions and used the enhanced input system to introduce vaulting actions.

**Explanation:**

- **Dynamic Motion Warping and Input Mapping:** Motion warping allows for adaptable animations, so movements like vaulting adjust to surface angles. Using the enhanced input system, I mapped complex moves like hopping to new input actions that respond during climbing.

---

### 3. Creating a Climb IK Trace Function

I implemented a custom function to trace climbable surfaces and adjust the character’s hand and foot placement. This ensures accurate IK adjustments during climbing.

**Explanation:**

- **Surface-Tracing for Accurate IK:** The trace function calculates the exact points where the character’s hands and feet should attach. This allows the IK system to update dynamically, enhancing realism as the character moves across various surfaces.

 
  ### Follow Development here : [Link](https://www.youtube.com/playlist?list=PLuB7iMA25lu-h2bbjuA8XGDXH3ydaKaBX)


  

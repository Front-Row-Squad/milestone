![milestone_water](https://github.com/user-attachments/assets/94c6763d-1d7c-4f29-a9f2-a4402e2ac4aa)

Video: [https://drive.google.com/file/d/1h4FQFK81x4Nv_42j9rWgMfB2mGJ-UdoU/view?usp=share_link](https://drive.google.com/file/d/1h4FQFK81x4Nv_42j9rWgMfB2mGJ-UdoU/view?usp=share_link)

Slides: [https://drive.google.com/file/d/1R2jh4EaSPaCAn7eE1zPtPpMNQImEHWX3/view?usp=share_link](https://drive.google.com/file/d/1R2jh4EaSPaCAn7eE1zPtPpMNQImEHWX3/view?usp=share_link)

## Abstract

Creating a convincing water simulation has traditionally been a difficult task in computer graphics due to its complex behavior and demand for a potentially high level of detail in splashes, foam, and bubbles. We present a heuristics-based water simulation that allows for a high level of visual fidelity in real-time. Our simulation will contain most of the features which will be widely wanted, including a realistic surface, caustics for visual effect, buoyancy for physics, destruction physics for gameplay, and LOD optimization to make sure that it is still real-time and anti-aliased. Currently for this milestone, we have implemented some surface effects and some basic Blinn-Phong shading in Unity, and are still working on implementing the other features.

## Introduction

Water simulation is an important problem that has been extensively researched for tasks such as CGI film, video game design, and simulation environments. However, these effects can be very computationally expensive to physically model, so a number of heuristics have been created to circumvent more physically-grounded computations without losing visual fidelity. For cases such as video game design, making it real-time is crucial, and there is currently no standardized way of optimizing it (so different implementations use wildly different techniques based on artistic preference and requirements). We aim to produce a real-time water simulation that contains most of the features which will be widely wanted, including a realistic surface, caustics for visual effect, buoyancy for physics, destruction physics for gameplay, and level-of-detail optimization to make sure that it is still real-time and anti-aliased.

The simulation we present can be broken up into 3 main parts: mesh manipulation, lighting, and buoyancy. The water mesh is manipulated to follow a sum of sine waves with various frequency modifications in the frequency domain by using Fast Fourier Transform (FFT). To achieve real-time performance, the wave calculations have been parallelized by Unity compute shaders so the GPU can be utilized. Custom shaders will be written to handle the lighting of the water mesh, potentially caustics if time allows. Buoyancy will be implemented by devising a sampling strategy to approximate volume of an object under the water mesh and apply appropriate physics to push the object up.

## Progress and Preliminary Results

So far we have implemented the minimum baseline that we proposed for our project, which includes the water mesh and some basic lighting with Blinn-Phong shading. We implemented our water mesh in Unity, and we can manipulated this mesh by displacing its vertices by an artistic choice of sum of sine waves. The math is straightforward, but as the resolution of the mesh increases, the number of calculations is too burdensome for a CPU to handle, so parallelism must be employed. Unity has a built-in method to access GPU resources via compute shaders which we used to speed up the simulation to ensure real-time performance. We experimented with tuning parameters organically for this purpose, but ended up repurposing some of the code from one of the Git repositories [1] that we're drawing inspiration from to create visually appealing wave shapes. To get started with some reasonably realistic lighting, we implemented a Blinn-Phong shader similar to what we have learned and implemented from this course.

We can see in the video demo that we can vary parameters to achieve different wave shapes and achieve different lighting effects for the water surface. This is a good baseline for us to work on more realistic lighting and wave shapes as we incoroportate these features over the new 2 weeks.

## Work Plan

We are making good progress and are mostly still on schedule with our original plan:

- Week 1
    - Project setup (DONE)
    - Initial water mesh (DONE)
- Week 2
    - Milestone Video Slideshow (DONE)
    - Lighting Part 1: Basic Shading (DONE)
    - Plan Showcase Videos (DONE)
    - Buoyancy Part 1 (IN PROGRESS)
    - Destruction Physics (IN PROGRESS)
    - AA and Optim Part 1 (IN PROGRESS)
- Milestone report (We're here!)
- Week 3
    - Lighting Part 2: Caustics (Stephen)
    - Buoyancy Part 2 (Jeremy / Nick)
    - AA and Optim Part 2 (Shiran)
- Week 4
    - Display Scene (All)
    - Final Report Writing (All)
    - Showcase Videos (Nick)

We have completed many of of week 2 goals, and the ones that haven't been completed are in progress and have already been planned to be completed in the following week. We think that given this schedule, we should be able to make all the deliverables that we had originally planned in time still, though if we run into unforseen issues and roadblocks, we can always scale back some of the additional features that we are working on.

## References

Garrett Gunnell. "Water Simulation Project." Available at: [https://github.com/GarrettGunnell/Water](https://github.com/GarrettGunnell/Water).


# ADR-002: Using World class to encapsulate complex scene interactions

## Context
The game's core loop involves multiple interacting systems: a 3D construction scene, a 2D sky background, physics simulation, environment parameters, and rendering logic. These interactions are too complex to be fully described by pure data classes or isolated Managers. While Managers handle business logic and data transformations (e.g., calculating wind force), they don't directly control scene objects, camera behavior, physics bodies, or real-time rendering.
I need a facade decision, that incapsulates these complex interactions into single point of control.

## Decision
I will introduce a World class that acts as the orchestrator for the 3D scene, 2D sky and physics. It encapsulates all complex interactions that span across multiple systems. The World is responsible for:
1. Rendering 3D scene of the building (crane, tower, falling tower blocks)
2. Rendering 2D background with the sky gradient and town.
3. Environment Parameters: Holding and applying the current environmental state (wind, gravity, time of day) to the scene and physics simulation.
4. It also incapsulate physics of falling blocks (using Godot default physics). Maybe in next versions, physics calculations will be moved to manager.

But World do not control time and weather changes. 

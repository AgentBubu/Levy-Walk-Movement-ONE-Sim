# LevyWalkMovement

This class implements the Lévy Walk movement model for nodes in the ONE simulator. The Lévy Walk is a random walk where step lengths follow a heavy-tailed (Pareto-like) distribution, resulting in a mix of many short moves and occasional long jumps.

## Overview

- **Step Lengths:** Drawn from a Pareto-like distribution controlled by the `alpha` parameter.
- **Directions:** Each step is taken in a random direction.
- **Boundaries:** If a step would take the node outside the simulation area, the node remains stationary for that step.
- **Parameters:**
  - `alpha`: Controls the distribution of step lengths (smaller values mean more long jumps).
  - `minStep`: Minimum possible step length.
  - `scaleFactor`: Multiplies the value from the Pareto distribution.

## Key Methods

- `getInitialLocation()`: Places the node at a random position within the simulation area.
- `getPath()`: Generates the next movement step using the Lévy Walk logic.
- `replicate()`: Creates a copy of the movement model for another node.

## Configuration

Parameters can be set in the ONE scenario settings under the `LevyWalkMovement` namespace:

```ini
LevyWalkMovement.alpha = 1.5         # Typical range: 0 < alpha <= 2
LevyWalkMovement.minStep = 0.1       # Minimum step length
LevyWalkMovement.scaleFactor = 1.0   # Step length scale
```

## Usage

To use this movement model in your scenario, specify `movement.LevyWalkMovement` as the movement model in your settings.

## Example

```
# Common settings for all groups
Group.movementModel = LevyWalkMovement

# Choose between 0-2
LevyWalkMovement.alpha = [0.5;0.7;0.9;1.0;1.2;1.4;1.6;1.8;2.0]

LevyWalkMovement.minStep = 0.1
LevyWalkMovement.scaleFactor = 10
```

## File

- [`src/movement/LevyWalkMovement.java`](src/movement/LevyWalkMovement.java)

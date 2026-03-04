# Pheromone Path Optimizer

A multi-robot path planning framework based on **Ant Colony Optimization (ACO)** that simulates robots navigating a dynamically generated grid road network.
The system uses **pheromone-guided exploration, adaptive heuristics, graph pruning, and collision-aware motion control** to compute efficient and safe paths for multiple robots.

The project demonstrates how swarm intelligence techniques can be applied to **multi-agent navigation problems** in robotics, logistics, and autonomous systems.

---

## Overview

This project implements a simulation where multiple robots must navigate a grid-based environment from randomly generated start locations to assigned targets.

Each robot independently searches for optimal routes using **Ant Colony Optimization**, where artificial ants explore the graph and update pheromone trails that guide future searches.

The framework includes several enhancements beyond classical ACO:

* Adaptive pheromone and heuristic weighting
* Graph edge pruning and recovery
* Velocity-based collision avoidance
* Energy / work estimation for robot motion
* Parallelized ant path exploration
* Animated visualization of robot movement

The result is a swarm-inspired navigation system capable of coordinating multiple robots in a shared environment.

---

## Key Features

### Multi-Robot Path Planning

Multiple robots simultaneously compute paths through the same graph environment.

### Adaptive Ant Colony Optimization

The algorithm dynamically adjusts pheromone importance and heuristic influence during iterations.

### Graph Edge Pruning

Edges that significantly deviate from efficient paths are temporarily removed to reduce search space.

### Edge Recovery Mechanism

Pruned edges can be restored when necessary if they become relevant to optimal paths.

### Collision-Aware Motion Planning

Robots adjust their velocities dynamically to avoid occupying the same space at the same time.

### Energy / Work Estimation

The framework calculates the mechanical work required for robot movement based on velocity changes and path length.

### Parallel Path Exploration

Multiple ants search the graph concurrently to improve exploration efficiency.

### Visualization

The simulation animates robot motion across the environment using Matplotlib.

---

## System Architecture

The system operates through several stages:

1. **Environment Generation**

   * A grid road network is generated with random spacing.
   * Each road segment is assigned a traversal weight representing path difficulty.

2. **Robot Initialization**

   * Three robots are assigned random start points.
   * Target destinations are assigned using a distance-minimizing matching strategy.

3. **ACO Path Search**

   * Artificial ants explore possible routes between start and target nodes.
   * Pheromone trails are updated based on successful path quality.

4. **Graph Pruning**

   * Edges unlikely to contribute to optimal paths are removed to improve search efficiency.

5. **Edge Recovery**

   * If pruning removes necessary paths, critical edges can be restored.

6. **Collision Avoidance**

   * Robots dynamically adjust velocities to prevent spatial-temporal collisions.

7. **Energy Estimation**

   * Mechanical work required for robot movement is calculated.

8. **Simulation Visualization**

   * Robot trajectories are animated across the road network.

---

## Algorithm Components

### Ant Colony Optimization

Each ant constructs a path by probabilistically selecting neighboring nodes based on:

* pheromone intensity
* heuristic desirability
* path cost

The probability of selecting an edge is determined by:

P(edge) ∝ (pheromone^α) × (heuristic^β)

Where:

* α controls pheromone influence
* β controls heuristic influence

Both parameters adapt dynamically during the optimization process.

---

### Dynamic Pheromone Updates

Pheromone values are updated using:

* evaporation to reduce influence of old paths
* reinforcement of successful paths
* higher rewards for shorter paths with fewer turns

---

### Edge Pruning Strategy

Edges are pruned when they:

* deviate significantly from the direct path between start and target
* create inefficient detours

This reduces the effective search space and accelerates convergence.

---

### Velocity-Based Collision Avoidance

Robots avoid collisions using **adaptive velocity scaling**.

When spatial conflicts are detected:

* velocity is reduced
* robot movement is temporarily delayed

This ensures robots do not occupy the same location simultaneously.

---

### Work / Energy Calculation

Mechanical work is estimated using velocity changes and motion distance.

This provides a physical interpretation of path efficiency beyond geometric distance.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/AdityanRajesh7/pheromone-path-optimizer.git
cd pheromone-path-optimizer
```

Install required packages:

```bash
pip install -r requirements.txt
```

---

## Requirements

The project uses the following Python libraries:

```
numpy
matplotlib
```

Python version:

```
Python 3.8+
```

---

## Running the Simulation

Execute the main script:

```bash
python code.py
```

The program will:

1. Generate a road network
2. Initialize robots and targets
3. Run the ACO optimization
4. Apply collision avoidance
5. Display an animated visualization of robot movement

---

## Example Output

The simulation prints:

* robot paths
* path cost
* estimated work required for each robot

An animated visualization displays robots navigating the grid environment.

---

## Example Applications

The methods used in this project are relevant to several real-world domains:

* autonomous robot navigation
* warehouse automation
* swarm robotics
* logistics routing
* multi-agent traffic systems
* drone fleet coordination

---

## Future Improvements

Possible extensions include:

* support for larger robot swarms
* real-time dynamic obstacles
* reinforcement learning integration
* ROS (Robot Operating System) compatibility
* GPU-accelerated optimization
* real-world map integration

---

## Author

Adityan Rajesh

GitHub:
https://github.com/AdityanRajesh7

---

## License

This project is provided for research and educational purposes.

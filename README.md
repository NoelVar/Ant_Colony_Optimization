# Ant Colony Optimisation

Developed for the Programming/Video Competition 2026 as part of the  
**Biologically Inspired Methods** course at King's College London.

---

## About the project

This project implements a fully working **Ant Colony Optimization (ACO)** algorithm applied to the **Travelling Salesman Problem (TSP)**, with visualisation.

Inspired by:
- [Ant Colony Optimization — Original Paper](https://www.researchgate.net/publication/308953674_Ant_Colony_Optimization)
- [Introduction to ACO — GeeksForGeeks](https://www.geeksforgeeks.org/machine-learning/introduction-to-ant-colony-optimization/)

---

## About the algorithm

Ant Colony Optimisation is a meta-heuristic method inspired by the behaviour of ants as they collect food and bring it back to their nest. Ants leave a trail of pheromone on the ground as they move, which other ants follow. This leads to a high concentration of pheromone being left on an important path. Based on the Two Bridge experiment, ants can utilise their pheromone to find the shortest path to a desired destination, e.g., a food source or nest.

### Selection Probability
At each step, an ant at city $i$ chooses the next city $j$ with probability:

$$p_{ij} = \frac{\tau_{ij}^{\alpha} \cdot \theta_{ij}^{\beta}}{\sum_{l \in N_i} \tau_{il}^{\alpha} \cdot \theta_{il}^{\beta}}$$

Where:
- $\tau_{ij}$ — pheromone amount on edge $(i, j)$
- $\theta_{ij} = \frac{1}{c_{ij}}$ — heuristic information associated with given edge
- $\alpha$ — pheromone importance value
- $\beta$ — heuristic importance value
- $N_i$ — set of all candidate nodes connected (next to go to)

### Pheromone Update
After each iteration, pheromone evaporates and is added to popular edges:

$$\tau_{ij}(t) \leftarrow (1 - \rho) \cdot \tau_{ij}(t) + \frac{1}{C_k}$$

Where:
- $\rho$ — evaporation rate
- $C_k$ — cost of solution constructed by ant $k$ on iteration $t$

---

## Components

| Function | Purpose |
|----------|---------|
| `__init__` | Initialises parameters |
| `heuristic()` | Calculate heuristic matrix (Eta) |
| `selection_probability()` | Calculates the selection probability for the next city to visit |
| `pheromone_update()` | Evaporate pheromone, calculate the value the pheromones should be updated by, updates tau matrix |
| `calculate_cost()` | Computes total tour distance |
| `visualise()` | Plot the best tour and the tours taken during the iterations, show the convergence of the cost |
| `run()` | Executes the ACO algorithm |

---

## Dependencies

```python
numpy
matplotlib
sklearn (MDS)
```

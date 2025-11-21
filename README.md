# CI2025_lab3
CI - Lab 3
This laboratory compares three shortest-path search algorithms on a directed, weighted graph (created using create_problem) to evaluate their efficiency and robustness under different conditions.

## Robustness
The primary comparison focused on the ability of the algorithms to operate in the presence of negative weights (when negative_values = True).

- The Bellman–Ford algorithm detects negative cycles and raises
a NetworkUnbounded exception, and returns the guaranteed minimum cost when no negative cycles are present.
- Dijkstra’s algorithm fails and NetworkX raises a ValueError as soon as it encounters a negative weight.
- A* does not detect negative cycles and does not guarantee optimality, the algorithm tends to get stuck in infinite loops.

Conclusion on robustness: only Bellman–Ford is correct for graphs with negative weights, while Dijkstra and A* are unsuitable and unreliable in these conditions.

## Efficiency
When no negative weights are present (negative_values = False), the algorithms can be compared based on their speed.
The execution-time results (Time_Astar_s, Time_Dijkstra_s, Time_Optimal_s) confirm the theoretical complexities:
- A* Search: the fastest algorithm overall.
- Dijkstra: intermediate speed.
- Bellman–Ford: the slowest.

The code prints the relative error of A* and Dijkstra compared to the optimal cost (Bellman–Ford) for each tested pair.
When no negative weights are present, the relative error for both algorithms is always zero.

## Custom A* implementation
The A* algorithm used in this comparison does not use the native nx.astar_path function from NetworkX; the implementation was written manually using the heapq module to replicate the internal mechanics of the algorithm.

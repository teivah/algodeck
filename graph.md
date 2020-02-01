# Graph

## A* algorithm

Complete solution to find the shortest path to a target node

Algorithm:
- Put initial state in a priority queue
- While priority queue is not empty: poll an element and inserts all neighbours
- If target is reached, update a min variable

Priority is computed using the evaluation function: f(n) = h + g where h is an heuristic (local cost to visit a node) and g is the cost so far (length of the path so far)

[#graph](graph.md)

## Backedge definition

An edge from a node to itself or to an ancestor

[#graph](graph.md)

## Best-first search algorithm

Greedy solution (non-complete) to find the shortest path to a target node

Algorithm:
- Put initial state in a priority queue
- While target not reached: poll an element and inserts all neighbours

Priority is computed using the evaluation function: f(n) = h where h is an heuristic (local cost to visit a node)

[#graph](graph.md) [#greedy](greedy.md)

## BFS & DFS graph traversal use cases

BFS: shortest path

DFS: does a path exist, does a cycle exist (memo: D for Does)

DFS stores a single path at a time, requires less memory than BFS (on average but same space complexity)

[#graph](graph.md)

## BFS and DFS graph traversal time and space complexity

Time: O(v + e) with v the number of vertices and e the number of edges

Space: O(v)

[#complexity](complexity.md) [#graph](graph.md)

## Bidirectional search

Run two simultaneous BFS, one from the source, one from the target

Once their searches collide, we found a path

If branching factor of a tree is b and the distance to the target vertex is d, then the normal BFS/DFS searching time complexity would we O(b^d)

Here it is O(b^(d/2))

[#graph](graph.md)

## Connected graph definition

If there is a path between every pair of vertices, the graph is called connected

Otherwise, the graph consists of multiple isolated subgraphs

[#graph](graph.md)

## Difference Best-first search and A* algorithms

Best-first search is a greedy solution: not complete // a solution can be not optimal

A*: complete

[#graph](graph.md)

## Dijkstra algorithm

Input: graph, initial vertex

Output: for each vertex: shortest path and previous node // The previous node is the one we are coming from in the shortest path. To find the shortest path between two nodes, we need to iterate backwards.  Example: A -> C => E, D, A

![](res/djikstra.png)

Algorithm:
- Init the shortest distance to MAX except for the initial node
- Init a priority queue where the comparator will be on the total distance so far
- Init a set to store all visited node
- Add initial vertex to the priority queue
- While queue is not empty: Poll a vertex (mark it visited) and check the total distance to each neighbour (current distance + distance so far), update shortest and previous arrays if smaller. If destination was unvisited, adds it to the queue
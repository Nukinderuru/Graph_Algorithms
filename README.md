# Graph_Algorithms

![Graphs_image](/images/Intro_to_Graphs.jpeg)

## Contents

1. [Part 1. Depth- and Breadth-first search](#part-1-depth--and-breadth-first-search)  
2. [Part 2. Finding the shortest paths in a graph](#part-2-finding-the-shortest-paths-in-a-graph)  
3. [Part 3. Finding the minimum spanning tree](#part-3-finding-the-minimum-spanning-tree)  
4. [Part 4. Traveling salesman problem](#part-4-traveling-salesman-problem)  
5. [Part 5. Console interface](#part-5-console-interface)

Within this project, all graphs must meet the following requirements:
- Edge weights are only natural numbers.
- Weights may differ on all edges.
- Only nonzero connected graphs.

## Part 1. Depth- and Breadth-first search

First of all, I need to store the graphs, load them from files and export to files. For these purposes `Graph` class was implemented. It stores information about the graph using an **adjacency matrix**. The dimensionality of the adjacency matrix is set dynamically when initializing the graph (when loading it from a file).
The class `Graph` also contains the following public methods:
+ `LoadGraphFromFile(string filename)` - loading a graph from a file in the adjacency matrix format.
+ `ExportGraphToDot(string filename)`- exporting a graph to a dot file.

Now I can implement some basic algorithms on graphs, c'est-а-dire depth first search and breadth first search. For this, `GraphAlgorithms` class was implemented. It contains some useful algorithms on graphs as public methods. Let's start with these two:

+ `DepthFirstSearch(Graph &graph, int start_vertex)` - a *non-recursive* depth-first search in the graph from a given vertex. The function returns an array that contains the traversed vertices in the order they were traversed. When implementing this function, a *self-written* data structure **stack** was used.

![DFS](/images/Depth-First-Search.gif)

+ `BreadthFirstSearch(Graph &graph, int start_vertex)` - breadth-first search in the graph from a given vertex. The function returns an array that contains the traversed vertices in the order they were traversed. When implementing this function, a *self-written* data structure **queue** was used.

![BFS](/images/Breadth-First-Search.gif)

## Part 2. Finding the shortest paths in a graph

* Now let's move on to the following methods of the `GraphAlgorithms` class:
+ `GetShortestPathBetweenVertices(Graph &graph, int vertex1, int vertex2)` - searching for the shortest path between two vertices in a graph using *Dijkstra's algorithm*. The function accepts numbers of two vertices as input and returns a numerical result equal to the smallest distance between them.

![Dijkstra's_algorithm](/images/Dijkstra_Algorithm.gif)

+ `GetShortestPathsBetweenAllVertices(Graph &graph)` - searching for the shortest paths between all pairs of vertices in a graph using the *Floyd-Warshall algorithm*. As a result, the function returns the matrix of the shortest paths between all vertices of the graph.

![Floyd_Warshall_algorithm](/images/Floyd_warshall.gif)

## Part 3. Finding the minimum spanning tree

* Now let's move on to the minimal spanning trees. For that there is implemented the following method:
+ `GetLeastSpanningTree(Graph &graph)` - searching for the minimal spanning tree in a graph using *Prim's algorithm*. As a result, the function returns the adjacency matrix for the minimal spanning tree.

![Prim_algorithm](/images/Prim-algorithm.gif)

## Part 4. Traveling salesman problem

* And now the most interesting part! The Traveling Salesman Problem. There are three methods implemented to find the shortest Hamiltonian cycle in a weighted graph:
+ `SolveTravelingSalesmanProblem(Graph &graph)` - solving the traveling salesman's problem using the *ant colony algorithm*. As a result, the function returns the `TsmResult` structure described below:
    ```cpp
    struct TsmResult {
        std::vector<int> vertices;    // an array with the route you are looking for (with the vertex traverse order)
        double distance;  // the length of this route
    }
    ``` 
![Ant_colony_algorithm](/images/Ant_Colony_Algorihm_applied_to_the_Travelling_Salesman_Problem.gif)

+ `SolveTravelingSalesmanProblemAnnealing(Graph &graph)` - solving the traveling salesman's problem using the *simulated annealing algorithm*.

![Simulated_annealing_algorithm](/images/Hill_Climbing_with_Simulated_Annealing.gif)

+ `SolveTravelingSalesmanProblemGenetic(Graph &graph)` - solving the traveling salesman's problem using the *genetic algorithm*.

![Genetic_algorithm](/images/Genetic_algotithm_traveling_salesman.gif)

*If it is impossible to solve the problem with a given graph, an error is output.*

## Part 5. Console interface

* The main program is a console application for testing the functionality of the implemented classes.
* The console interface provides the following functionality:
    1. loading the original graph from a file;
    2. graph traversal in breadth with output of the result to the console;   
    3. graph traversal in depth with output of the result to the console;
    4. searching for the shortest path between any two vertices and displaying the result to the console;
    5. searching for the shortest paths between all pairs of vertices in the graph with the output of the resulting matrix to the console;
    6. searching for the minimal spanning tree in the graph with the output of the resulting adjacency matrix to the console;
    7. solving the salesman problem with the output of the resulting route and its length to the console;
    8. comparison of speed of the three algorithms used to solve the traveling salesman problem.

# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE:
## AIM:
To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.



## Algorithm
1.Initialize a color list with all vertices uncolored (value 0).
2.Start coloring vertices recursively, trying each color from 1 to m.
3.Check if assigning a color is safe by ensuring no adjacent vertex has the same color.
4.Backtrack if a color leads to conflict, and try the next available color.
5.Print the color assignment if all vertices are colored successfully, otherwise state no solution.
## Program:
~~~
Program to implement Graph Coloring Problem using backtracking.
Developed by: RAKSHITHA K
Register Number:  212223110039

class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [[0 for _ in range(vertices)] for _ in range(vertices)]

    def isSafe(self, v, colour, c):
        for i in range(self.V):
            if self.graph[v][i] and colour[i] == c:
                return False
        return True

    def graphColoringUtil(self, m, colour, v):
        if v == self.V:
            return True

        for c in range(1, m + 1):
            if self.isSafe(v, colour, c):
                colour[v] = c
                if self.graphColoringUtil(m, colour, v + 1):
                    return True
                colour[v] = 0
        return False  # Return False if no valid coloring is possible

    def graphColouring(self, m):
        colour = [0] * self.V
        if not self.graphColoringUtil(m, colour, 0):
            print("Solution does not exist")
            return
        
        return colour
            

# Driver code
g = Graph(4)
g.graph = [
    [0, 1, 1, 1],
    [1, 0, 1, 0],
    [1, 1, 0, 1],
    [1, 0, 1, 0]
]
m = 3
colors = g.graphColouring(m)

if colors:
    print("Solution exist and Following are the assigned colours:")
    for c in colors:
        print(c, end=" ")
    print()
~~~

## Output:
![image](https://github.com/user-attachments/assets/23eae476-e623-41eb-ade9-605940f09950)

## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.

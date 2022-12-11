# <u>Dijkstra's Algorithm</u>
### <u>Definition</u>
Dijkstra's Algorithm is a greedy algorithm that finds the shortest path from a particular source node to every other node in a graph. The algorithm is essentially a modifited breadth first search that uses a **priority queue** instead of a FIFO queue. 
* Works on the basis that **each subpath is the shortest path**.
* Produces a **shortest path tree**
	* It differs from a *minimum spanning tree* because the shortest distance between two vertices might not include all the vertices of the graph. (i.e It does not span a graph).
* **Relaxtion Process**: updating the cost of all vertices conencted to a vertex, if the costs would be improved by including the path via *v*. [source](https://stackoverflow.com/questions/12782431/relaxation-of-an-edge-in-dijkstras-algorithm#:~:text=The%20relaxation%20process%20in%20Dijkstra%27s%20algorithm%20refers%20to%20updating%20the%20cost%20of%20all%20vertices%20connected%20to%20a%20vertex%20v%2C%20if%20those%20costs%20would%20be%20improved%20by%20including%20the%20path%20via%20v.)
	* Whenever we face a ***tense*** node (i.e. when the tentative shortest path is incorrect because there's a path that is shorter), we ***relax*** the edge.
## <u>Pseudocode</u>
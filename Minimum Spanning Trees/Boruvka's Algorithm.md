# <u>Borůvka's Algorithm</u>
### <u>Definition:</u>
A greedy algorithm for finding the minimum spanning tree (MST) of a graph. The goal of the algorithm is to connect components using the shortest edge between them. It begins with all of the vertices considered as separate components.

Borůvka's is the oldest and simplext minimum spanning tree algorithm. Predatting both Prim's and Kruskal's.
	
## <u>Pseudocode</u>
```javascript
function boruvka(V, E):
	F = (V,∅)
	count = CountAndLabel(F)
	while count > 1 do:
		AddAllSafeEdges(E, F, count)
		count = CountAndLabel(F)
	return F
```
### <u>Algorithm Description</u>
All you do is add all safe edges and recurse. As simple as that.
	Each node is its own cluster at first. **Each cluster finds the minimum weight outgoing edge.** 	
	Find all the edges that leave a cluster, find the minimum weight one and connect those two and combine into a single cluster.

### <u>Time Complexity</u>
The worst case time complexity of this algorithm is **O(E log V)**.
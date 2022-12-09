	# <u>Topological Sort</u>
You can only do a topological sort on a **Directed Acyclic Graph (DAG)**.
All the edges go in the <b><u>same direction</u></b>. Either all edges point right to left or all edges point left to right. 
* The resulting order thus follows each node appearing before each of the nodes it points to.
* **NOTE:** Topological orderings are **NOT** unique.
### <u>Why Can't a Cyclical Graph Have a Topological Ordering?</u>
There cannot be an order if there's a **cyclical dependency** since there's nowhere to start. 
	You'll have trouble ordering the nodes in a single direction if there's a cycle.
**Every node in a cycle depends on another**, so any graph with a directed cycle is therefore forbidden.
### <u>Example from interviewcake.com</u>
![](https://www.interviewcake.com/images/svgs/messy_graph.svg?bust=210)
The **topological order** of the DAG above is `[1,2,3,4,5].`
* Notice how node 1 appears before both of the nodes it points to, the same rule apply for the others. 
* Each node appears before the nodes i
[Source](https://www.interviewcake.com/concept/java/topological-sort#:~:text=The%20topological%20sort%20algorithm%20takes,is%20called%20a%20topological%20ordering.)
## <u>Pseudocode</u>
```javascript
// Require: G is a DAG and stored as an adjacency list
function topsort(G):
	visited = [false,..., false]
	ordering = [0,..., 0]
	for each v ∈ V do:
		if visited[v] is false do:
			position = dfs(position, v, V, ordering, G)
	return ordering
	
// Executes Depth First Search DFS,	inserts a node directly inside the next valid position of the array and returns the next position, pos-1, as we are going in reverse order.
function dfs(pos, v, V, ordering, G):
	V[v] = true
	edges = g.getEdges(v)
	for each e ∈ E do:
		if V[e] is false do:
			pos = dfs(pos, e, V, ordering, G)
	add vertex v to the ordering list at position pos
	return decrement of position
	
```
### <u>Algorithm Description</u>
<ol>
	<li>Pick an <b>unvisited</b> node</li>
	<li>Do a <b>Depth First Search (DFS)</b>, beginning with the selected node and explore only the unvisited nodes.</li>
	<li>On the recursive callback of the DFS, add the current node to the topological ordering in <b>reverse order</b></li>
</ol>

### <u>Time Complexity</u>
The worst case time complexity of a topological sort is **O(V+E)**

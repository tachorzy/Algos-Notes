#### Defintion:
In a directed graph, You have a set of nodes, so **every pair of nodes can reach eachother** and you can't add any more nodes without ruining it it's strong connection. 
Any pair of nodes in a component can reach eachother.
A strongly connected component has to have a cycle. 
##  <u>Finding Strong Components</u>
## Kosaraju's Algorithm
* Do a DFS, you record the finish times
* Do a DFS in reverse order of the finish times.
	* on the transposed directed graph G^T 

The **Component Graph** is a DAG, it's a graph where each node is a component. 
* There can be no cycles. 
* All of the nodes on the right of a Component Graph will be explored before the nodes on the left. Thus their finishing times will come first.
	* Once a node is fully explored that is its finish time.
	* and that value is what is put into the list of finish times.
* The one that finished last will be in the first component.
Going in **reverse** will get you the Strongly Connected Component because 

The point of this algorithm is to find and output the components of a directed graph. 

#### A tangent on DFS in this algorithm
We go through all the nodes one by one and do a depth-first search, we go to a node and go through all of its neighbors. 
```python
for v in V:
	if v is unvisited:
		dfs(v)
```
You do DFS on every node while making sure you never do it twice. If a node's been visited you don't revisit it.

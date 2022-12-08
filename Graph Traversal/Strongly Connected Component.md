# <u>Strongly Connected Components</u>
### <u>Defintion:</u>
In a directed graph, a strongly connected component is a set of nodes in which **every pair of nodes can reach eachother**. And you can't add any more nodes without ruining it it's strong connection. 
* Any pair of nodes in a component can reach eachother.
* A strongly connected component has to have a cycle. 
In other words, a **strongly connected component** is a portion of a directed graph in whiched there is a path from each vertex to another.
#### <u>Example from Programiz</u>
Take the **initial graph** depicted below.
<img src="https://cdn.programiz.com/sites/tutorial2program/files/scc-initial-graph.png" width="355" height="143"/>
Its **strongly connected components** are shown below.
<img src="https://cdn.programiz.com/sites/tutorial2program/files/scc-strongly-connected-components.png" width="355" height="172"/>
Notice what make each of these components strongly connected. Each node can reach the others through a directed path. 
### <u>Finding Strong Components</u>
### <u>Kosaraju's Algorithm</u>
* Do a DFS, you record the finish times
* Do a DFS in reverse order of the finish times.
	* on the transposed directed graph G^T 

The **Component Graph** is a DAG where each node is a *component* (connected subgraph). 
* There can be no cycles. 
* All of the nodes on the right of a Component Graph will be explored before the nodes on the left. Thus their finishing times will come first.
	* Once a node is fully explored that is its finish time.
	* and that value is what is put into the list of finish times.
* The one that finished last will be in the first component.
Going in **reverse** will get you the Strongly Connected Component because 

The point of this algorithm is to find and output the components of a directed graph. 

#### <u>A tangent on DFS in this algorithm</u>
We go through all the nodes one by one and do a depth-first search, we go to a node and go through all of its neighbors. 
```python
for v in V:
	if v is unvisited:
		dfs(v)
```
You do DFS on every node while making sure you never do it twice. If a node's been visited you don't revisit it.

# <u>Strongly Connected Components</u>
### <u>Defintion:</u>
In a directed graph, a **strongly connected component (SCC)** is a set of nodes in which **every pair of nodes can reach eachother**. And you can't add any more nodes without ruining it it's strong connection. 
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
Kosaraju's Algorithm is a DFS based algorithm used to find Strongly Connected Components in a graph. 
* Do a DFS on the original graph, recording the finish times for each node.
* Transpose the graph (reverse the edges), done with an adjacency list.
* Do a DFS one by one in the now reversed order of the finish times. Until all nodes are visited.

You can think of the algorithm as this, we use DFS to find the correct order of nodes, and then we do another DFS going in that order.
* The reversed order we get from the transposed graph is the correct order we need. 
* **💡:** When we do a **post-order DFS on the transposed graph** we know that the last node will be inside of a *sink* SCC *(the sink component is the component without outgoing edges)*.

To represent our graph more clearly we can use a **component graph** to breakdown the problem before we analyze it for Strongly Connected Components. As illustrated in the image below.

<img src="https://media.discordapp.net/attachments/896545105480142864/1050135214128648292/image.png?width=891&height=669"/>

The **Component Graph** is a DAG where each node is a *component* (connected subgraph). 
* There aren't any cycles.
* And there are fewer nodes to take care of.
* Each node will be a component that we will then check for a strong connection.
When we traverse across this component graph we need to be aware of a few key things:
1. **💡: All of the nodes on the right** of a Component Graph will be **explored before** the nodes on the **left**. Thus their finishing times will come first.
2. Once a node is fully explored that is its finish time.
3. and that value is what is put into the list of finish times.
4. The node that finished last will be the first component.

### <u>Pseudocode</u>
Now with that all clarified, let's take a deeper look at the Pseudocode.
1. First Notice that we have two DFS calls in the `kosaraju` function. 
2. We do a postorder DFS on the reversed graph first to get the correct order. 
3. Then we do the second DFS pass going in that order.
```javascript
s = null
order = []
function dfs_loop(G):
	for node in G:
		if node is unvisited do:
			s = node
			dfs(G, node)

function dfs(G, V):
	V.explored = true
	V.leader = s
	for each edge:(v, W):
		if W.explored is false do:
			dfs(G, W)
	order = [v] + order

function kosaraju():
	dfs(G_reversed)
	dfs(G) in order
```
**[Source](https://hassamuddin.com/blog/kosaraju/ "https://hassamuddin.com/blog/kosaraju/")**
Each node's "leader" is the first node that we encountered within its SCC. We then group by leader and find each SCC.

`WIP notes below, rewording, and considering Khalid's input`
#### <u>A tangent on DFS in this algorithm</u>
We go through all the nodes one by one and do a depth-first search, we go to a node and go through all of its neighbors. 
```python
for v in V:
	if v is unvisited:
		dfs(v)
```
You do DFS on every node while making sure you never do it twice. If a node's been visited you don't revisit it.

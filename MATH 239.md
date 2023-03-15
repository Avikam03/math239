

### Isomorphism
Two graphs $G_1$ and $G_2$ are isomorphic if there exists a bijection $f: V(G_1) \to V(G_2)$ such that the vertices $f(u)$ and $f(v)$ are adjacent in $G_2$ iff $u$ and $v$ are adjacent in $G_1$

The bijection in this definition that preserves adjacency is called an isomorphism.

**Petersen Graph**:
![](https://i.imgur.com/WbleaOU.png)


### Handshaking Lemma
For any graph G, we have
$$\sum_{v \in V(G)} deg(v) = 2 |E(G)|$$
It follows from this that the number of vertices with odd degree is even.

### Average degree
The average degree of a vertex in a graph G is
$$\frac{2 | E(G) |}{|V(G)|}$$

### k-regular graph
A graph in which every vertex has degree k, for some fixed k, is called a k-regular graph.

### Complete graph
A graph in which all pairs of distinct vertices are adjacent. The complete graph with p vertices is denoted $K_p$ where $p \geq 1$.

### Bipartite graph
A graph in which the vertices can be partitioned into two sets A and B, so that all edges join a vertex in A to a vertex in B, is called a bipartite graph, with bipartition (A,B).

The complete bipartite graph $K_{m, n}$ has all vertices in A adjacent to all vertices in B, with $|A| = m$, $|B| = n$.

### n-cube
For $n \geq 0$ the n-cube is the graph whose vertices are the $\{0, 1\}$- strings of length n, and two strings are adjacent if and only if they differ in exactly one position.

### Adjacency Matrix
The adjacency matrix of a graph $G$ having vertices $v_1, v_2, v_3, \dots, v_p$ is the $p \times p$ matrix $A[a_{ij}]$ where 
$$
a_{ij = }
\left\{
\begin{array}{lr}
1 & \text{if }  v_i  \,\,\text{and}  \,\, v_j \, \,\text{are adjacent}\\
0 & \text{otherseise }
\end{array}
\right\} $$

### Incidence Matrix
The incidence matrix of a graph $G$ with vertices $v_1, v_2, \dots, v_p$ and edges $e_1, e_2, e_3, \dots e_q$ is the $p \times q$ matrix $B = [b_{i, j}]$ where
$$
b_{ij = }
\left\{
\begin{array}{lr}
1 & \text{if }  v_i  \,\,\text{is incident with}  \,\, e_j \, \,\text{are adjacent}\\
0 & \text{otherwise}
\end{array}
\right\} 
$$
### Adjacency List
Another way specifying a graph is to give, for each vertex, a list of the vertices adjacent to it.

### Subgraph
A subgraph of a graph $G$ is a graph whose vertex set is a subset $U$ of $V(G)$ and whose edge set is a subset of those edges of $G$ that have both vertices in $U$.

If $V(H) = V(G)$, that is $H$ has all vertices of $G$, we say H is a **spanning subgraph** of $G$.

If $H$ is a subgraph of $G$ and $H$ is not equal to $G$, we say it is a **proper subgraph** of $G$.

### Walk
A walk in a graph $G$ from $v_0$ to $v_n$, $n > 0$, is an alternating sequence of vertices and edges of $G$.
$$v_0e_1v_1e_2v_2 \dots v_{n - 1}e_n v_n$$
which begins with vertex $v_0$ and ends with vertex $v_n$ where $1 \leq 1 \leq n$, edge $e_i = {v_{i - 1}, v_i}$.

Note that the length of a walk is the number of edges in it (in this case, n)

A walk is said to be closed if $v_0 = v_n$.

### Path
A path is a walk in which all the vertices are distinct. Observe that since all the vertices in a path are distinct, so are all the edges.

### Theorem 4.6.2.
If there is a walk from vertex $x$ to vertex $y$ in $G$, then there is a path from $x$ to $y$ in $G$.

### Corollary 4.6.3
Let $x, y, z$ be vertices of $G$. If there is a path from $x$ to $y$ in $G$ and a path from $y$ to $z$ in $G$, then there is a path from $x$ to $z$ in $G$.

### Cycle
A cycle in a graph $G$ is a subgraph with $n$ distinct vertices $v_0, v_1, \dots, v_{n - 1}$, $n \geq 1$, and n distinct edges $\{v_0, v_1\}, \{v_1, v_2\}, \dots,\{v_{n - 2}, v_{n - 1}\}, \{ v_{n - 1}, v_0\}$. Equivalently, a cycle is a connected graph that is regular of degree two.

The subgraph we get from a cycle by deleting one edge is called a path.

A cycle with n edges is called an n-cycle or a cycle of length n.

The shortest possible cycle in a graph is a 3-cycle.

there are 2n closed walks of length n associated with a given n-cycle.

### Theorem 4.6.4
If every vertex in $G$ has degree at least 2, then $G$ contains a cycle.

### Girth
The girth of a graph $G$ is the length of the shortest cycle in $G$, and is denoted by $g(G)$.

### Hamilton Cycle
A spanning cycle in a graph is known as a Hamilton cycle.

### Connected
A graph $G$ is connected if, for each two vertices $x$ and $y$, there is a path from $x$ to $y$.

### Theorem 4.8.2.
Let $G$ be a graph and let $v$ be a vertex in $G$. If for each vertex w in $G$ there is a path from $v$ to $w$ in $G$, then $G$ is connected.

### Component
A component of $G$ is a subgraph $C$ of $G$ such that
- $C$ is connected
- No subgraph of $G$ that properly contains $C$ is connected.

### Cuts
If we are given a partition $(X,Y)$ of $V(G)$ such that there are no edges having an end in $X$ and an end in $Y$ , then there is no path from any vertex in $X$ to any vertex in $Y$ . So, if $X$ and $Y$ are both nonempty, $G$ is not connected. Given a subset $X$ of the vertices of $G$, the cut induced by $X$ is the set of edges that have exactly one end in $X$.

### Theorem 4.8.5.
A graph $G$ is not connected if and only if there exists a proper nonempty subset X of $V(G)$ such that the cut induced by $X$ is empty.

### Eulerian Circuit
An Eulerian circuit of a graph $G$ is a closed walk that contains every edge of $G$ exactly once.

### Theorem 4.9.2.
Let $G$ be a connected graph. Then $G$ has an Eulerian circuit if and only if every vertex has even degree.

### Bridge
An edge $e$ of $G$ is a bridge if $G - e$ has more components than $e$

### Lemma 4.10.2.
If $e = \{x, y\}$ is a bridge of a connected graph $G$, then $G - e$ has precisely two components; furthermore, $x$ and $y$ are in different components.

### Theorem 4.10.3. 
An edge $e$ is a bridge of a graph $G$ if and only if it is not contained in any cycle of $G$.

### Corollary 4.10.4.
If there are two distinct paths from vertex $u$ to vertex $v$ in $G$, then $G$ contains a cycle.













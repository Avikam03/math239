
## Math 239 Graph Theory

### Isomorphism
Two graphs $G_1$ and $G_2$ are isomorphic if there exists a bijection $f: V(G_1) \to V(G_2)$ such that the vertices $f(u)$ and $f(v)$ are adjacent in $G_2$ iff $u$ and $v$ are adjacent in $G_1$

The bijection in this definition that preserves adjacency is called an isomorphism.

### How to tell if 2 graphs are isomorphic?
A graph **invariant** is a property of a graph that does not change under isomorphism. We can therefore use the invariants of the two graphs to tell if they are isomorphic.

Examples of graph invariants
1. $|V|$
2. $|E|$
3. Degree sequence (This is a list of all the vertex degrees in non-decreasing order)
4. Planarity
5. Bipartitness
6. Determinant of Adjacency Matrix
7. Eigenvalues of the Adjacency Matrix

Apart from this another useful thing to look for is:
- Number of cycles of some length $n$

### Petersen Graph:
The petersen graph is "a remarkable configuration that **serves as a counterexample to many optimistic predictions about what might be true for graphs in general**."
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

Q: How many edges are there in a k-regular graph with n vertices?
A: $\frac{nk}{2}$. Since each of the $n$ vertices have degree $k$, the sum of degrees is $nk$. From the handshaking lemma, we thus know that the number of edges is $\frac{nk}{2}$.

### Complete graph
A graph in which all pairs of distinct vertices are adjacent. The complete graph with p vertices is denoted $K_p$ where $p \geq 1$.

### Bipartite graph
A graph in which the vertices can be partitioned into two sets A and B, so that all edges join a vertex in A to a vertex in B, is called a bipartite graph, with bipartition (A,B).

Q: What is a small non-bipartite graph
A: $K_3$ 

The complete bipartite graph $K_{m, n}$ has all vertices in A adjacent to all vertices in B, with $|A| = m$, $|B| = n$.

Q: What is the smallest bipartite graph that cannot be drawn on the plane without edge crossings?
A: $K_{3, 3}$

Q: How many edges are there in $K_{m, n}$
A: $mn$

### n-cube
For $n \geq 0$ the n-cube is the graph whose vertices are the $\{0, 1\}$- strings of length n, and two strings are adjacent if and only if they differ in exactly one position.

Q: How many vertices are in the n-cube?
A: $2^n$, the number of binary strings of length $n$.

Q: Is the n-cube regular?
A: Yes, it is n-regular. For each string $S$, we can get a neighbour by changing one of the $n$ positions.

Q: How many edges does the n-cube have?
A: Since there are $2^n$ vertices each with degree $n$, the sum of degrees is $2^n \cdot n$. By the handshaking lemma, the number of edges is $2^{n - 1} \cdot n$.

Q: Is the n-cube bipartite?
A: Yes.
Let $A$ be the set of all binary strings of length $n$ with an odd number of $0$'s.
Let $B$ be the set of all binary strings of length $n$ with an even number of $0$'s.
We see that $(A, B)$ partitions the vertices of the n-cube .
Take an arbitrary edge joining $s$ and $t$. By definition, $t$ can be obtained from from $s$ by changing exactly one position : either change a $0$ to a $1$, or change a $1$ to a $0$. In the first case, the number of $0$'s decreases by $1$. In the second case, the number of $0$'s increases by $1$. In either case, the parity of the number of $0$'s changes, so this parity for $s$ and $t$ must be different. Hence $st$ joins $A$ to $B$, and the n-cube is bipartite.

#### Recursive construction of the n-cube
1. We make $2$ copies of the n-cube
2. Add $0$ in front of all strings of one copy, $1$ for the other copy
3. Join corresponding copies of the vertices with edges.


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

**Proof:**
We prove by strong induction on $k$ on the statement "If there is a $u,v$ walk with k-repeated vertices, then there is a $u,v$ path."

**Base Case:**
When $k = 0$, a $u, v$ walk with $0$ repeated vertices is a $u, v$ path.

**Induction Hypothesis:**
If there is a $u, v$ walk with less than $k$ repeated vertices, then there is a $u, v$ path.

**Induction Step:**
Suppose there is a $u, v$ walk with $k$ repeated vertices $v_0, v_1, v_2, \dots v_t$ where $v_0 = u$, $v_t = v$. Let $w$ be a repeated vertex. Let $i$ and $j$ be the smallest and largest index respectively where $w = v_i = v_j$. Then, $v_0, v_1, v_2, \dots, v_i (= v_j), v_{j + 1}, \dots, v_t$ is also a $u, v$ walk. But, $w$ is no longer repeated, so this walk has lesser than $k$ repeated vertices. By induction, this is a $u, v$ path.
$\blacksquare$

**Alternate Proof**:
Among all $u, v$ walks, pick one $v_0, v_1, \dots, v_k$ that is shortest in length. If this walk has no repeated vertices, then it is a $u, v$ path and we are done. Otherwise, there exists $i < j$ such that $v_i = v_j$. Then, $v_0, v_1, v_2, \dots, v_i (= v_j), v_{j + 1}, \dots, v_k$ is shorter than our shortest $u,v$ walk, contradiction. Hence, a $u, v$ path exists.

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

**Proof:**
Let $v_0, v_1, \dots, v_k$ be a longest path in $G$. Since every vertex has degree at least 2, WLOG let vertex $v_0$ have $v_1$ as a neighbour. Let $v_0$ also have another neighbour, say $x$. If $x$ is not on the path, then $x, v_0, v_1, \dots, v_k$ is a path in $G$ longer than our longest path. This however is a contradiction. Thus, $x = v_i$ for some $i \geq 2$, and $v_0, v_1, \dots, v_i, v_0$ is a cycle in $G$. 
$\blacksquare$

Note: the converse of this theorem is not necessarily true.

### Girth
The girth of a graph $G$ is the length of the shortest cycle in $G$, and is denoted by $g(G)$.

Generally, girth can be a measure of the density of a graph. High girth usually means lower average-degree.

### Hamilton Cycle
A spanning cycle in a graph is known as a Hamilton cycle.

### Connected
A graph $G$ is connected if, for each two vertices $x$ and $y$, there is a path from $x$ to $y$.

### Theorem 4.8.2.
Let $G$ be a graph and let $v$ be a vertex in $G$. If for each vertex $w$ in $G$ there is a path from $v$ to $w$ in $G$, then $G$ is connected.

Consequence: We only need to check $|V(G)| - 1$ paths to show connectedness.

**Proof**:
Let $x, y \in V(G)$. By assumption, there exists a $x,v$ path and a $y,v$ path. By Corollary 4.6.3, there exists an $x, y$ path. Hence, G is connected.

Q: Show that the n-cube is connected.
A: Let $v_0$ be the string of $n$ $0$'s. Let $x$ be any string of length $n$. Suppose $x$ has $k$ $1$'s at positions $i_1, \dots, i_k$. We produce $k$ strings as follows: $v_j$ is the string of length $n$ with exactly $j$ $1$'s, at positions $i_1, \dots, i_j$. Then, $v_j$ and $v_{j + 1}$ differ in exactly one position, $i_{j + 1}$. So, $v_j v_{j + 1}$ is an edge.Then, $v_0, v_1, v_2, \dots, v_k (= x)$ is a $v_0, x$ path. By theorem 4.8.2, the n-cube is connected!

### Component
A component of $G$ is a subgraph $C$ of $G$ such that
- $C$ is connected
- No subgraph of $G$ that properly contains $C$ is connected.

### Cuts
If we are given a partition $(X,Y)$ of $V(G)$ such that there are no edges having an end in $X$ and an end in $Y$ , then there is no path from any vertex in $X$ to any vertex in $Y$ . So, if $X$ and $Y$ are both nonempty, $G$ is not connected. Given a subset $X$ of the vertices of $G$, the cut induced by $X$ is the set of edges that have exactly one end in $X$.

### Theorem 4.8.5.
A graph $G$ is not connected if and only if there exists a proper nonempty subset (the set is neither empty nor the whole set itself) X of $V(G)$ such that the cut induced by $X$ is empty.

**Proof:**
$\implies$
Suppose that $G$ is not connected and let $C$ be a component of $G$. Consider the partition $(X, Y)$ of $V(G)$ where $X = V(C)$ and $Y = V(G) \setminus V(C)$. Since $C$ is connected and $G$ is not, $X$ is a proper nonempty subset of $V(G)$. Since $C$ is a component, if the vertex $y$ is adjacent to a vertex in $C$, then $y \in V(C)$. Hence the cut induced by $X$ is empty.
$\impliedby$
Let us assume that there exists a proper nonempty subset $X$ of $V(G)$ such that the cut induced by $X$ is empty. Let us for the sake of contradiction assume that $G$ is connected. Let us choose vertices $u \in X$ and $v \in V(G) \setminus X$. Since $G$ is connected, there exists a path $x_0, x_1, x_2, \dots, x_n$ from $u$ to $v$. Choose $k$ as large as possible such that $x_k \in X$. Since $x_n = v \notin X$, $k < n$, the edge $x_k x_{k + 1}$is in the cut induced by $X$ and the cut is infact not empty. However, this is a contradiction! Thus our assumption is incorrect, and $G$ is in fact not connected.
$\blacksquare$

### Eulerian Circuit
An Eulerian circuit of a graph $G$ is a closed walk that contains every edge of $G$ exactly once.

### Theorem 4.9.2.
Let $G$ be a connected graph. Then $G$ has an Eulerian circuit if and only if every vertex has even degree.

### Bridge
An edge $e$ of $G$ is a bridge if $G - e$ has more components than $G$.

### Lemma 4.10.2.
If $e = \{x, y\}$ is a bridge of a connected graph $G$, then $G - e$ has precisely two components; furthermore, $x$ and $y$ are in different components.

### Theorem 4.10.3. 
An edge $e$ is a bridge of a graph $G$ if and only if it is not contained in any cycle of $G$.

### Corollary 4.10.4.
If there are two distinct paths from vertex $u$ to vertex $v$ in $G$, then $G$ contains a cycle.

### Tree
A tree is a connected graph with no cycles.

If connectedness is not required, then the graph is a forest (has multiple trees).

### Forest
A forest is a graph with no cycles.

### Lemma 5.1.3.
If $u$ and $v$ are vertices in a tree $T$ , then there is a unique $u, v$-path in $T$.

**Proof**:
Let us for the sake of contradiction assume that there exist two unique $u, v$ paths between $x$ and $y$ in $T$. Let these two paths be $P_1$ and $P_2$. Since $P_1$ and $P_2$ are unique paths, we know that there needs to be at least one edge in one path and not the other. WLOG, let us assume that the edge $u,v$ is in $P_1$. If we removed the edge $u, v$, since $T$ is a tree and every edge is a bridge (since none of the edges are in a cycle), we should end up with two components. Thus, there should technically not exist a path between $u$ and $v$. However, notice that if we went from $u$ to $x$ following $P_1$, then used $P_2$ to go to $y$, then went to $v$ from $y$, then we would have a valid path to $u$ to $v$. However, this is a contradiction since by definition $u$ and $v$ should be in different components. Thus, our assumption is wrong and there exists only one unique path.

### Lemma 5.1.4.
Every edge of a tree $T$ is a bridge.

### Theorem 5.1.5.
If $T$ is a tree, then $|E(T)| = |V(T )| - 1$.

### Corollary 5.1.6.
If $G$ is a forest with $k$ components, then $|E(G)|=|V(G)|- k$.

### Leaf
A leaf in a tree is a vertex of degree 1.

### Theorem 5.1.8.
A tree with at least two vertices has at least two leaves.

### Lemma
Every Tree is bipartite.

### Spanning Trees
A spanning subgraph which is also a tree is called a spanning tree.

The reason that spanning trees are important is that, of all the spanning subgraphs, they have the fewest edges while remaining connected

### Theorem 5.2.1.
A graph $G$ is connected if and only if it has a spanning tree.

### Corollary 5.2.2.
If $G$ is connected, with $p$ vertices and $q = p - 1$ edges, then $G$ is a tree.

### Theorem 5.2.3.
If $T$ is a spanning tree of $G$ and $e$ is an edge not in $T$ , then $T + e$ contains exactly one cycle $C$. Moreover, if $e'$ is any edge on $C$, then $T + e - e'$ is also a spanning tree of $G$.

### Theorem 5.2.4.
If $T$ is a spanning tree of $G$ and $e$ is an edge in $T$ , then $T - e$ has 2 components. If $e'$ is in the cut induced by one of the components, then $T - e + e'$ is also a spanning tree of $G$.

### Lemma 5.3.1. 
An odd cycle is not bipartite.

An odd cycle is a cycle with an odd number of vertices.

### Theorem 5.3.2.
A graph is bipartite if and only if it has no odd cycles.


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
- The subgraph we get from a cycle by deleting one edge is called a path.
- A cycle with n edges is called an n-cycle or a cycle of length n.
- The shortest possible cycle in a graph is a 3-cycle.
- There are 2n closed walks of length n associated with a given n-cycle.

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

**Proof:**
Consider the graph with cycle $C: x_1, x_2, \dots, x_k, x_1$. Let us assume that this cycle is bipartite. To classify the graph as bipartite, we need to partition all the vertices into two sets (say $A$ and $B$). Since we are dealing with an odd cycle, we know that $k$ is odd. WLOG, let $x_1$ be in $A$. Then, we can say that $x_2$ is in $B$, $x_3$ is in $A$, $x_4$ is in $B$, etc. Notice that it is easy to notice that we've put $x_i$ where $i$ is odd in $A$, and $x_i$ where $i$ is even in $B$. Since we know that $k$ is odd, we can safely put $x_k$ in $A$. However, $x_k$ and $x_1$ are adjacent to each other, and both belong in the same partition $A$. This is a contradiction. Thus, our assumption that an odd cycle is bipartite is wrong and an arbitrary odd cycle is NOT bipartite.

### Theorem 5.3.2.
A graph is bipartite if and only if it has no odd cycles.

**Proof:**
$(\implies)$
Let us assume that a graph $G$ is bipartite. From Lemma 5.3.1, we know that an odd cycle is not bipartite. Thus, we know that graph $G$ can not have odd cycles.
Hence Proved.

$(\impliedby)$
We need to prove that If a graph has no odd cycles, then it is bipartite.
We can alternatively also prove the contrapositive: If a graph is not bipartite, then it has an odd cycle.

Let us assume that the graph $G$ is not bipartite. Since the graph $G$ is not bipartite, at least one of its components $H$ is not bipartite. Since $H$ is a component (is connected), we know that there exists a spanning tree $T$ inside $H$. We know that trees are bipartite, so we can create a bipartition $A, B$ of $T$. Since $H$ is not bipartite, we know that $(A, B)$ is not a bipartition of $H$. Thus, we know that there exists an edge $u, v$ in $H$ such that both $u$ and $v$ are in $A$ or both are in $B$. Since we can swap when needed, let us take $A$ for now.
Since $T$ is spanning and connected, there must exist a $u, v$ path $P$ in $T$ of the form $u, x_1, x_2, x_3, \dots, x_n, v$. Note that since $u$ is in the partition $A$ and $T$ is bipartite, $x_1, x_2, x_3, \dots, x_n$ must alternate between $B$ and $A$. We can also notice that all $x_i$ where $i$ is even are in $A$ and all $x_i$ where $i$ is odd are in $B$. Since $v$ is in $A$, we know that $x_n$ must be in $B$. Thus, $n$ is odd! Adding $u$ and $v$, the $u, v$ path comes out to have $n + 2$ vertices (which is also odd).
Now, consider the cycle created by $P$ and the edge $uv$. This cycle would look something like this: $u, x_1, x_2, \dots, x_n, v, u$. Since $n$ is odd, we know that the cycle has even vertices, and is thus of odd length. Thus, the graph has an odd cycle. Hence Proved.


### Planar Graphs
A graph $G$ is **planar** if it has a drawing in the plane so that its edges intersect only at their ends, and so that no two vertices coincide. The actual drawing is called a **planar embedding** of $G$, or a planar map

### Face
A **face** of a planar embedding is a connected region on the plane (not separated by the edges).

### Boundary
A **boundary** of a face is a subgraph of all vertices and edges that touch the face. Two faces are adjacent if they share at least one edge in their boundaries.

### Boundary Walk
For a connected planar embedding, the boundary walk of a face is a closed walk once around the perimeter of the face boundary. The degree of a face is $f$ is the length of its boundary walk, denoted by $deg(f)$.

**Note:** If $G$ is not connected, the boundary walk may be disconnected. If so, we take a boundary walk around each component and sum them up to get its degree.

### Faceshaking Lemma
Let $G$ be a planar graph with a planar embedding where $F$ is the set of all faces. Then, $$\sum_{f \in F} \deg(f) = 2|E(G)|$$

**Proof:**
Each edge contributes two to the sum of face degrees, one for each side of the edge.

### Corollary 7.1.3.
If the connected graph $G$ has a panar embedding with $f$ faces, the average degree of a face in the embedding is $$ \frac{2E|G|}{f} $$
### Lemma
In a planar embedding, $e$ is a bridge if and only if the two sides of $e$ are in the same face.

### Jordan Curve Theorem
Every planar embedding of a cycle separates the plane into two parts, one on the inside, and one on the outside.

### Euler's Formula
Let $G$ be a connected planar graph with $n$ vertices and $m$ edges. Consider a planar embedding of $G$ with $s$ faces. Then, $$n - m + s = 2$$
**Consequence**: For any planar embedding with $s$ faces, $s = 2 - n + m$. 
$n$, $m$ are constant for a graph.

**Proof:**
We fix the number of vertices $n$. We prove by induction on the number of edges $m$.

**Base Case:**
The graph is connected, so it has a spanning tree which has $n - 1$ edges. Thus, our base case is $m = n - 1$. A connected graph with $n - 1$ edges is a Tree. Any planar embedding of a tree has $1$ face. Thus, $s = 1$. So, $n - m + s = n - (n - 1) + 1 = 2$.

**Inductive Hypothesis:**
Assume that Euler's Formula holds for any conneted planar graph with $n$ vertices and $m - 1$ edges.

**Inductive Step**:
Consider a connected planar graph with $n$ vertices, $m$ edges, and $s$ faces. Let $e$ be an edge that is not a bridge. Then, $G - e$  is connected by definition. Also, $G - e$ is a planar since we can remove $e$ from a planar embedding of $G$ to get a planar embedding of $G - e$. And $G - e$ has $m - 1$ edges. So, Euler's Formula holds for $G - e$ by induction.

Since $e$ is not a bridge, the two sides of the edge are different faces. Thus, when we remove $e$ from the planar embedding of $G$ to obtain the planar embedding of $G - e$, the newly obtained planar embedding has 1 less face since the two faces on the different sides of the edge are now merged into one. Thus, embedding of $G - e$ has $s - 1$ faces. By Euler's formula, we can say
$$n - (m - 1) + (s - 1) = 2$$
This equation equates to $n - m + s = 2$, thus showing that Euler's formula holds for $G$.
$\blacksquare$


**Note:** If $G$ has $c$ components, then Euler's formula becomes $$n - m + s = 1 + c$$
### Lemma 7.5.1
If $G$ contains a cycle, then in a planar embedding of $G$, the boundary of each face contains a cycle.

**Proof:**
Since $G$ has a cycle, it has more than one face. Therefore, every face $f$ is adjacent to at least one more face say $g$.
Let $e_1 = {v_0, v_1}$ be an edge that is incident with both $f$ and $g$. Let $H$ be the component in the boundary of the face $f$ containing edge $e_1$. Let
$$W_f = (v_0, e_1, v_1, e_2, v_2, \dots, v_{n - 1}, e_n, v_0)$$
be the boundary walk of $H$. Since the edge $e_1$ is incident with both $f$ and $g$, it is contained in $W_f$ exactly once.
The edge $e_1$ is not a bridge of $H$ because 
$$v_1, e_2, v_2, \dots, v_{n - 1}, e_n, v_0$$
is a walk from $v_1$ to $v_0$ in $H - e_1$. Thus, by 4.10.3, $H$ contains a cycle.
$\blacksquare$

#### Lemma 7.5.2
Let $G$ be a planar embedding with $p$ vertices and $q$ edges. If each face of $G$ has degree at least $d$, then $(d - 2)q \leq d (p - 2)$.

**Proof:**
We first deal with the case when $G$ is connected. Let $f_1, f_2, d_3, \dots, f_s$ be the faces of $G$. Thus, applying lemma 7.1.2, we get
$$2q = \sum_{i = 1}^{s} \deg(f_i) \geq s(d)$$
Also, by euler's formula we know that $p - q + s = 2$. We can rewrite this to obtain
$$
s = 2 - p + q
$$
Combining these two equations, we obtain
$$
\begin{align*}
2q &\geq s(d) \\
&= d (2 - p + q) \\
&= 2d - dp + dq \\
d(p - 2) &= dq - 2q \\
\frac{d(p - 2)}{d - 2} &= q
\end{align*}
$$
If $G$ is not connected, [incomplete proof].
$\blacksquare$

### Theorem 7.5.3
In a planar graph $G$ with $p \geq 3$ vertices and $q$ edges, we have
$$
q \leq 3p - 6
$$
**Proof:**
If $G$ does not contain cycle, then $G$ is a forest. In that case, we know from our corollary where $|E(G)| = |V(G)| - k$.
$$
q \leq p - 1
$$
and since $p \geq 3$, we also know that $p - 1 \leq 3p - 6$. We can easily verify this by plotting out the graph.
Thus, we can say
$$q \leq p - 1 \leq 3p - 6$$
In the other case, $G$ does contain a cycle. In that case, by Lemma 7.5.1, we know that every boundary face has contains a cycle. Since each cycle has a length of at least 3, each face has a degree of at least 3. We can thus use Lemma 7.5.2 to say that
$$\begin{align*}
q &\leq \frac{d(p - 2)}{(d - 2)} \\
&= \frac{3(p - 2)}{3 - 2} \\
&= 3(p - 2) \\
&= 3p - 6
\end{align*}$$
$\blacksquare$

### Corollary 7.5.4
$K_5$ is not planar

**Proof:** $|E(K_5)| = {5 \choose 2} = 10$

From Theorem 7.5.3, we know that for planar graphs with $p \geq 3$,  $q \leq 2p - 6$. In this case, theorem tells us that $q \leq 3(5) - 6) = 9$. However, $10 > 9$, so $K_5$ is not planar.

### Corollary 7.5.5
A planar graph has a vertex of degree at most $5$.

**Proof:** This is naturally true when $p \leq 2$. Otherwise, if $p \geq 3$, then theorem 7.5.3 tells us that $$q \leq 3p - 6$$
We can rewrite this as 
$$\frac{2q}{p} \leq 6 - \frac{12}{p}$$
This tells us that the average degree of the graph is lesser than 6. Thus, there needs to be at least one vertex of degree $\leq 5$.

### Theorem 7.5.6
In a bipartite planar graph $G$ with $p \geq 3$ vertices and $q$ edges, we have
$$q \leq 2q - 4$$

**Proof:**
If $G$ does not contain a cycle, then $G$ is a forest. In this case, we know from our corollary where $|E(G)| = |V(G)| - k$ that
$$
q \leq p - 1
$$
and since $p \geq 3$, we also know that $p - 1 \leq 2p - 4$. We can easily verify this by plotting out the graph.
Thus, we can say
$$q \leq p - 1 \leq 2p - 4$$

The other case is when $G$ contains a cycle. In this case, by lemma 7.5.1, every face boundary contains a cycle. Since $G$ is bipartite, we know that it doesn't have a cycle of length $3$. Thus, the minimum length of a cycle in $G$ is $4$, and thus each face a degree at least $4$. By Lemma 7.5.2, we can thus say
$$ \begin{align*}
q &\leq \frac{4(p - 2)}{4 - 2} \\
&\leq 2(p - 2) \\
&\leq 2p - 4
\end{align*} $$
Hence Proved

### Lemma 7.5.7
$K_{3, 3}$ is not planar.

**Proof:**
We have $|E(K_{3, 3})| = 3 \cdot 3 = 9$

Theorem 7.5.6 tells us that a bipartite planar graph $G$ with $p \geq 3$ and $q$ edges should have $q \leq 2p - 4$. In this case, since $p = 6$, we should have $q \leq 12 - 4 = 8$. However, $q = 9$. Thus $K_{3, 3}$ is not planar.

### Kuratowski’s Theorem (Theorem 7.6.1)
A graph is not planar if and only if it has a subgraph that is an edge subdivision of $K_5$ or $K_{3, 3}$.

Main Idea:
An edge subdivision of a graph G is obtained by applying the following operation, independently, to each edge of G: replace the edge by a path of length 1 or more; if the path has length $m > 1$, then there are $m - 1$ new vertices and $m - 1$ new edges created; if the path has length $m = 1$, then the edge is unchanged.

The operation of edge subdivision does not change planarity: if G is a planar graph, then all edge subdivisions of G are planar; if G is nonplanar, then all edge subdivisions of G are nonplanar. Similarly, note that if a graph G has a nonplanar subgraph, then G is nonplanar.

From these observations, we can immediately conclude that if a graph G has a subgraph isomorphic to an edge subdivision of $K_{3,3}$ or $K_5$, then G is nonplanar.


### k-colouring
A **k-colouring** of a graph $G$ is a function from $V(G)$ to a set of size $k$ (whose elements are called **colours**), so that adjacent vertices always have different colours. A graph with a k-colouring is called a **k-colourable** graph.

### Theorem 7.7.2
A graph is 2-colourable if and only if it is bipartite.

### Theorem 7.7.3
$K_n$ is n-colourable and not k-colourable for any $k < n$.

### Theorem 7.7.4
Every planar graph is 6-colourable.

**Proof:**
The proof is by induction on the number of $p$ vertices.

**Base Case:**
$p = 1$. All graphs of one vertex are 6-colourable, so the result is true for $p = 1$.

**Inductive Hypothesis:**
Let us assume that all graphs where $p \leq k$ and $k \geq 1$ are 6-colourable.

**Inductive Step:**
Consider a graph with $p = k + 1$ vertices. From Corollary 7.7.5, we know that since $G$ is planar, $G$ has a vertex $v$ of degree at most $5$. Suppose we remove vertex $v$ and all edges incident to it. We then end up with a subgraph $H$ which has $k$ vertices. From our inductive hypothesis, we know that graph $H$ is 6-colourable. Now, we find a 6-colouring of $H$. There are at most $5$ vertices adjacent to $v$ in $G$, so these vertices are assigned at most $5$ different colours. Thus, there is at least one of the $6$ colours remaining. We can assign one of those colours to $v$, so that $v$ has a different colour than all of its adjacent vertices in $G$. Thus, we have a 6-colouring for $G$ and the inductive hypothesis is true for $k + 1$. Thus, hypothesis is true by POMI.

### Contracting Edges
Let $G$ be a graph and let $e = \{x, y\}$ be an edge of $G$. The graph $G - e$ obtained from $G$ by contracting the edge $e$ is the graph with vertex set $V(G) \setminus \{ x, y\} \cup {z}$, where $z$ is a new vertex, and edge set.
$$ \{ \{u, v \}\in E(G) : \{u, v\} \cap\{x, y\} = \phi\} \cup \{\{u, z\} : u \notin \{x, y\} , \{u, w\} \in E(G) \,\text{for some} \,w \in \{x, y\} \} $$

### Theorem 7.7.6
Every planar graph is 5-colourable. [check cn for proof]

### Theorem 7.7.7
Every planar graph is 4-colourable. [very hard proof. not in scope of course]

### Dual Planar Maps
Given a connected planar embedding $G$, the dual $G^d$ is a planar embedding constructed as follows: $G^d$ has one vertex for each face of $G$. Two vertices of $G^d$ are joined by an edge whenever the corresponding faces of $G$ have an edge in common (one side for each face), and the edge in $G^d$ is drawn to cross this common boundary edge in $G$. 

Key facts about relationship b/w $G$ and $G^d$:
- A face of degree $k$ in $G$ becomes a vertex of degree $k$ in $G^d$
- A vertex of degree $j$ in $G$ becomes a face of degree $j$ in $G^d$
- $(G^d)^d = G$ 

Note that a bridge in $G$ gives an edge in $G^d$ between a vertex and itself (such an edge is called a loop), and more than one edge between two faces in $G$ gives more than one edge between a pair of vertices (these are together called a multiple-edge). Thus, $G^d$ may be a multigraph, rather than a graph.

This effectively shows how the four-colouring theorem for colouring vertices in planar graphs is equivalent to the Four Colour Theorem for colouring faces in Planar Embeddings via duality.

### Matching
A **matching** in a graph $G$ is a set $M$ of edges of $G$ such that no two edges in $M$ have a common end.

We say that a vertex $v$ of $G$ is **saturated** by $M$, or that $M$ saturates $v$, if $v$ is incident with an edge in $M$.

A special kind of maximum matching is one having size $\dfrac{p}{2}$, that is, one that saturates every vertex, called a **perfect matching**.

### Alternating Path
We say that a path $v_0, v_1, v_2, \dots, v_n$ is an alternating path with respect to $M$ if one of the following is true:
- $\{v_i, v_{i + 1}\} \in M$ if $i$ is even and $\{v_{i}, v_{i + 1}\} \notin M$ if $i$ is odd
- $\{v_i, v_{i + 1}\} \notin M$ if $i$ is even and $\{v_{i}, v_{i + 1}\} \in M$ if $i$ is odd

### Augmenting Path
An augmenting path with respect to $M$ is an alternating path joining two distinct vertices neither of which is saturated by $M$.

### Lemma 8.1.1
If $M$ has an augmenting path, it is not a maximum matching.

### Cover
A cover of a graph $G$ is a set C $of$ vertices such that every edge of $G$ has at least one end in $C$.

### Lemma 8.2.1
If $M$ is a matching of $G$ and $C$ is a cover of $G$, then $|M| \leq |C|$

### Lemma 8.2.2
If $M$ is matching and $C$ is a cover and $|M|=|C|$, then $M$ is a maximum matching and $C$ is a minimum cover.

Given a matching $M$ and an augmenting path with set $E(P)$, the new matching $M'$ is:
$$M' = [M \cup (E(P) \setminus M)] \setminus (E(P) \cap M)$$

### König’s Theorem
In a bipartite graph the maximum size of a matching is the minimum size of a cover.

It might seem trivial to state this after we've seen Lemma 8.2.1, by which $|M| \leq |C|$, but that is not the case. Though $|M| = |C|$ or the maximum size of a matching is the same size as a minimum cover occurs is true for bipartite graphs, it is not the case for all graphs. Example: A minimum cover for $K_p$ has size $p - 1$ and a maximum matching has size $\lfloor \dfrac{p}{2} \rfloor$.

Let $X_0$ be the set of vertices in $A$ not satured by $M$, and let $Z$ denote the set of vertices in $G$ that are joined by a vertex in $X_0$ by an alternating path.If $v \in Z$, then let $P(v)$ denote the alternating path that joins $v$ to $X_0$. Now, define
- $X = A \cup Z$
- $Y = B \cup Z$

Note that any alternating path has $P(v)$ has even length if $v \in X$ and odd length if $v \in Y$. Since the first edge in any alternating path starts from an unsatured vertex, we know that the first edge is not in a matching. The second edge, and every alternate edge from there is in a matching.
- If $v \in X$, then the last edge of $P(v)$ is in $M$
- if $v \in Y$, then the last edge of $P(v)$ is not in $M$.

### Lemma 8.3.2
Let $M$ be a matching of a bipartite graph $G$ with bipartition $A, B,$ and let $X$ and $Y$ be defined as above. Then:
1. There is no edge of $G$ from $X$ to $B \setminus Y$.
2. $C = Y \cup (A \setminus X)$
3. There is no edge of $M$ from $Y$ to $A \setminus X$.
4. $|M| = |C| - |U|$ where $U$ is the set of unsatured vertices in $Y$.
5. There is an augmenting path to each vertex in $U$.

**Proof:**
1. Suppose that this is false. In that case, for a vertex $u \in X$ and $v \in B \setminus Y$, there exists an edge $e: \{u, v\}$ in the graph $G$. However, this would mean that we could add the edge $e$ to the even alternating path $P(u)$ from $X_0$ to get an odd alternating path to $v$, which would mean that $v \in Y$, a contradiction.
2. The only edges that are not adjacent to an element in $C$ is edges that go from a vertex in $X$ to a vertex in $B \setminus Y$. From 1), we know that there is no edge of $G$ from $X$ to $B \setminus Y$. Thus, our cover is valid and covers all edges.
3. Suppose that this is false. In that case, for a vertex $u \in Y$ and $v \in A \setminus X$, there exists an edge $e : \{ u, v \}$ in the graph $G$. However, this would mean that we could add the edge $e$ to the odd alternating path $P(u)$ from $X_0$ to get an even alternating path to $v$, which would mean that $v \in X$, a contradiction.
4. From 1) and 3), we know that every edge in $M$ joins a vertex in $X$ to a vertex in $Y$ or joins a vertex in $A \setminus X$ to a vertex in $B \setminus Y$. The number of edges of the first type is $|Y| - |U|$. Also, since $X_0 \subset X$, every vertex in $A \setminus X$ is saturated. Thus, the number of edges of the second type is $|A \setminus X|$. It follows that
   $$|M| = |Y| - |U| + |A \setminus X|$$Note that from 2), we know that $|C| = |Y| + |A \setminus X|$. Thus, we can finally say
   $$|M| = |C| - |U|$$
5. if $U$ is not empty, then we know that all $v \in U$ are unsaturated vertices. Thus, $P(v)$ is an augmenting path.


### Proof of König’s Theorem
Assume that $M$ is the maximum matching of a graph $G$. Then, by Lemma 8.1.1, and 5) of Lemma 8.3.2, we know that $U$ should be empty. Thus $|U| = 0$. Thus, from 2) and 4) of Lemma 8.3.2, we know that $C = Y \cup (A \setminus X)$, and that $|M| = |C|$. From Lemma 8.2.2, our result follows.


### Bipartite Graph Edges/Matching Result
Let $G$ be a bipartite graph with bipartition $A, B,$ where $|A| = |B| = n$. Prove that if $G$ has $q$ edges, then $G$ has a matching of size at least $\dfrac{q}{n}$.

**Proof**:
Suppose that $C$ is a cover of $G$. There can be at most $n$ edges incident to a vertex in $C$. Thus, the total number of edges incident to $C$ will at most be $n |C|$. However, $C$ is a cover so we know that every edge in $G$ is incident to $C$. Thus, we know that $n |C| \geq q$. Hence Proved


### Hall's Theorem (Theorem 8.4.1)
A bipartite graph $G$ with bipartition $A,B$ has a matching saturating every vertex in $A$, if and only if every subset $D$ of $A$ satisfies $$|N(D)| \geq |D|$$
**Proof:**
$(\implies)$ 
Let us assume that $G$ does have a matching $M$ saturing ever vertex in $A$. Then, for any subset $D$ of $A$, $N(D)$ contains the other end of the edge of $M$ incident with $v$ for every $v \in D$, and these vertices must all be distinct because matchings don't share vertices. Thus, $|N(D)| \geq |D|$.

$(\impliedby)$
We prove the contrapositive. Thus, we prove that A bipartite graph $G$ with bipartition $A, B$ doesn't have a matching saturating every vertex in $A$ if and only if there exists a subset $D$ of $A$ that satisfies $|N(D)| \geq |D|$.

Let us assume that $G$ does not have a matching saturing every vertex in $A$. Thus, 
every subset $D$ of $A$ satisfies $|N(D) \geq |D|$ for $G$. Let $M$ be a maximum matching in $G$. Then, $|M| < |A|$. By Konig's Theorem, there must be a cover $C$ such that $|M| = |C|$. Thus, $|C| < |A|$.

Now, consider the 4 sets: $A \cap C$, $A \setminus C$, $B \cap C$, $B \setminus C$. Note how there can not be an edge between $A \setminus C$ and $B \setminus C$ because $C$ is a cover and there can not be an edge that isn't incident with our valid cover. Thus, all neighbours of $A \setminus C$ are in $B \cap C$, that is, $N(A \setminus C) \subset (B \cap C)$. Now, $C = (A \cap C) \cup (B \cap C)$ and $A = (A \cap C)  \cup (A \setminus C)$. Also, we know that $|C| < |A|$. Thus, we know that 
$$|A \cap C| + |B \cap C| < (A \cap C) + (A \setminus C) $$
We can write this as
$$|B \cap C| < (A \setminus C)$$
However, note that we showed earlier that $N(A \setminus C) \subset (B \cap C)$. Thus, since for $D = (A \setminus C)$, we can say
$$|N(D)| < |D|$$
We have proved the hypothesis
$\blacksquare$

### Hall’s SDR Theorem (Corollary 8.5.1)
This theorem is nothing but a restatement of Theorem 8.4.1 in the language of SDR’s.

The collection $Q_1, Q_2, \dots, Q_n$ of subsets of the finite set $Q$ has an SDR if and only if for every subset $J$ of $\{ 1, 2, 3, \dots, n\}$, we have $$|\sum_{i \in J}Q_i| \geq |J|$$
### Corollary 8.6.1
A bipartite graph with bipartition $A, B$ has a perfect matching if and only if $|A| = |B|$ and every subset $D$ of $A$ satisfies $$|N(D)| \geq |D|$$
### Theorem 8.6.2
If $G$ is a k-regular bipartite graph with $k \geq 1$, then $G$ has a perfect matching.

**Proof:**
Let $A, B$, be a bipartition of $G$. Then, since every edge has one end in $A$ and the other end in $B$, we have $\sum_{v \in A} \deg(v) = \sum_{v \in B} \deg(v)$. It follows that $k |A| = k |B|$, and therefore, since $k > 0$, that $|A = |B|$. Now, let $D \subset A$. Then, since every edge incident with a vertex in $D$ has its other end in $N(D)$, we have $$\sum_{v \in D} \deg(v) \leq \sum_{v \in N(D)} \deg(v)$$
It follows that $k |D| \leq k |N(D)|$, and therefore (again, since $k > 0$) that $|N(D)| \geq |D|$. Now, by Corollary 8.6.1, $G$ has a perfect matching.

Note: this theorem works even if $G$ contains multiple edges.


### Edge-colouring
An edge k-colouring of a graph $G$ is an assignment of one of a set of $k$ colours to each edge of $G$ so that two edges incident with the same vertex are assigned different colours

### Theorem 8.7.1
A bipartite graph with maximum degree $d$ has an edge $d$-colouring.

### Lemma 8.7.2
Let $G$ be a bipartite graph having at least one edge. Then, $G$ has a matching saturating each vertex of maximum degree. 

**Proof**:
Let $A, B$, be a bipartition of $G$ and $K = \{ v \in V : \deg(v) = d\}$. Let $M$ be a maximum matching that leaves as few elements of $K$ unsaturated as possible. If $M$ saturates all elements of $K$, we are finished. Otherwise, we may assume by interchanging $A$ with $B$ if necessary, that there is a vertex in $A \cap K$ that is not saturated by $M$. Apply the XY-construction, except that we define $X_0$ to consist only of the unsaturated vetices in $A \cap K$. Then $Y$ contains no unsaturated vertex, since $M$ is a maximum matching.

Suppose there is a vertex $w \in X$ having degree less than $d$. Consider the alternating path $P(w)$. It has even length. If we replace the edges of $M$ that are in $P(w)$ by those that are not, we get another maximum matching, but one that leaves fewer elements of $K$ unsaturated, a contradiction to the choice of $M$. So, every vertex in $X$ has degree $d$.

By the construction and the fact that $M$ is maximum, for every $u \in Y$ there is an edge of $M$ joining $u$ to some vertex in $x$. Since $X$ contains at least one unsaturated vertex, $|X| > |Y|$. Moreover, again by the construction, there is noe dge from $X$ to $B \setminus Y$, so $N(X) \subset Y$. Therefore, 
$$d|Y| < d|X| = \sum_{v \in X} \deg(v) \leq \sum_{v \in Y} \deg(v) \leq d|Y|$$
a contradiction. Therfore, there are no vetices in $K$ not saturated by $M$, and we are done. 
$\blacksquare$


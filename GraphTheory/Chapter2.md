- [Chapter 2 Path and Cycles](#chapter-2-path-and-cycles)
  - [Definitions](#definitions)

# Chapter 2 Path and Cycles

## Definitions

👉 Walk(途径)

- a sequence of edges of the form $v_0v_1,v_1v_2,\cdots,v_{n-1}v_{n}$
  - the number of edges is the **length** of the walk
  - $v_0$ is called the initial vertex
  - $v_n$ is called the final vertex of the walk
  - the vertices except for $v_0$ and $v_n$ is called internal vertices

👉 A theorem about walk

- The entry $a_{ij}^{(k)}$ in row $i$ and column $j$ of $A^k$(邻接矩阵的$k$次幂) is the **number** of **distinct** $v_i-v_j$(始点到终点) **walks** of **length $k$**
  - Use induction(归纳法) to prove this theorem

👉 Trail(迹) Path(路) Cycle

- A walk in which all the edges are **distinct** is called a **trail**
- A trail in which all vertices $v_0,v_1,\cdots,v_n$ are **distinct**(except possibly $v_0=v_n$，即始点和终点重合) is called a **path**, denoted by $P_{n+1}$
- A path with $v_0=v_n$ is called a cycle, denoted by $C_n$
  - A cycle of length 3 is usually called a triangle
  - a loop is cycle of length 1
  - a multiple edge is a cycle of length 2

👉 A Theorem about cycle

- Let $G$ be a graph in which all vertices have degree at least two. Then $G$ contains a cycle
- Proof
  - if $G$ has a loop, it contains a cycle of length 1
  - if $G$ has multiple edges, it contains a cycle of length 2, so we can assume that $G$ is simple
  - Let $P=v_0v_1\cdots v_k$ be a longest path in $G$(常用此种证明方式)
    - Because the degree of $v_k$ is at least two, there exists a vertex $v$ different from $v_{k-1}$ **If $v$ is not on $P$**, the path $v_0v_1\cdots v_kv$ **contradicts** the choice of $P$ as a longest path. Thus, $v=v_i$, for some $0\leq i \leq k-2$ and $v_iv_{i+1}\cdots v_kv_i$ is a cycle

👉 Another definition about connectedness(连通性)

- A graph is connected if, for each pair $x,y$ of vertices, there is a **path** from $x$ to $y$
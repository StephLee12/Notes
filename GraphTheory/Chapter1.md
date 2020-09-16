- [Chapter 1](#chapter-1)
  - [Definitions and Examples](#definitions-and-examples)

# Chapter 1

## Definitions and Examples

👉 边集和点集

- set of vertices $V(G)$
- set of edges $E(G)$
  - $E$ is a **collection** of pairs(说明在$E$中允许**边重复**(即不是集合，因为集合不允许元素重复) 即可以有$v_1v_2,v_2v_1$)

👉 重边

- 两个顶点有**多条边**相连

👉 The relationship between vertex and edge

- $e$ joins vertices $u$ and $v$
  - $u$ and $v$ are **adjacent**,written $u \leftrightarrow v$
  - $e$ is **incident** with both $u$ and $v$
  - $u$ and $v$ are called the **ends** of $e$
- The **order**(阶数) of a graph is **the number of vertices**,denoted by $n$
- The **size**(大小) of a graph is **the number of edges**,denoted by **m**

👉 自环

- An edge with **identical**(同样的) ends

👉 简单图(simple graph)

- no **loops or multiple edges**

👉 度

- **degree**,denoted by $d(v)$
  - the number of edges incident with a vertex $v$,**with loops counted twice**
- maximum degree
  - $\Delta(G)=max\{d(v)\mid v \in V(G)\}$
- minimum degree
  - $\delta(G)=min\{d(v)\mid v \in V(G)\}$
- neighborhood $N(v)$
  - the set of all neighbors of $v$
- degree sequence
  - the degrees in increasing(or decreasing) order
- isolated vertices(孤立点)
  - vertices' degree are 0
- pendant vertices
  - vertices' degree are 1

👉 握手定理(The first Theorem of Graph Theory)

$$
\begin{aligned}
  \sum_{v\in V} d(v) &= 2\mid E\mid \\
\end{aligned}
$$

- 根据度的定义(the number of edges incident with vertex $v$)，一条边**贡献2度**，则对边数求和除以2即为图中每个顶点度的和(也可以理解为对每个顶点的度求和时每一条边都要**重复计算一次**)

👉 Lemma 2.10

- the number of vertices of odd degree is even(奇度点的数量是偶数)

$$
\text{Proof:Given a graph G, let }V_1 \text{ and } V_2 \text{be the set of vertices of odd and even degree in G respectively} \\
Then \quad \sum_{v\in V_1} d(v) +\sum_{v\in V_2}d(v) = \sum_{v\in V} d(v) = 2\mid E\mid \\
因为偶度点的求和一定为偶数，移项后奇度点的求和也一定为偶数\\
所以奇度点的数量是偶数
$$

👉 Subgraphs(子图)

- $H$是$G$的子图,denoted by $H \subseteq G$，if $V(H) \subseteq V(G)$ and $E(H) \subseteq E(G)$
- Spanning subgraph(支撑子图,生成子图)
  - $V(H)=V(G)$
- Induced subgraphh(导出子图)
  - $F$ is an induced subgraph of $G$ if whenever $u$ and $v$ are vertices of $F$ and $uv$ is an edge of $G$(so $uv$ is actually an edge of $F$ as well)
  - denoted by $G[S]$

👉 同构(Isomorphism)

- $G_1$ and $G_2$ are isomorphic if there exists a **one-to-one correspondence**(双射，即可以逆映射) $\phi$ from $V(G_1)$ to $V(G_2)$ such that $u_1v_1\in E(G_1)$ if and only if $\phi(u_1)\phi(v_1)\in E(G_2)$,denoted by $G_1\cong G_2$

👉 Connectedness(连通性)

- if $V_1 \cap V_2 = \emptyset$, **disjoint union**(不交并) $G_1 \cup G_2$(**precisely** $G_1+G_2$) is a graph with $V=V_1\cup V_2$ and $E = E_1 \cup E_2$
- 判断一个图是否是连通的
  - it cannot b expressed as **the disjoint union of two graphs**
- 连通分支
  - 任何一个不连通的图$G$都可以表示为多个连通图的**并集**,这些连通图称为$G$的**连通分支**(component)
  - 连通分支的数量 denoted by $\omega(G)$

👉 对图的运算

- delete vertex $v$,the edge incident with $v$ will also be removed
- delete edge $e$,the ends of $e$ will not be removed
- Contraction(收缩)
  - remove edge $e$ and **identify** its ends $v$ and $w$(将$v$和$w$重合,认为是同一个顶点), so that the **resulting vertex**(重合后的顶点) is **incident with deges which were originally incident with** $v$ or $w$
  - note ！！！！需要在这里加一个示意图

👉 邻接矩阵$A$和关联矩阵$B$

- Adjacency matrix $A=[a_{ij}]_{n\times n}$

$$
a_{ij=}\begin{cases}
  1,\quad v_iv_j \in E(G)\\
  0,\quad otherwise
\end{cases}
$$

- Incidence matrix $B=[b_{ij}]_{n\times m}$

$$
b_{ij} = \begin{cases}
  1,\quad \text{if }v_i \text{ is incident with } e_j \\
  0,\quad otherwise
\end{cases}
$$

- 通过关联矩阵能用代数方法证明握手定理

👉 拉普拉斯矩阵(Laplacian Matrix)$L$

$$
L=D-A
$$

- $D$ is the degree matrix(a **diagonal matrix** with **diagonal elements being degree** of its corresponding vertex)

👉 空图(null graph) denoted by $\emptyset$ 零图(empty graph) denoted by $E_n$

- 空图
  - 点集和边集都为空的图
- 零图
  - 边集为空的图

👉 完全图(complete graph) $K_n$

- a **simple graph**(没有重边和自环) in which **each pair of distinct** vertices are **adjacent**
- $n$为顶点集的大小，称为完全图的阶数
- note！！需要加一个ppt上的图

👉 正则图(regular graph)

- if $\delta(G)=\Delta(G)$, then all vertices have the **same degree**, so the graph is called **regular**
- $G$ is **r-regular**(r正则的) if $d(v)=r$ for every $v$ where $0\leq r \leq n-1$

👉 Peterson Graph

- the **simple graph** whose vertices are the **2-element subsets of a 5-element set**(是一个五个元素集合的含有两个元素的子集) and whose edges are the **pairs of disjoint 2-element subsets**(只有两个含有两个元素的子集**不交并**才将两个顶点相连)
- note!!!需要加一个图

👉 Platonic graphs(柏拉图图)

- 都是正则图
- 正四面体(tectrahedron)
- 立方体(cube)
- 正八面体(octahedron)
- 正十二面体(icosahedron)
- 正二十面体(dodecahedron)

👉 二部图(Bipartite graphs)

- if the vertexset can be split into two **disjoint sets** $A$ and $B$ so that each edge **joins** a vertex of $A$ and a vertex of $B$
- Complete bipartite graph(完全二部图)
  - each vertex in $A$ is joined to each vertex in $B$ by **just one edge**
- denoted by $K_{r,s}$ where $r$ is the number of one party's vertices and $s$ is the number of the other

👉 Cartesian product(卡氏乘积)

- written $G\Box H$
- is the **graph** with vertex set $V(G)\times V(H)$(笛卡尔乘积,$G$中的顶点用$u$表示,$H$中的顶点用$v$表示) specified by putting $(u,v)$ adjacent to $(u^{'},v^{'})$ if and only if $u=u^{'}\text{ and }vv^{'} \in E(H)$ or $v=v^{'}\text{ and }uu^{'} \in E(G)$

👉 超立方/k-立方(hypercube/k-cube)

- denoted by $Q_k$
- vertices correspond to the sequences $(a_1,a_2,\cdots,a_k)$ where each $a_i=0 \text{ or } 1$ and whose edges **join** those sequences that **differ in just one coordinate**
- 利用卡氏乘积和完全图计算超立方

$$
Q_1=K_2\\
Q_k = K_2 \Box Q_{k-1}
$$

- 两个超立方的卡氏乘积依然为一个超立方

$$
Q_i \Box Q_j = Q_{i+j}
$$
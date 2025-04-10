## Ejercicio 5

![image](https://github.com/user-attachments/assets/795cc9ea-b1b2-4440-9dc1-aa766881d152)

### Algoritmo de Dijkstra

En Soltys 58-pdf

Suppose that we are given a graph G = (V, E), a designated start node s,
and a cost function for each edge e ∈ E, denoted c(e). We are asked to
compute the cheapest paths from s to every other node in G, where the
cost of a path is the sum of the costs of its edges.
Consider the following greedy algorithm: the algorithm maintains a set
S of explored nodes, and for each u ∈ S it stores a value d(u), which is the
cheapest path inside S, starting at s and ending at u.
Initially, S = {s} and d(s) = 0. Now, for each v ∈ V − S we find the
shortest path to v by traveling inside the explored part S to some u ∈ S,
followed by a single edge (u, v). 

That is, we compute:
d
0
(v) = min
u∈S,e=(u,v)
d(u) + c(e).

We choose the node v ∈ V − S for which (2.3) is minimized, add v to S,
and set d(v) = d
0
(v), and repeat. Thus we add one node at a time to the
explored part, and we stop when S = V .

Cormen 642-pdf


### Algoritmo de Bellman-Ford

En Soltys 88-pdf

Suppose that we want to find the shortest path from s to t, in a directed
graph G = (V,E), where edges have non-negative costs. Let Opt(i, v)
denote the minimal cost of an i-path from v to t, where an i-path is a path
that uses at most i edges. Let p be an optimal i-path with cost Opt(i, v);
if no such p exists we adopt the convention that Opt(i, v) = ∞.
If p uses i−1 edges, then Opt(i, v) = Opt(i−1, v), and if p uses i edges,
and the first edge is (v, w) ∈ E, then Opt(i, v) = c(v, w) + Opt(i − 1, w),
where c(v, w) is the cost of edge (v, w). This gives us the recursive formula,
for i > 0: Opt(i, v) = min{Opt(i−1, v), minw∈V {c(v, w)+Opt(i−1, w)}}.

Cormen 634-pdf

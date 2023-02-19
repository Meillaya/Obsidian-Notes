An optimal algorithm is to schedule the jobs in decreasing order of $w_{i} / t_{i}$. We prove the optimality of this algorithm by an exchange argument.

Thus, consider any other schedule. As is standard in exchange arguments, we observe that this schedule must contain an inversion - a pair of jobs $i, j$ for which $i$ comes before $j$ in the alternate solution, and $j$ comes before $i$ in the greedy solution. Further, in fact, there must be an adjacent such pair $i, j$. Note that for this pair, we have $w_{j} / t_{j} \geq w_{i} / t_{i}$, by the definition of the greedy schedule. If we can show that swapping this pair $i, j$ does not increase the weighted sum of completion times, then we can iteratively do this until there are no more inversions, arriving at the greedy schedule without having increased the function we're trying to minimize. It will then follow that the greedy algorithm is optimal.

So consider the effect of swapping $i$ and $j$. The completion times of all other jobs remain the same. Suppose the completion time of the job before $i$ and $j$ is $C$. Then before the swap, the contribution of $i$ and $j$ to the total sum was $w_{i}\left(C+t_{i}\right)+w_{j}\left(C+t_{i}+t_{j}\right)$, while after the sum it is $w_{j}\left(C+t_{j}\right)+w_{i}\left(C+t_{i}+t_{j}\right)$. The difference between the value after the swap, compared to the value before the swap is (canceling terms in common between the two expressions) $w_{i} t_{j}-w_{j} t_{i}$. Since $w_{j} / t_{j} \geq w_{i} / t_{i}$, this difference is bounded above by 0 , and so the total weighted sum of completion times does not increase due to the swap, as desired.

${ }^{1} \operatorname{ex} 948.540 .252$ Let $c_{e}$ denote the cost of the edge $e$ and we will overload the notation and write $c_{s t}$ to denote the cost of the edge between the nodes $s$ and $t$.

This problem is by its nature quite similar to the shortest path problem. Let us consider a two-parameter function $\operatorname{Opt}(i, s)$ denoting the optimal cost of shortest path to $s$ using exactly $i$ edges, and let $N(i, s)$ denote the number of such paths.

We start by setting $\operatorname{Opt}(i, v)=0$ and $\operatorname{Opt}\left(i, v^{\prime}\right)=\infty$ for all $v^{\prime} \neq v$. Also set $N(i, v)=1$ and $N\left(i, v^{\prime}\right)=0$ for all $v^{\prime} \neq v$. Intuitively this means that the source $v$ is reachable with cost 0 and there is currently one path to achieve this.

Then we compute the following recurrence:

$$
O p t(i, s)=\min _{t,(t, s) \in E}\left\{O p t(i-1, t)+c_{t s}\right\}
$$

The above recurrence means that in order to travel to node $s$ using exactly $i$ edges, we must travel a predecessor node $t$ using cxactly $i-1$ cdges and then take the cdge connecting $t$ to s. Once of course the optimal cost value has been computed, the number of paths that achieve this optimum would be computed by the following recurrence:

$$
N(i, s)=\sum_{t,(t, s) \in E \text { and }} \sum_{O p t(i, s)=O p t(i-1, t)+c_{t s}} N(i-1, t) .
$$

In other words, we look at all the predecessors from which the optimal cost path may be achieved and add all the counters.

The above recurrences can be calculated by a double loop, where the outside loops over $i$ and the inside loops over all the possible nodes $s$. Once the recurrences have been solved, our target optimal path to $w$ is obtained by taking the minimum of all the paths of different lengths to $w$ - that is:

$$
O p t(w)=\min _{i}\{O p t(i, w)\} .
$$

And the number of such paths can be computed by adding up the counters of all the paths which achieve the minimal cost.

$$
N(w)=\sum_{i, O p t(i, w)=O p t(w)} N(i, w)
$$

${ }^{1} \operatorname{ex} 720.859 .203$ The basic idea is to ask: How should we gerrymander precincts 1 through $\mathrm{j}$, for each $\mathrm{j}$ ? To make this work, though, we have to keep track of a few extra things, by adding some variables. For brevity, we say that the $A$-votes in a precinct are the votes for party $A$, and $B$-votes are the votes for party $B$. We keep track of the following information about a partial solution.

- How many precincts have becn assigned to district 1 so far?

- How many A-votes are in district 1 so far?

- how many A-votes are in district 2 so far?

So let $M[j, p, x, y]=t r u e$ if it is possible to achieve at least $x$ A-votes in district 1 and $y$ Avotes in district 2 , while allocating $p$ of the first $\mathrm{j}$ precincts to district $1 .(M[j, p, x, y]-f a l s e$ otherwise.) Now suppose precinct $j+1$ has $z$ A-votes. To compute $M[j+1, p, x, y]$, you either put precinct $j+1$ in district 1 (in which case you check the results of sub-problem $M[j, p-1, x-z, y]$ ) or in precinct 2 (in which case you check the results of sub-problem $M[j, p, x, y-z])$. Now to decide if there's a solution to the whole problem, you scan the entire table at the end, looking for a value of "true" in any entry of the form $M[n, n / 2, x, y]$, where each of $\mathrm{x}$ and $\mathrm{y}$ is greater than $\mathrm{mn} / 4$. (Since each district gets $\mathrm{mn} / 2$ votes total.)

We can build this up in order of increasing $j$, and each sub-problem takes constant time to compute, using the values of smaller sub-problems. Since there are $n^{2} m^{2}$ sub-problems, the running time is $O\left(n^{2} m^{2}\right)$.

${ }^{1} \operatorname{ex} 706.269 .18$ The subproblems will represent the optimum way to satisfy orders $1, \ldots, i$ with an inventory of $s$ trucks left over after the month $i$. Let $O P T(i, s)$ denote the value of the optimal solution for this subproblem.

- The problem we want to solve is $O P T(n, 0)$ as we do not need any leftover inventory at the end.

- The number of subproblems is $n(S+1)$ as there could be $0,1, \ldots, S$ trucks left over after a period.

- To get the solution for a subproblem $O P T(i, s)$ given the values of the previous subproblems, we have to try every possible number of trucks that could have been left over after the previous period. If the previous period had $z$ trucks left over, then so far we paid $O P T(i-1, z)$ and now we have to pay $z C$ for storage. In order to satisfy the demand of $d_{i}$ and have $s$ trucks left over, we need $s+d_{i}$ trucks. If $z<s+d_{i}$ we have to order more, and pay the ordering fee of $K$.

In summary the cost $O P T(i, s)$ is obtained by taking the smaller of $O P T\left(i-1, s+d_{i}\right)+$ $C\left(s+d_{i}\right)$ (if $\left.s+d_{i} \leq S\right)$, and the minimum over smaller values of $z, \min _{z<\min \left(s+d_{i}, S\right)}(O P T(i-$ $1, z)+z(K+K)$

We can also observe that the minimum in this second term is obtained when $z=0$ (if we have to reorder anyhow, why pay storage for any extra trucks?). With this extra observation we get that

$-$ if $s+d_{i}>S$ then $O P T(i, s)=O P T(i-1,0)+K$,

$-$ else $O P T(i, s)=\min \left(O P T\left(i-1, s+d_{i}\right)+C\left(s+d_{i}\right), O P T(i-1,0)+K\right)$.

$1 \operatorname{ex} 304.359 .690$ (a) Let $J$ be the optimal subset. By definition all jobs in $J$ can be scheduled to meet their deadline. Now consider the problem of scheduling to minimize the maximum lateness from class, but consider the jobs in $J$ only. We know by the definition of $J$ that the minimum lateness is 0 (i.e., all jobs can be scheduled in time), and in class we showed that the greedy algorithm of scheduling jobs in the order of their deadline, is optimal for minimizing maximum lateness. Hence ordering the jobs in $J$ by the deadline generates a feasible schedule for this set of jobs.

(b) The problem is analogous to the Subset Sum Problem. We will have subproblems analogous to the subproblems for that problem. The first idea is to consider subproblems using a subset of jobs $\{1, \ldots, m\}$. As always we will order the jobs by increasing deadline, and we will assume that they are numbered this way, i.e., we have that $d_{1} \leq \ldots \leq d_{n}=D$. To solve the original problem we consider two cases: either the last job $n$ is accepted or it is rejected. If job $n$ is rejected, then the problem reduces to the subproblem using only the first $n-1$ items. Now consider the case when job $n$ is accepted. By part (a) we know that we may assume that job $n$ will be scheduled last. In order to make sure that the machine can finish job $n$ by its deadline $D$, all other jobs accepted by the schedule should be done by time $D-t_{n}$. We will define subproblems so that this problem is one of our subproblems.

For a time $0 \leq d \leq D$ and $m=0, \ldots, n$ let $O P T(d, m)$ denote the maximum subset of requests in the set $\{1, \ldots, m\}$ that can be satisfied by the deadline $d$. What we mean is that in this subproblem the machine is no longer available after time $d$, so all requests either have to be scheduled to be done by deadline $d$, or should be rejected (even if the deadline $d_{i}$ of the job is $d_{i}>d$ ). Now we have the following statement.

- If job $m$ is not in the optimal solution $O P T(d, m)$ then $O P T(m, d)=O P T(m-1, d)$.

- If job $m$ is in the optimal solution $O P^{\prime} I^{\prime}(m, d)$ then $O Y^{\prime} I^{\prime}(m, d)=O P^{\prime} l^{\prime}(m-1, d-$ $\left.t_{m}\right)+1$.

This suggests the following way to build up values for the subproblems.

![](https://cdn.mathpix.com/cropped/2023_01_22_2b3fc3fbddfb85fd422fg-05.jpg?height=518&width=983&top_left_y=1827&top_left_x=342)

${ }^{1} \operatorname{ex} 601.300 .669$ 

![](https://cdn.mathpix.com/cropped/2023_01_22_2b3fc3fbddfb85fd422fg-06.jpg?height=467&width=755&top_left_y=244&top_left_x=403)

The correctness follows immediately from the statement (1). The running time of $O\left(n^{2} D\right)$ is also immediate from the for loops in the problem, there are two nested for loops for $m$ and one for $d$. This means that the internal part of the loop gets invoked $O(n D)$ time. The internal part of this for loop takes $O(n)$ time, as we explicitly maintain the optimal solutions. The running time can be improved to $O(n D)$ by not maintaining the $S$ array, and only recovering the solution later, once the values are known. We build the following flow network. There is a node $v_{i}$ for each client $i$, a node $w_{j}$ for each base station $j$, and an edge $\left(v_{i}, w_{j}\right)$ of capacity 1 if client $i$ is within range of base station $j$. We then connect a super-source $s$ to each of the client nodes by an edge of capacity 1 , and we connect each of the base station nodes to a super-sink $t$ by an edge of capacity $L$.

We claim that there is a feasible way to connect all clients to base stations if and only if there is an $s$ - $t$ flow of value $n$. If there is a feasible connection, then we send one unit of flow from $s$ to $t$ along each of the paths $s, v_{i}, w_{j}, t$, where client $i$ is connected to base station j. This does not violate the capacity conditions, in particular on the edges $\left(w_{j}, t\right)$, due to the load constraints. Conversely, if there is a flow of value $n$, then there is one with integer values. We connect client $i$ to base station $j$ if the edge $\left(v_{i}, w_{j}\right)$ carries one unit of flow, and we observe that the capacity condition ensures that no base station is overloaded.

The running is the time required to solve a max-flow problem on a graph with $O(n+k)$ nodes and $O(n k)$ edges.

$1 \operatorname{ex} 751.45 .676$ We will assume that the flow $f$ is integer-valued. Let $e^{*}=(v, w)$. If the edge $e^{*}$ is not saturated with flow, then reducing its capacity by one unit does not cause a problem. So assume it is saturated.

We first reduce the flow on $e^{*}$ to satisfy the capacity conditions. We now have to restore the capacity conditions. We construct a path from $w$ to $t$ such that all edges carry flow, and we reduce the flow by one unit on each of these edges. We then do the same thing from $v$ back to s. Note that because the flow $f$ is acyclic, we do not encounter any edge twice in this process, so all edges we traverse have their flow reduced by exactly one unit, and the capacity condition is restored.

Let $f^{\prime}$ be the current flow. We have to decide whether $f^{\prime}$ is a maximum flow, or whether the flow value can be increased. Since $f$ was a maximum flow, and the value of $f^{\prime}$ is only one unit less than $f$, we attempt to find a single augmenting path from $s$ to $t$ in the residual graph $G_{f^{\prime}}$. If we fail to find one, then $f^{\prime}$ is maximum. Else, the flow is augmented to have a value at least that of $f$; since the current flow network cannot have a larger maximum flow value than the original one, this is a maximum flow.

${ }^{1} \operatorname{ex} 257.178 .863$ If the minimum $s$ - $t$ cut has size $\leq k$, then we can reduce the flow to 0 . Otherwise, let $f>k$ be the value of the maximum s-t flow. We identify a minimum $s$ - $t$ cut $(A, B)$, and delete $k$ of the edges out of $A$. The resulting subgraph has a maximum flow value of at most $f-k$.

But we claim that for any set of edges $F$ of size $k$, the subgraph $G^{\prime}=(V, F-F)$ has an $s$ - $t$ flow of value at least $f-k$. Indeed, consider any cut $(A, B)$ of $G^{\prime}$. There are at least $f$ edges out of $A$ in $G$, and at most $k$ have been deleted, so there are at least $f-k$ edges out of $A$ in $G^{\prime}$. Thus, the minimum cut in $G^{\prime}$ has value at least $f-k$, and so there is a flow of at least this value.

${ }^{1} \operatorname{ex} 225.750 .725$ (a) Let $G=(V, E)$ be a bipartite graph with a node $p_{i} \in V$ representing each person and a node $d_{j} \in V$ representing each night. The edges consist of all pairs $\left(p_{i}, d_{j}\right)$ for which $d_{j} \notin S_{i}$.

Now, a perfect matching in $G$ is a pairing of people and nights so that each person is paired with exactly one night, no two people are paired with the same night, and each person is available on the night they are paired with. Thus, if $G$ has a perfect matching, then it has a feasible dinner schedule. Conversely, if $G$ has a feasible dinner schedule, consisting of a set of pairs $S=\left\{\left(p_{i}, d_{j}\right)\right\}$, then each $\left(p_{i}, d_{j}\right) \in S$ is an edge of $G$, no two of these pairs share an endpoint in $G$, and hence these edges define a perfect matching in $G$.

(b) An algorithm is as follows. First, construct the bipartite graph $G$ from part (a): it takes $O(1)$ time to decide for each pair $\left(p_{i}, d_{j}\right)$ whether it should be an edge in $G$, so the total time to construct $G$ is $O\left(n^{2}\right)$. Now, let $Q$ denote the set of edges constructed by Alanis. Delete the edge $\left(p_{j}, d_{k}\right)$ from $Q$, obtaining a set of edges $Q^{\prime} . Q^{\prime}$ has size $n-1$, and since no person or night appears more than once in $Q^{\prime}$, it is a matching.

We now try to find an augmenting path in $G$ with respect to $Q^{\prime}$, in time $O(|E|)=O\left(n^{2}\right)$. If we find such an augmenting path $P$, then increasing $Q^{\prime}$ using $P$ gives us a matching of size $n$, which is a perfect matching and hence by (a) corresponds to a feasible dinner schedule. If $G$ has no augmenting path with respect to $Q^{\prime}$, then by a theorem from class, $Q^{\prime}$ must be a maximum matching in $G$. In particular, this means that $G$ has no perfect matching, and hence by (a) there is no feasible dinner schedule.

${ }^{1} \operatorname{ex} 245.875 .267$ (a) Define a flow network as follows. There is a source $s$, a node $x_{i}$ representing each balloon $i$, a node $z_{i}$ representing each condition $c_{i}$, and a sink $t$. There are edges $\left(s, x_{i}\right)$ of capacity $2,\left(x_{i}, z_{j}\right)$ of capacity 1 whenever $c_{j} \in S_{i}$, and edges $\left(z_{j}, t\right)$ of capacity $k$. We then test whether the maximum $s-t$ flow has value $n k$.

The Ford-Fulkerson algorithm to find a maximum flow has running time $O(|F| C)$, where $|E|$ is the number of edges and $C$ is the total capacity of edges out of $s$. Here we have $|E|=O(m n)$ and $C=2 m$, so the running time is $O\left(m^{2} n\right)$.

An alternate but related solution would place a lower bound of $k$ on each edge of the form $\left(z_{j}, t\right)$. One would then place a demand of $-n k$ on $s$ and $n k$ on $t$, and test whether there is a feasible circulation.

(b) Break all edges $\left(x_{i}, z_{j}\right)$. Insert new nodes $y_{p j}$ for each sub-contractor $p$ and condition $c_{j}$. Add an edge $\left(x_{i}, y_{p j}\right)$ of capacity 1 when $c_{j} \in S_{i}$ and balloon $i$ is produced by subcontractor $p$. Add an edge $\left(y_{p j}, c_{j}\right)$ of capacity $k-1$. Again, test whether the maximum $s$ - $t$ flow has value $n k$.

As in part (a), the running time is $O(|E| C)$. Here $|E|$ is still $O(m n)$, and $C=2 m$, so the running time is $O\left(m^{2} n\right)$.

The alternate solution in (a) based on circulations with lower bounds can be modified in the same way.

$1^{1} \operatorname{ex} 557.796 .690$
Question 3 
Say $n$ boxes arrive in the order $b_{1}, \ldots, b_{n}$. Say each box $b_{i}$ has a positive weight $w_{i}$, and the maximum weight each truck can carry is $W$. To pack the boxes into $N$ trucks preserving the order is to assign each box to one of the trucks $1, \ldots, N$ so that:

- No truck is overloaded: the total weight of all boxes in each truck is less or equal to $W$.

- The order of arrivals is preserved: if the box $b_{i}$ is sent before the box $b_{j}$ (i.e. box $b_{i}$ is assigned to truck $x$, box $b_{j}$ is assigned to truck $y$, and $x<y$ ) then it must be the case that $b_{i}$ has arrived to the company earlier than $b_{j}$ (i.e. $i<j$ ).

We prove that the greedy algorithm uses the fewest possible trucks by showing that it "stays ahead" of any other solution. Specifically, we consider any other solution and show the following. If the greedy algorithm fits boxes $b_{1}, b_{2}, \ldots, b_{j}$ into the first $k$ trucks, and the other solution fits $b_{1}, \ldots, b_{i}$ into the first $k$ trucks, then $i \leq j$. Note that this implies the optimality of the greedy algorithm, by setiing $k$ to be the number of trucks used by the greedy algorithm.

We will prove this claim by induction on $k$. The case $k=1$ is clear; the greedy algorithm fits as many boxes as possible into the first truck. Now, assuming it holds for $k-1$ : the greedy algorithm fits $j^{\prime}$ boxes into the first $k-1$, and the other solution fits $i^{\prime} \leq j^{\prime}$. Now, for the $k^{\text {th }}$ truck, the alternate solution packs in $b_{i^{\prime}+1}, \ldots, b_{i}$. Thus, since $j^{\prime} \geq i^{\prime}$, the greedy algorithm is able at least to lit all the boxes $b_{j^{\prime}+1}, \ldots, b_{i}$ into the $k^{\text {th }}$ truck, and it can potentially fit more. This completes the induction step, the proof of the claim, and hence the proof of optimality of the greedy algorithm.



Question 5
Here is a greedy algorithm for this problem. Start at the western end of the road and begin moving east until the first moment when there's a house $h$ exactly four miles to the west. We place a base station at this point (if we went any farther east without placing a base station, we wouldn't cover $h$ ). We then delete all the houses covered by this base station, and iterate this process on the remaining houses.

Here's another way to view this algorithm. For any point on the road, define its position to be the number of miles it is from the western end. We place the first base station at the easternmost (i.e. largest) position $s_{1}$ with the property that all houses between 0 and $s_{1}$ will be covered by $s_{1}$. In general, having placed $\left\{s_{1}, \ldots, s_{i}\right\}$, we place base station $i+1$ at the largest position $s_{i+1}$ with the property that all houses between $s_{i}$ and $s_{i+1}$ will be covered by $s_{i}$ and $s_{i 11}$.

Let $S=\left\{s_{1}, \ldots, s_{k}\right\}$ denote the full set of base station positions that our greedy algorithm places, and let $T=\left\{t_{1}, \ldots, t_{m}\right\}$ denote the set of base station positions in an optimal solution, sorted in increasing order (i.e. from west to east). We must show that $k=m$.

We do this by showing a sense in which our greedy solution $S$ "stays ahead" of the optimal solution $T$. Specifically, we claim that $s_{i} \geq t_{i}$ for each $i$, and prove this by induction. The claim is true for $i=1$, since we go as far as possible to the east before placing the first base station. Assume now it is true for some value $i \geq 1$; this means that our algorithm's first $i$ centers $\left\{s_{1}, \ldots, s_{i}\right\}$ cover all the houses covered by the first $i$ centers $\left\{t_{1}, \ldots, t_{i}\right\}$. As a result, if we add $t_{i+1}$ to $\left\{s_{1}, \ldots, s_{i}\right\}$, we will not leave any house between $s_{i}$ and $t_{i+1}$ uncovered. But the $(i+1)^{\text {st }}$ step of the greedy algorithm chooses $s_{i+1}$ to be as large as possible subject to the condition of covering all houses between $s_{i}$ and $s_{i+1}$; so we have $s_{i+1} \geq t_{i+1}$. 'I'his proves the claim by induction.

Finally, if $k>m$, then $\left\{s_{1}, \ldots, s_{m}\right\}$ fails to cover all houses. But $s_{m} \geq t_{m}$, and so $\left\{t_{1}, \ldots, t_{m}\right\}=' T$ ' also fails to cover all houses, a contradiction.



Question 6
Let the contestants be numbered $1, \ldots, n$, and let $s_{i}, b_{i}, r_{i}$ denote the swimming, biking, and running times of contestant i. Here is an algorithm to produce a schedule: arrange the contestants in order of decreasing $b_{i}+r_{i}$, and send them out in this order. We claim that this order minimizes the completion time.

We prove this by an exchange argument. Consider any optimal solution, and suppose it does not use this order. Then the optimal solution must contain two contestants $i$ and $j$ so that $j$ is sent out directly after $i$, but $b_{i}+r_{i}<b_{j}+r_{j}$. We will call such a pair $(i, j)$ an inversion. Consider the solution obtained by swapping the orders of $i$ and $j$. In this swapped schedule, $j$ completes earlier than he/she used to. Also, in the swapped schedule, $i$ gets out of the pool when $j$ previously got out of the pool; but since $b_{i}+r_{i}<b_{j}+r_{j}, i$ finishes sooner in the swapped schedule than $j$ finished in the previous schedule. Hence our swapped schedule does not have a greater completion time, and so it too is optimal.

Continuing in this way, we can eliminate all inversions without increasing the completion time. At the end of this process, we will have a schedule in the order produced by our algorithm, whose completion time is no greater than that of the original optimal order we considered. Thus the order produced by our algorithm must also be optimal.


Question 16
In this problem, you basically have a set of $n$ points (the account events) and a set of intervals (the "error bars" around the suspicious transactions, i.e. $\left[t_{i}-e_{i}, t_{i}+e_{i}\right]$ ), and you want to know if there is a perfect matching between points and intervals so that each point lies in its corresponding interval). Without loss of generality, let us assume $x_{1} \leq x_{2} \leq \ldots \leq x_{n}$.

A greedy style algorithm goes like this:

![](https://cdn.mathpix.com/cropped/2023_01_22_f0000382638124fc474cg-04.jpg?height=262&width=1030&top_left_y=543&top_left_x=346)

It is obvious that if the algorithm succceds, it rcally finds a perfect matching. We want to prove that if there is a perfect matching, the algorithm will find it. We prove this by an exchange argument, which we will express in the form of a proof by contradiction.

Supposc by way of contradiction that there is a pcrfcct matching, but that the above greedy algorithm does not construct one. Choose a perfect matching $M$, in which the first $i$ points $x_{1}, x_{2}, \ldots, x_{i}$ match to intervals in the same way described in the algorithm, and $i$ is the largest number with this property. Now suppose $x_{i+1}$ matches to an interval centered at $t_{l}$ in $M$, but the algorithm matches $x_{i+1}$ to another interval centered at $t_{j}$. According to the algorithm, we know that $t_{j}+e_{j} \leq t_{l}+e_{l}$. Suppose $t_{j}$ is matched to $x_{k}\left(x_{k} \geq x_{i+1}\right)$ in $M$. Then we have

$$
t_{l}-e_{l} \leq x_{i+1} \leq x_{k} \leq t_{j}+e_{j} \leq t_{l}+e_{l}
$$

so in $M$ we can instead match $x_{k}$ to $t_{l}$ and match $x_{i+1}$ to $t_{j}$ to have a new perfect matching $M^{\prime}$, which agrees with the algorithm. $M^{\prime}$ agrees with the output of the greedy algorithm on the first $i$ | 1 points, contradicting our choice of $i$.

To bound the running time, note that if we simply enumerate all unmatched intervals in each iteration of the for loop, it will take $O(n)$ time to find the unmatched one that ends carlicst. There are $n$ itcrations, so the algorithm takes $O\left(n^{2}\right)$ time.

Question 24
 To design an optimal solution, we apply a general technique that is known as Deferred Merge Embedding (DME) by researchers in the VLSI community. It's a greedy algorithm that works as follows. Let $v$ denote the root, with $v^{\prime}$ and $v^{\prime \prime}$ its two children. Let $d^{\prime}$ denote the maximum root-to-leaf distance over all leaves that are descendants of $v^{\prime}$, and let $d^{\prime \prime}$ denote the maximum root-to-leaf distance over all leaves that are descendants of $v^{\prime \prime}$. Now:

- If $d^{\prime}>d^{\prime \prime}$, we add $d^{\prime}-d^{\prime \prime}$ to the length of the $v$-to-v" edge and add nothing to the length of the $v$-to- $v^{\prime}$ edge.

- If $d^{\prime \prime}>d^{\prime}$, we add $d^{\prime \prime}-d^{\prime}$ to the length of the $v$-to- $v^{\prime}$ edge and add nothing to the length of the $v$-to-v" edge.

- $d^{\prime}=d^{\prime \prime}$ we add nothing to the length of either edge below $v$.

We now apply this procedure recursively to the subtrees rooted at each of $v^{\prime}$ and $v^{\prime \prime}$.

Let $T$ be the complete binary tree in the problem. We first develop two basic facts about the optimal solution, and then use these in an "exchange" argument to prove that the DME" algorithm is optimal.

(i) Let $w$ be an internal node in $T$, and let $e^{\prime}, e^{\prime \prime}$ be the two edges directly below $w$. If a solution adds non-zero length to both $e^{\prime}$ and $e^{\prime \prime}$, then it is not optimal.

Proof. Suppose that $\delta^{\prime}>0$ and $\delta^{\prime \prime}>0$ are added to $\ell_{e^{\prime}}$ and $\ell_{e^{\prime \prime}}$ respectively. Let $\delta=$ $\min \left(\delta^{\prime}, \delta^{\prime \prime}\right)$. Then the solution which adds $\delta^{\prime}-\delta$ and $\delta^{\prime \prime}-\delta$ to the lengths of these edges must also have zero skew, and uses less total length.

(ii) Let $w$ be a node in ' $T$ ' that is neither the root nor a leaf. If a solution increases the length of every path from $w$ to a leaf below $w$, then the solution is not optimal.

Proof. Suppose that $x_{1}, \ldots, x_{k}$ are the leaves below $w$. Consider edges $e$ in the subtree below $w$ with the following property: the solution increases the length of $e$, and it does not increase the length of any edge on the path from $w$ to e. Let $F$ be the set of all such edges; we observe two facts about $F$. First, for each leaf $x_{i}$, the first edge on the $w-x_{i}$ path whose length has been increased must belong to $F$, (and no other edge on this path can belong to $F$ ); thus there is exactly one edge from $F$ on every $w-x_{i}$ path. Second, $|F| \geq 2$, since a path in the left subtree below $w$ shares no edges with a path in the right subtree below $w$, and yet each contains an edge of $F$.

Let $e_{w}$ be the edge entering $w$ from its parent (recall that $w$ is not the root). Teet $\delta$ be the minimum amount of length added to any of the edges in $F$. If we subtract $\delta$ from the length added to each edge in $F$, and add $\delta$ to the edge above $w$, the length of all root-to-leaf paths remains the same, and so the tree remains zero-skew. But we have subtracted $|F| \delta \geq 2 \delta$ from the total length of the tree, and added only $\delta$, so we get a zero skew tree with less total length.

We can now prove a somewhat stronger fact than what is asked for.

(iii) The DME algorithm produces the unique optimal solution.

Proof. Consider any other solution, and let $v$ be any node of $T$ at which the solution does not add lengths in the way that DME would. We use the notation from the problem, and assume without loss of generality that $d^{\prime} \geq d^{\prime \prime}$. Suppose the solution adds $\delta^{\prime}$ to the edge $\left(v, v^{\prime}\right)$ and $\delta^{\prime \prime}$ to the edge $\left(v, v^{\prime \prime}\right)$.

If $\delta^{\prime \prime} \delta^{\prime}=d^{\prime} \quad d^{\prime \prime}$, then it must be that $\delta^{\prime}>0$ or clse the solution would do the same thing as DME; in this case, by (i) it is not optimal. If $\delta^{\prime \prime}-\delta^{\prime}<d^{\prime}-d^{\prime \prime}$, then the solution will still have to increase the length of the path from $v^{\prime \prime}$ to each of its leaves in order to make the trec zcro-skew; so by (ii) it is not optimal. Similarly, if $\delta^{\prime \prime} \delta^{\prime}>d^{\prime} d^{\prime \prime}$, then the solution will still have to increase the length of the path from $v^{\prime}$ to each of its leaves in order to make the tree zero-skew; so by (ii) it is not optimal. 



Question 3
(a) The graph on nodes $v_{1}, \ldots, v_{5}$ with edges $\left(v_{1}, v_{2}\right),\left(v_{1}, v_{3}\right),\left(v_{2}, v_{5}\right),\left(v_{3}, v_{4}\right)$ and $\left(v_{4}, v_{5}\right)$ is such an example. The algorithm will return 2 corresponding to the path of edges $\left(v_{1}, v_{2}\right)$ and $\left(v_{2}, v_{5}\right)$, while the optimum is 3 using the path $\left(v_{1}, v_{3}\right),\left(v_{3}, v_{4}\right)$ and $\left(v_{4}, v_{5}\right)$.

(b) The idea is to use dynamic programming. The simplest version to think of uses the subproblems $O P T[i]$ for the length of the longest path from $v_{1}$ to $v_{i}$. One point to be careful of is that not all nodes $v_{i}$ necessarily have a path from $v_{1}$ to $v_{i}$. We will use the value " $-\infty "$ for the $O P T[i]$ value in this case. We use $O P T(1)=0$ as the longest path from $v_{1}$ to $v_{1}$ has 0 edges.

![](https://cdn.mathpix.com/cropped/2023_01_22_f0000382638124fc474cg-07.jpg?height=711&width=722&top_left_y=698&top_left_x=340)

The running time is $O\left(n^{2}\right)$ if you assume that all edges entering a node $i$ can be listed in $O(n)$ time.

Question 5
The key observation to make in this problem is that if the segmentation $y_{1} y_{2} \ldots y_{n}$ is an optimal one for the string $y$, then the segmentation $y_{1} y_{2} \ldots y_{n-1}$ would be an optimal segmentation for the prefix of $y$ that excludes $y_{n}$ (because otherwise we could substitute the optimal solution for the prefix in the original problem and get a better solution).

Given this observation, we design the subproblems as follows. Let Opt(i) be the score of the best segmentation of the prefix consisting of the first $i$ characters of $y$. We claim that the recurrence

$$
O p t(i)=\min _{j \leq i}\{O p t(j-1)+\text { Quality }(j \ldots n)\}
$$

would give us the correct optimal segmentation (where Quality $(\alpha \ldots \beta)$ means the quality of the word that is formed by the characters starting from position $\alpha$ and cnding in position $\beta)$. Notice that the desired solution is $\operatorname{Opt}(n)$.

We prove the correctness of the above formula by induction on the index $i$. The base case is trivial, since there is only one word with one letter.

For the inductive step, assume that we know that the Opt function as written above finds the optimum solution for the indices less than $i$, and we want to show that the value Opt(i) is the optimum cost of any segmentation for the prefix of $y$ up to the $i$-th character. We consider the last word in the optimal segmentation of this prefix. Let's assume it starts at index $j \leq i$. Then according to our key observation above, the prefix containing only the first $j-1$ characters must also be optimal. But according to our induction hypothesis, $\operatorname{Opt}(j)$ will yield us the value of the aforementioned optimal segmentation. Therefore the optimal cost Opt(i) would be equal to Opt(j) plus the cost of the last word.

But notice that our above recurrence exactly does this calculation for each possibility of the last word. Therefore our recurrence will correctly find the cost of the optimal segmentation.

As for the running time, a simple implementation (direct evaluation of the above formula starting at index 1 until $n$, where $n$ is the number of characters in the input string) will yield a quadratic algorithm.

Question 7 
Let $X_{j}$ (for $j=1, \ldots, n$ ) denote the maximum possible return the investors can make if they sell the stock on day $j$. Note that $X_{1}=0$. Now, in the optimal way of selling the stock on day $j$, the investors were either holding it on day $j-1$ or there weren't. If they weren't, then $X_{j}=0$. If they were, then $X_{j}=X_{j-1}+(p(j)-p(j-1))$. Thus, we have

$$
X_{j}=\max \left(0, X_{j-1}+(p(j)-p(j-1))\right) \text {. }
$$

Finally, the answer is the maximum, over $j=1, \ldots, n$, of $X_{j}$.

Question 10
Here are two examples:

$$$$
\begin{tabular}{|c||c|c|}
\hline & Minute 1 & Minute 2 \\
\hline A & 2 & 10 \\
\hline B & 1 & 20 \\
\hline
\end{tabular}

The greedy algorithm would choose $A$ for both steps, while the optimal solution would be to choose $B$ for both steps.

\begin{tabular}{|c||c|c|c|c|}
\hline & Minute 1 & Minute 2 & Minute 3 & Minute 4 \\
\hline A & 2 & 1 & 1 & 200 \\
\hline B & 1 & 1 & 20 & 100 \\
\hline
\end{tabular}

The greedy algorithm would choose $A$, then move, then choose $B$ for the final two steps. The optimal solution would be to choose $A$ for all four steps.

(1b) Let $\operatorname{Opt}(i, A)$ denote the maximum value of a plan in minutes 1 through $i$ that ends on machine $A$, and define $O p t(i, B)$ analogously for $B$.

Now, if you're on machine $A$ in minute $i$, where werc you in minutc $i-1 ?$ Either on machine $A$, or in the process of moving from machine $B$. In the first case, we have $\operatorname{Opt}(i, A)=a_{i}+\operatorname{Opt}(i-1, A)$. In the second case, since you were last at $B$ in minute $i-2$, we have $\operatorname{Opt}(i, \Lambda)=a_{i} \mid \operatorname{Opt}(i-2, B)$. Thus, overall, we have

$$
\operatorname{Opt}(i, A)=a_{i}+\max (O p t(i-1, A), O p t(i-2, B))
$$

A symmetric formula holds for $\operatorname{Opt}(i, B)$.

The full algorithm initializes $\operatorname{Opt}(1, A)-a_{1}$ and $\operatorname{Opt}(1, B)-b_{1}$. Then, for $i-2,3, \ldots, n$, it computes $\operatorname{Opt}(i, A)$ and $O p t(i, B)$ using the recurrence. This takes constant time for each of $n-1$ iterations, and so the total time is $O(n)$.

Ilere is an alternate solution. Let $\operatorname{Opt}(i)$ be the maximum value of a plan in minutes 1 through $i$. Also, initialize $O p t(-1)=O p t(0)=0$. Now, in minute $i$, we ask: when was the most recent minute in which we moved? If this was minute $k-1$ (where perhaps $k-1=0$ ), then $O p t(i)$ would be equal to the best we could do up through minute $k-2$, followed by a move in minute $k-1$, followed by the best we could do on a single machine from minutes $k$ through $i$. Thus, we have

$$
O p t(i)=\max _{1 \leq k \leq i} O p t(k-2)+\max \left[\sum_{\ell=k}^{i} a_{\ell}, \sum_{\ell=k}^{i} b_{\ell}\right]
$$

The full algorithm then builds up these values for $i-2,3, \ldots, n$. Each iteration takes $O(n)$ time to compute the maximum, so the total running time is $\mathcal{O}\left(n^{2}\right)$.

A common type of error is to use a single-variable set of sub-problems as in the second correct solution (using Opt(i) to denote the maximum value of a plan in minutes 1 through $i$ ), but with a recurrence that computed $O p t(i)$ by looking only at $O p t(i-1)$ and $O p t(i-2)$. For example, a common recurrence was to let $m_{j}$ denote the machine on which the optimal plan for minutes 1 through $j$ ended, let $c\left(m_{j}\right)$ denote the number of steps available on machine $m_{j}$ in minute $j$, and then write $O p t(i)=\max \left(O p t(i-1)+c\left(m_{i-1}\right), O p t(i-2)+c\left(m_{i-2}\right)\right)$. But if we consider an example like

\begin{tabular}{|c||c|c|c|}
\hline & Minute 1 & Minute 2 & Minute 3 \\
\hline A & 2 & 10 & 200 \\
\hline B & 1 & 20 & 100 \\
\hline
\end{tabular}

then $\operatorname{Opt}(1)=2, \operatorname{Opt}(2)=21, m_{1}=A$, and $m_{2}=B$. But $O p t(3)=212$, which does not follow from the recurrence above. There are a number of variations on the above recurrence, but they all break on this example.

Question 17
(a) Consider the sequence 1,4,2,3. The greedy algorithm produces the rising trend 1, 4 , while the optimal solution is $1,2,3$.

(b) Let $O P T(j)$ be the length of the longest increasing subsequence on the set $P[j], P[j+$ $1]$, ldots, $P[n]$, including the element $P[j]$. Note that we can initialize $O P T(n)=1$, and $O P T(1)$ is the length of the longest rising trend, as desired.

Now, consider a solution achieving $O P T(j)$. Its first element is $P[j]$, and its next element is $P[k]$ for some $k>j$ for which $P[k]>P[j]$. From $k$ onward, it is simply the longest increasing subsequence that starts at $P[k]$; in other words, this part of the sequence has length $O P T(k)$, so including $P[j]$, the full sequence has length $1+O P T(k)$. We have thus justified the following recurrence.

$$
O P T(j)=1+\max _{k>j: P|k|>P|j|} O P T(k)
$$

The values of $O P T$ can be built up in order of decreasing $j$, in time $O(n-j)$ for iteration $j$, leading to a total running time of $O\left(n^{2}\right)$. The value we want is $O P T(1)$, and the subsequence itself can be found by tracing back through the array of $O P T$ values.

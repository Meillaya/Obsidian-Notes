We know from the text that polynomials (i.e. a sum of terms where $n$ is raised to fixed powers, even if they are not integers) grow slower than exponentials. Thus, we will consider $f_{1}, f_{2}, f_{3}, f_{6}$ as a group, and then put $f_{4}$ and $f_{5}$ after them.

For polynomials $f_{i}$ and $f_{j}$, we know that $f_{i}$ and $f_{j}$ can be ordered by comparing the highest exponent on any term in $f_{i}$ to the highest exponent on any term in $f_{j}$. Thus, we can put $f_{2}$ before $f_{3}$ before $f_{1}$. Now, where to insert $f_{6}$ ? It grows faster than $n^{2}$, and from the text we know that logarithms grow slower than polynomials, so $f_{6}$ grows slower than $n^{c}$ for any $c>2$. Thus we can insert $f_{6}$ in this order between $f_{3}$ and $f_{1}$.

Finally come $f_{4}$ and $f_{5}$. We know that exponentials can be ordered by their bases, so we put $f_{4}$ before $f_{5}$.
We know that polynomials grow slower in comparison to exponentials. As such, $f_{1}, f_{2}, f_{3}, f_{6}$ as a group will come first and then $f_{4}$ and $f_{5}$ after. We know that for polynomials $f_{i}$ and $f_{j}$,  $f_{i}$ and $f_{j}$ can be ordered according to the highest exponent on terms in $f_{i}$ in comparison to the highest exponent on terms in $f_{j}$. Therefore, the initial ordering is as follows: $f_{2}$, $f_{3}$, $f_{1}$.

$f_{6}$ grows at a greater rate than $n^{2}$ and logarithms grow at a slower rate compared to polynomials, as such $f_{6}$ grows slower than $n^{c}$ for any $c > 2$. Thus, $f_{6}$ comes after $f_{3}$ and before $f_{1}$. For $f_{4}$ and $f_{5}$, because exponentials are ordered by their base, $f_{4}$ comes before $f_{5}$. Therefore, the final ordering is as follows:

$f_{2}$, $f_{3}$,$f_{6}$, $f_{1}$, $f_{4}$, $f_{5}$


4
The functions are ordered in the following order:
- $g_1$ comes before $g_5$. Taking logarithms, we compare $\sqrt{\log n}$ to $\log n \mid \log (\log n) \geq \log n$; changing variables via $z=\log n$, results in $\sqrt{z}=z^{1 / 2}$ versus $z+\log z \geq z$.
- $g_5$ comes before $g_3$, $(\log n)^3$ grows faster than log $n$. 
- $g_3$ co before $g_4$ : Dividing both by $n$, we compare (log $\left.n\right)^3$ with $n^{1 / 3}$ or $\log n$ with $n^{1 / 9}$. Logarithms grow slower than exponentials.
- $g_4$ comes before $g_2$, polynomials grow slower than exponentials.
- $g_2$ comes before $g_7$ : Taking logarithms, comparing $n$ to $n^2$, and $n^2$ is the polynomial with the larger degree.
- $g_7$ comes before $g_6$ : Taking logarithms, comparing $n^2$ to $2^n$, and polynomials grow slower than exponentials.
The right ordering (from smallest to largest) is: $g_{1}, g_{3}, g_{4}, g_{5}, g_{2}, g_{7}, g_{6}$




(i) This is false in general, since it could be that $g(n)=1$ for all $n, f(n)=2$ for all $n$, and then $\log _{2} g(n)=0$, whence we cannot write $\log _{2} f(n) \leq c \log _{2} g(n)$.

On th other hand, if we simply require $g(n) \geq 2$ for all $n$ beyond some $n_{1}$, then the statement holds. Since $f(n) \leq c g(n)$ for all $n \geq n_{0}$, we have $\log _{2} f(n) \leq \log _{2} g(n)+$ $\log _{2} c \leq\left(\log _{2} c\right)\left(\log _{2} g(n)\right)$ once $n \geq \operatorname{mrax}\left(n_{0}, n_{1}\right)$.

(ii) This is false: take $f(n)=2 n$ and $g(n)=n$. Then $2^{\prime(n)}=4^{\prime \prime}$, while $2^{g(n)}=2^{n}$.

(iii) This is true. Since $f(n) \leq c g(n)$ for all $n \geq n_{0}$, we have $(f(n))^{2} \leq c^{2}(g(n))^{2}$ for all $n \geq n_{0}$.



(a) Suppose for simplicity that $n$ is a perfect square. We drop the first jar from heights that are multiples of $\sqrt{n}$ (i.e. from $\sqrt{n}, 2 \sqrt{n}, 3 \sqrt{n}, \ldots$ ) until it breaks.

If we drop it from the top rung and it survives, then we're also done. Otherwise, suppose it breaks from height $j \sqrt{n}$. Then we know the highest safe rung is between $(j-1) \sqrt{n}$ and $j \sqrt{n}$, so we drop the second jar from rung $1+(j-1) \sqrt{n}$ on mpward, going up by one each time.

In this way, we drop each of the two jars at most $\sqrt{n}$ times, for a total of at most $2 \sqrt{n}$. If $n$ is not a perfect square, then we drop the first jar from heights that are multiples of $\lfloor\sqrt{n}\rfloor$, and then apply the above rule for the second jar. In this way, we drop the first jar at most $2 \sqrt{n}$ times (quite an overestimate if $n$ is reasonably large) and the second jar at most $\sqrt{n}$ times, still obtaining a bound of $O(\sqrt{n})$.

(b) We claim by induction that $f_{k}(n) \leq 2 k n^{1 / k}$. We begin by dropping the first jar from heights that are multiples of $\left\lfloor n^{(k-1) / k}\right\rfloor$. In this way, we drop the first jar at most $2 n / n^{(k-1) / k}=2 n^{1 / k}$ times, and thus narrow the set of possible rungs down to an interval of length at most $n^{(k-1) / k}$.

We then apply the strategy for $k-1$ jars recursively. By induction it uses at most $2(k-1)\left(n^{(k-1) / k}\right)^{1 /(k-1)}=2(k-1) n^{1 / k}$ drops. Adding in the $\leq 2 n^{1 / k}$ drops made using the first jar, we get a bound of $2 k n^{1 / k}$, completing the induction step.





2
We'll define a recursive divide-and-conquer algorithm ALG which takes a sequence of distinct numbers $a_{1}, \ldots, a_{n}$ and returns $N$ and $a_{1}^{\prime}, \ldots, a_{n}^{\prime}$ where

- $N$ is the number of significant inversions

- $a_{1}^{\prime}, \ldots, a_{n}^{\prime}$ is same sequence sorted in the increasing order

ALG is similar to the algorithm from the chapter that computes the number of inversions. The difference is that in the 'conquer' step we merge twice: first we merge $b_{1}, \ldots, b_{k}$ with $b_{k+1}, \ldots, b_{n}$ just for sorting, and then we merge $b_{1}, \ldots, b_{k}$ with $2 b_{k+1}, \ldots, 2 b_{n}$ for counting significant inversions.

Let's define ALG formally. For $n=1$ ALG just returns $N=0$ and $\left\{a_{1}\right\}$ for the sequence. For $n>1$ ALG does the following:

- let $k=\lfloor n / 2\rfloor$.

- call $\operatorname{ALG}\left(a_{1}^{\prime}, \ldots, a_{k}^{\prime}\right)$. Say it returns $N_{1}$ and $b_{1}, \ldots, b_{k}$.

- call $\operatorname{ALG}\left(a_{k_{1}}^{\prime}, \ldots, a_{n}^{\prime}\right)$. Say it returns $N_{2}$ and $b_{k+1}, \ldots, b_{n}$.

- compute the number $N_{3}$ of significant inversions $\left(a_{i}, a_{j}\right)$ where $i \leq k<j$.

- return $N-N_{1}+N_{2}+N_{3}$ and $a_{1}^{\prime}, \ldots, a_{n}^{\prime}-\operatorname{MERGE}\left(b_{1}, \ldots, b_{k} ; b_{k+1}, \ldots, b_{n}\right)$

MERGE can be implemented in $O(n)$ time. According to the discussion in the book, it remains to find a way to compute $N_{3}$ in $O(n)$ time. We implement a variant of merge-count of $b_{1}, \ldots, b_{k}$ and $2 b_{k+1}, \ldots, 2 b_{n}$ as follows.

- Initialize counters: $i \leftarrow k, j \leftarrow n, N_{3} \leftarrow 0$.

- If $b_{i} \leq 2 b_{j}$ then

- if $j>k+1$ decrease $j$ by 1 .

- if $j=k+1$ return $N_{3}$.

- If $b_{i}>2 b_{j}$ then increase $N_{3}$ by $j-k$. Then

- if $i>1$ decrease $i$ by 1 .

- if $i=1$ return $N_{3}$.

Explanation For every $i$ we count the number of significant inversions between $b_{i}$ and all $b_{j}$ 's. If $b_{i} \leq 2 b_{j}$ then there are no significant inversions between $b_{i}$ and any $b_{m}$ s.t. $m \geq j$, so we decrease $j$. If $b_{i}>2 b_{j}$ then $b_{i}>2 b_{m}$ for all $m$ s.t. $k<m \leq j$. In other words, we have detected $j-k$ significant inversions involving $b_{i}$. So we increase $N_{3}$ by $j-k$. Finally, when we are down to $i=1$ and have counted significant inversions involving $b_{1}$, there are no more significant inversions to be detected.


3
We give two solutions for this problem. The first solution is a divide and conquer algorithm, which is easier to think of. The second solution is a clever linear time algorithm.

Via divide and conquer: Let $e_{1}, \ldots, e_{n}$ denote the equivalence classes of the cards: cards $i$ and $j$ are equivalent if $e_{i}=e_{j}$. What we are looking for is a value $x$ so that more than $n / 2$ of the indices have $e_{i}=x$.

Divide the set of cards into two roughly equal piles: a set of $\lfloor n / 2\rfloor$ cards and a second set for the remaining $\lceil n / 2\rceil$ cards. We will recursively run the algorithm on the two sides, and will assume that if the algorithm finds an equivalence class containing more than half of the cards, then it returns a sample card in the equivalence class.

Note that if there are more than $n / 2$ cards that are equivalent in the whole set, say have equivalence class $x$, than at least one of the two sides will have more than half the cards also equivalent to $x$. So at least one of the two recursive calls will return a card that has equivalence class $x$.

The reverse of this statement is not true: there can be a majority of equivalent cards in one side, without that equivalence class having more than $n / 2$ cards overall (as it was only a majority on one side). So if a majority card is returned on either side we must test this card against all other cards.

```python
if |S| = 1 return one card
if |S| = 2
	test equivalence between the two cards
	return card if equivalent
S1 = set of the first n/2 cards
S2 = set of remaining cards

Recursive call on S1

If card returned
	test against all cards
If no card with majority equivalence detected
	call S2 recursively
	if card found
		test against all cards
Return card from majority equivalence class if card detected
```

The correctness of the algorithm follows from the observation above: that if there is a majority equivalence class, than this must be a majority equivalence class for at least one of the two sides.

To analyze the running time, let $T(n)$ denote the maximum number of tests the algorithm does for any set of $n$ cards. The algorithm has two recursive calls, and does at most $2 n$ tests outside of the recursive calls. So we get the following recurrence (assuming $n$ is divisible by 2):

$$
T(n) \leq 2 T(n / 2)+2 n .
$$

As we have seen in the chapter, this recurrence implies that $T(n)=O(n \log n)$.

In linear time: Pair up all cards, and test all pairs for equivalence. If $n$ was odd, one card is unmatched. For each pair that is not equivalent, discard both cards. For pairs that are equivalent, keep one of the two. Keep also the immatched card, if $n$ is odd. We can call this subroutine Eliminate.

The observation that leads to the linear time algorithm is as follows. If there is an equivalence class with more then $\mathrm{n} / 2$ cards, than the same equivalence class must also have more than half of the cards after calling ELIMINATE. This is true, as when we discard both cards in a pair, then at most one of them can be from the majority equivalence class. One call to FrimminatF, on a set of $n$ cards takes $n / 2$ tests, and as a result, we have only $\leq\lceil n / 2\rceil$ cards left. When we are down to a single card, then its equivalence is the only candidate for having a majority. We test this card against all others to check if its equivalence class has more than $n / 2$ elements.

This method takes $n / 2+n / 4+\ldots$ tests for all the eliminates, plus $n-1$ tests for the final counting, for a total of less than ' $2 n$ tests.



4
This can be accomplished directly using a convolution. Define one vector to be $a=$ $\left(q_{1}, q_{2}, \ldots, q_{n}\right)$. Define the other vector to be $b=\left(n^{-2},(n-1)^{-2}, \ldots, 1 / 4,1,0,-1,-1 / 4, \ldots-\right.$ $\left.n^{-2}\right)$. Now, for each $j$, the convolution of $a$ and $b$ will contain an entry of the form

$$
\sum_{i<j} \frac{q_{i}}{(j-i)^{2}}+\sum_{i>j} \frac{-q_{i}}{(j-i)^{2}} .
$$

From this term, we simply multiply by $C q_{j}$ to get the desired net force $F_{j}$.

The convolution can be computed in $O(n \log n)$ time, and reconstructing the terms $F_{j}$ takes an additional $O(n)$ time.




6
For simplicity, we will say $u$ is smaller than $v$, or $u \prec v$, if $x_{u}<x_{v}$. We will extend this to sets: if $S$ is a set of nodes, we say $u \prec S$ if $u$ has a smaller value than any node in $S$.

The algorithm is the following. We begin at the root $r$ of the tree, and see if $r$ is smaller than its two children. If so, the root is a local minimum. Otherwise, we move to any smaller child and iterate.

The algorithm terminates when either (1) we reach a node $v$ that is smaller than both its children, or (2) we reach a leaf $w$. In the former case, we return $v$; in the latter case, we return w.

The algorithm performs $O(d)=O(\log n)$ probes of the tree; we must now argue that the returned value is a local minimum. If the root $r$ is returned, then it is a local minimum as explained above. If we terminate in case (1), $v$ is a local minimum because $v$ is smaller than its parent (since it was chosen in the previous iteration) and its two children (since we terminated). If we terminate in case (2), $w$ is a local minimum because $w$ is smaller than its parent (again since it was chosen in the previous iteration).





7
Let $B$ denote the set of nodes on the border of the grid $G$ - i.e. the outermost rows and columns. Say that $G$ has Property $(*)$ if it contains a node $v \notin B$ that is adjacent to a node in $B$ and satisfies $v \prec B$. Note that in a grid $G$ with Property $(*)$, the global minimum does not occur on the border $B$ (since the global minimum is no larger than $v$, which is smaller than $B$ ) - hence $G$ has at least one local minimum that does not occur on the border. We call such a local minimum an internal local minimum.

We now describe a recursive algorithm that takes a grid satisfying Property $(*)$ and returns an internal local minimum, using $O(n)$ probes. At the end, we will describe how this can be easily converted into a solution for the overall problem.

Thus, let $G$ satisfy Property $(*)$, and let $v \notin B$ be adjacent to a node in $B$ and smaller than all nodes in $B$. Iet $C$ denote the union of the nodes in the middle row and middle column of $G$, not counting the nodes on the border. Let $S=B \cup C$; deleting $S$ from $G$ divides up $G$ into four sub-grids. Finally, let $T$ be all nodes adjacent to $S$.

Using $O(n)$ probes, we find the node $u \in S \cup T$ of minimum value. We know that $u \notin B$, since $v \in S \cup T$ and $v \prec B$. Thus, we have two cases. If $u \in C$, then $u$ is an internal local minimum, since all of the neighbors of $u$ are in $S \cup T$, and $u$ is smaller than all of them. Otherwise, $u \in T$. Let $G^{\prime}$ be the sub-grid containing $u$, together with the portions of $S$ that border it. Now, $G^{\prime}$ satisfies Property $(*)$, since $u$ is adjacent to the border of $G^{\prime}$ and is smaller than all nodes on the border of $G^{\prime}$. 'Thus, $G^{\prime}$ has an internal local minimum, which is also an internal local minimum of $G$. We call our algorithm recursively on $G^{\prime}$ to find such an internal local minimum.

If $I '(n)$ denotes the number of probes needed by the algorithm to find an internal local minimum in an $n \times n$ grid, we have the recurrence $T(n)=O(n)+T(n / 2)$, which solves to $T(n)-O(n)$

Finally, we convert this into an algorithm to find a local minimum (not necessarily internal) of a grid $G$. Using $O(n)$ probes, we find the node $v$ on the border $B$ of minimum value. If $v$ is a corner node, it is a local minimum and we're done. Otherwise, $v$ has a unique neighbor $u$ not on $B$. If $v \prec u$, then $v$ is a local minimum and again we're done. Otherwise, $G$ satisfies Property $(*$ ) (since $u$ is smaller than every node on $B$ ), and we call the above algorithm.


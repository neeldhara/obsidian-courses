---
{"dg-publish":true,"permalink":"/materials/dsa/euler-tours/","hide":true}
---

[Link to Companion Slides](https://slides.com/neeldhara/euler-tours)

## Euler Tours

We revisit the following problem from our introduction to graphs:

> [!caution]+ The Problem
> The city of Königsberg in Prussia (now Kaliningrad, Russia) was set on both sides of the Pregel River, and included two large islands—Kneiphof and Lomse—which were connected to each other, and to the two mainland portions of the city, by seven bridges.
> 
> Devise a walk through the city that would cross each of those bridges once and only once. Try this yourself on a few different maps at [Mathigon](https://mathigon.org/course/graph-theory/bridges)!

We also found such traversals useful for computing de Bruijn sequences, so between success on city exploration challenges and impressing with card tricks, there is plenty of motivation to take an Euler tour in a graph.

In general, we are given a directed or undirected graph $G = (V,E)$ and we want to know if there is a sequence of edges:

$$W := e_0 = (u_0,v_0), \ldots, e_{m-1} = (u_{m-1},v_{m-1})$$

such that $v_i = u_{i+1 \mod m}$ for all $i \in \{0,1,\ldots,m-1\}$, and every edge in $E$ features _exactly once_ in this sequence.

### Necessary and sufficient conditions

Note that if such a sequence does exist for a directed graph $G$, then the indegree of every vertex must equal its outdegree, i.e:

> indegree$(v)$ = outdegree$(v)$ for all $v \in V$.

Likewise, if such a sequence exists for an undirected graph $G$, then every vertex must have even degree:

> degree$(v) = 2k_v$ for all $v \in V$ and some integer $k_v$.

You can observe this based on simulating the sequence on the graph and imagining it from the perspective of your favorite vertex $v$ in it. In particular, assume you are walking around in $G$ as dictated by $W$. Fix your attention on $v$: every time you "enter" $v$, via, say the edge $e_i$, then you must "exit" $v$ via the edge $e_{i+1}$. If $G$ is directed, $e_i$ is an incoming edge and $e_{i+1}$ is an outgoing edge, and if $G$ is undirected, these are simply two edges incident on $v$ that can be naturally "paired off". So any successful walk witnesses the claims above.

> [!warning]+ These conditions are necessary, but are they sufficient?
> 
> It turns out that you could have graphs where these conditions are true, but there are no Euler tours. This happens when the graph is "disconnected", i.e, when there is a pair of vertices $u$ and $v$ such that there is no path from $u$ to $v$. The following are good exercises to work through:
> 
> - Come up with an example of a graph where the degree conditions are met but there is no Euler tour.
> 
> - Convince yourself that if $G$ is connected and satisfies the degree conditions indicated above, you can always find an Euler tour.

### A naive algorithm

Now we turn to the procedural question: knowing what it takes to find an Euler tour, how do we actually find one? First, we get the simple degree-based sanity check out of the way. For undirected graphs we have:

```plaintext
for v in V(G):
    if deg[v] % 2 != 0:
        return False
```

and for directed graphs we have:

```plaintext
for v in V(G):
    if indeg[v] != outdeg[v]:
        return False
```


Assuming we pass these sanity checks, we want to embark on an actual tour. Here's a reasonable starting point, which essentially amounts to saying that you get to start anywhere, and keep going while you can:


```plaintext
find_tour(G,v):
    // G is the graph
    // and v is our favorite vertex
    set curr := v
    set S := empty
    while there is an outgoing edge e = (curr,u) which is not in S:
        add e to S
        set curr := u
    return S
```

This is basically a "keep going until stuck" process. By the very nature of the process, the sequence $S$ that we come up with is _walkable_ and does not repeat edges, but it is unclear if this list is exhaustive. Indeed, you should be able to come up with examples of graphs $G$ where $G$ has an Euler tour but `find_tour(G)` does not output one.

### Fixing the naive approach

How do we fix this? For one, we need to know if we are done or not: if an edge is missing from $S$, then that's a bad sign, and we need to do something about it. How do we know if every edge is enlisted in the output? One way is to compute the length of $S$: if it falls short of $m$, we are not done yet.


But we also need to know what the missing edges are. We could in principle go through our edge list and ask ourselves if the edge made it to $S$ or not, but that sounds mildly painstaking. Let's save ourselves the pain with some additional bookkeeping --- let's track the "residual degree" of the vertices: this is the number of edges incident on $v$ that are not yet listed in $S$. Any vertex with non-zero residual degree gives us concrete hints about missing edges.

So for directed graphs we have:

```plaintext
find_tour(G,v):
    init res_deg[v] = outdeg[v]
    set curr := v
    set S := empty
    while there is an outgoing edge e = (curr,u) which is not in S:
        add e to S
        res_deg[curr] = res_deg[curr]-1
        set curr := u
    return S
```

and for undirected graphs we have:

```plaintext
find_tour(G,v):
    init res_deg[v] = deg[v]
    set curr := v
    set S := empty
    while there is an outgoing edge e = (curr,u) which is not in S:
        add e to S
        res_deg[curr] = res_deg[curr]-1
        res_deg[u] = res_deg[u]-1
        set curr := u
    return S
```

So now we know when our algorithm is a fail. What's the fix? Well, let's approach vertices who are not done yet as per our intel from their `res_deg` value. We use these vertices to trigger more happy-go-lucky tours:


```plaintext
find_tour_fr(G):
    i := 0
    marked := emptyset
    res_deg[v] := outdeg[v]
    S := list of lists
    while there is some v with res_deg[v] > 0:
        let S[i] := find_tour(G,v,marked)
        add every edge in S_i to marked
        i = i+1
```


Since we need to track visited edges across multiple runs now, we actually inform the `find_tour` function about the edges already visited from past lives. This is tracked with the `marked` set.

So our updated `find_tour` function looks like this:

```plaintext
find_tour(G,v,marked):
    set curr := v
    set S := empty
    while there is an outgoing edge e = (curr,u)
    which is not in S or marked:
        add e to S
        res_deg[curr] = res_deg[curr]-1
        set curr := u
    return S
```

(The change is analogous for the version dealing with undirected graphs.)

What we have now is a bunch of fragments, each of which is essentially a walk that begins and ends at the same vertex. Because of our relentless and careful pursuit (c.f. the while condition and the marked set), every edge in $G$ features in _exactly_ one of these fragments. Now it's just a matter of putting everything together.

Start with the first fragment $S_0$. If this is the only fragment we have, that means that our first happy-go-lucky tour was in fact also a lucky one! So we have nothing left to do. Otherwise, there are at least two fragments. Let us look at the set of vertices involved in $S_0$. The crucial observation is that there must be at least one other fragment, say $S_i$, that also features some vertex that appears in $S_0$. Indeed, if this is not the case, then you can argue that $S_0$ is a sad isolated fragment, and we can actually report that $G$ has no Euler tour.

Otherwise, find the common vertex between $S_0$ and $S_i$, and extend one of them using the other: for example, if $v$ is the common vertex, take a walk in $S_0$ until you encounter $v$, and then instead of following along on $S_0$, take a detour as specified by $S_i$. Remember if you start on $S_i$ at $v$, then you will eventurally exhaust $S_i$ by coming back to $v$: and at this point you can "resume" your walk on $S_0$. Note that this process welds two fragments at the vertex $v$ thereby reducing the total number of fragments by one. This should count as a sure sign of progress: repeating for as long as possible, we have to do this at most $(f-1)$ many times, where $f \leq \frac{m}{2}$ is the total number of fragments.

```
patchup():
    Let S[i] for i in 1, 2, ..., f denote the set of all fragments
    while f > 1:
        look for a fragment S[i] that intersects S[0]
        if S[i] does not exist:
            return false
        else:
            expand S[0] along S[i]
            remove S[i] from the set of all fragments
```

### Expenses

Although arguably a naive algorithm, the cool thing about this procedure is that it is guaranteed to work, and the number of steps involved is not terribly bad either. Here's a naive back-of-the-envelope analysis, assuming $G$ is stored as an adjacency list:

1. The degree-based sanity checks are $\approx m$ since $G$ is stored as an adjacency list.
2. Consider `find_tour_fr(G)`:
    - The outer `while` loop runs at most $m$ times since each iteration decreases the residual degree of at least two vertices and the sum of residual degrees is $2m$ at the start (an analogous argument applies for directed graphs).
    - The inner `while` loop in `find_tour(G,v,marked)` is executed at most $m$ times. To find an appropriate edge, we have to go through the negibors of `curr` and check if the associated edge is already in `S` or `marked`. This takes at most $(nm)$ iterations in the worse case, if implemented directly.
    - Assuming that `S` is a linked list and `res_deg` is an array, the innermost operations are all constant time.
    - The overall cost of a direct implementation is therefore $nm^3$.
3. The `patchup` procedure involves a outer `while` loop that runs at most $f$ times if we have $f$ fragments. The looking business to merge fragments will take no more than $m$ units of time: worst case we have to scan all remaining fragments to find a suitable match, and the merger involves updating a few pointers --- noting again that the fragments are stored as lists. This is of course a conservative estimate, but it will do. The overall time here is therefore no worse than $\approx m^2$ since $f \leq \frac{m}{2}$.

This gives us $m + nm^3 + m^2$ in total damages. However, notice that a more careful analysis helps us do better without doing anything substantially different. If you think about `find_tour_fr(G)` think about how often the instructions:

```
add e to S
res_deg[curr] = res_deg[curr]-1
set curr := u
```

from `find_tour(G,v,marked)` are actually executed. Every time we execute this set of instructions, we effectively add one edge to the set of marked edges, and since this happens exactly once per edge, these instructions only execute $m$ times overall. Recall that what it takes to enter this loop is the discovery of an unused edge:

```
while there is an outgoing edge e = (curr,u)
which is not in S or marked
```

This is the bit that took us a while, because we assumed we have to examine all possible edges that go out of `curr` and then also tally up against `S` and `marked`. One way to speed this up is to always commit to pulling out the first element in the adjacency list of the vertex `u` and then in fact deleting this element from the list. If you are paranoid about subjecting your input to this kind of annihilation, then you can just make a working copy upfront. This way, you can be sure that you can find what you want in constant time, a good case in point to show how the way you store your data can impact the performance of your algorithm.

Based on the hints above, convince yourself that `find_tour_fr(G)` in fact has a total expense amounting to $\approx m$, modulo constants. With this, our overall cost comes down to $\approx 2m + m^2$.

### Afterthoughts

Can we do better? Indeed, it turns out that with a slightly more careful implementation, the business of merging fragments can also be done with an expense proportional to the number of edges. The careful version goes by Hierholzer's algorithm, and you can read up about this [on Wikipedia](https://en.wikipedia.org/wiki/Eulerian_path#Hierholzer's_algorithm) or watch [this video](https://www.youtube.com/embed/8MpoO2zA2l4).
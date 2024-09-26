---
{"dg-publish":true,"permalink":"/materials/dsa/stable-matchings/"}
---


[Link to Companion Slides](https://slides.com/neeldhara/stable-matchings)

# Stable Matchings

The problem of pairing up people and/or resources shows up a lot:

- Matching students who graduate high school to seats in various colleges.
- Matching students who graduate college to employers for jobs, internships, residencies, and so on.
- Getting actors and actresses to commit to work together for films amidst various constraints.
- Matching organ donors to patients accounting for constraints of compatibility and timing.
- Matching men and women in a dating/marriage market.

We are going to look at one particular abstraction that captures many of the scenarios above (among others). Suppose we have a set $V = \{m_1, \ldots, m_n\}$ of $n$ men and $W = \{w_1, \ldots, w_n\}$ of $n$ women, where each man (respectively, woman) has a strict and complete ranking over the women (respectively, men). Our goal is to find a _matching_ between the men and the women, which is to say, a bijection between $V$ and $W$.

Now, a natural question at this point is: what kind of matchings do we want to find? Unconstrained, there are plenty of matchings that we can choose from. Which one is the "best"?

Upon a moment's reflection you might come up with several ideas. We are going to focus on a fundamental game-theoretic approach to identifying what we desire from the matchings we seek. What we will demand of the matching $M$ that we seek is that there _is no man and woman who are unmatched in $M$ who prefer each other over their matched partners_. To this end, we first define the notion of a blocking pair with respect to $M$:

> [!Note]+ Blocking Pair
> 
> Given a matching $M$ between $n$ men and $n$ women, if $a \in V$ and $b \in W$, then $(a,b)$ forms a _blocking pair_ if ALL of the following hold:
> 
> - $a$ and $b$ are _not_ matched to each other in $M$,
> 
> - $a$ prefers $b$ over $M(a)$,
> 
> - $b$ prefers $a$ over $M(b)$

The presence of a blocking pair $(a,b)$ implies that the matching $M$ is unlikely to "sustain": $a$ and $b$ _both_ have an incentive to break off the alliances suggested by the matching $M$ and "elope" with each other instead. Thus, matchings that have blocking pairs are called **unstable**.

> [!Note]+ Unstable Matching
>
> A matching $M$ is said to be _unstable_ if there is a blocking pair with respect to $M$.


> [!Caution]- An Example of a Matching with _no_ blocking pairs.
> 
> Consider the preferences given below (where the first column in each row is the ID of the men and the women, and the remaining columns indicate the rank):
> 
>| Men | 1 | 2 | 3 | 4 |
>| --- | --- | --- | --- | --- |
>| 1 | 2 | 4 | 1 | 3 |
>| 2 | 3 | 1 | 4 | 2 |
>| 3 | 2 | 3 | 1 | 4 |
>| 4 | 4 | 1 | 3 | 2 |
>
>| Women | 1 | 2 | 3 | 4 |
>| ----- | --- | --- | --- | --- |
>| 1 | 2 | 1 | 4 | 3 |
>| 2 | 4 | 3 | 1 | 2 |
>| 3 | 1 | 4 | 3 | 2 |
>| 4 | 2 | 1 | 4 | 3 |
> and the matching given by: **M = (1,4), (2,3), (3,2), (4,1)**. 
> Notice that this matching has, in fact, _no_ blocking pairs.

> [!question] Food for thought.
> How many blocking pairs can we have?
> Come up with a stable matching instance that has $\Omega(n^2)$ blocking pairs. What's the maximum number possible?

A matching without blocking pairs is called **stable**.

> [!note] Stable Matching
>
> A matching $M$ is said to be _stable_ if there are no blocking pairs with respect to $M$.

It's easy to verify if a _given_ matching $M$ is stable: for all men $m$ we look up all women $w$ that $m$ ranks higher than $M(m)$, and check if $w$ also ranks $m$ higher than $M(w)$: if yes, then we can declare $M$ unstable since $(m,w)$ is a blocking pair. If we find no blocking pairs after having checked all men $m$, then we can declare that $M$ is stable.

This takes at most $O(n^2)$ time, assuming that ranks can be retrieved in constant time. Thus we have the following.

> [!note]+ Verifying that a matching is stable.
>
Given a matching $M$ between $n$ men and $n$ women and their preferences over each other, it is possible to verify if $M$ is stable in $O(n^2)$ time.

The next natural questions are:

- Do stable matchings always exist?
- If yes: can we always find them efficiently?
- If not: can we efficiently find matchings that minimize the number of blocking pairs?

This is a good place to pause and ponder!

### Developing a Solution

It turns out that (somewhat surprisingly!) stable matchings indeed always exist!

The algorithm for finding a stable matching works as follows. To begin with, we say that all men and women are _single_, i.e, unmatched to anyone so far.

Anticipating our need for stability, we take a greedy approach: the men attempt to match up to their best option by _proposing_ to them. But notice that this may not be immediately workable: possibly multiple men have the same choice for their top option. This puts the ball in the woman's court, so to speak, and again in the interest of being eventually stable, it's intuitive that the woman will choose to align with the best offer she has among the proposals she's recieved.

Also, since we finally want everyone to be matched, we will also ensure that proposals are not rejected simply because they seem unattractive in absolute terms: if a woman who's single recieves one or more proposals, she will accept the best among them, no matter how good or bad they are.

After one round of proposals, the situation is as follows:

- some women (say $W_\star \subseteq W$) recieved one or more proposals and picked the best offer, and are no longer single;
- some women (say $W_0 = W \setminus W_\star$) recieved no proposals and are still single;
- some men (say $V_\star \subseteq V$) had their proposals accepted and they are no longer single ;
- some men (say $V_0 = V \setminus V_\star$) were turned down and are still single.

If $W_0 = \emptyset$, that's... well, that's awesome, because what that means is all men had distinct choices for their top preference, and so $V_0 = \emptyset$ as well and we already have a matching where everyone has their best possible match: so this is clearly very stable and we are done.

On the other hand, it's possible that $W_0 \neq \emptyset$, which is to say that some women are still single, and therefore there are some single men as well. Now, to make progress, single men go back to the drawing board and propose _again_. Now, a natural question at this point is the following:

> Should the currently single men try their luck again with women who've rejected them?

Well, since they were rejected for good reason (said women had better offers), and the reason has not gone away, it is clearly a waste of time for men to go back to women who've rejected them. So what they do instead is to propose to the _next best option_. Now: what if their next best option is _not_ a single woman? Well, suppose $m$ decides to not approach $w$ because $w$ is matched to some $m^\star$ in the first round. Then $m$ will eventually be matched to someone who's worse than $w$, and _if_ $w$ happened to prefer $m$ over $m^\star$, then $(m,w)$ will eventually be a blocking pair.

However, recall that this is exactly the situation we want to avoid. So we're going to have $m$ propose to their next best option _irrespective_ of whether they are single or not. From the woman's perspective, they are going to recieve proposals again, and we'll let them pick the best offer, _even if it means breaking off their current engagement_.

After this second round of proposals we again have some single men and women, and some engagements. Note that the following invariant is true:

> Any woman who was not single at the end of the first round remains engaged at the end of the second round as well.

Men, on the other hand, may become single again. At this point, we simply continue as before: at the end of every round, the single men continue to propose to their current best option, and the women continue to accept the best offer that they have. We continue this until there are no single men left.

### The Algorithm and its Properties

Here's pseudocode (borrowed from Wikipedia) summarizing the algorithm, which is due to Gale and Shapley. The version below is morally equivalent to our description above, except that all proposals happen one by one, and it turns out that this way of looking at it simplifies the analysis.

```text

Initialize m ∈ M and w ∈ W to free
while ∃ free man m:
    w := first woman on m's list to whom m has not yet proposed
    if w is already engaged (say to m'), then:
        if w prefers m to m' then:
            m' becomes free
            (m, w) become engaged
        end if
    else
        (m, w) become engaged
    end if
repeat

```

It turns out that this procedure:

- terminates in finite time (in fact, after $O(n^2)$ proposals have been made)
- outputs a perfect matching $M$ between the men and the women that has **no blocking pairs**.

The first property follows from the fact that men never propose twice to the same woman, so the number of proposals made is $\leqslant n^2$ . Also note that no man $m$ is rejected by _all_ women: this can only happen if all the women have found better engagements (which are necessarily distinct --- notice that the set of engagments at any stage of the algorithm always forms a valid matching), but there are only $n-1$ men other than $w$: so this is not feasible.

So we know that the `while` loop terminates, and that once it does we have a matching $M$.

It remains to show that $M$ is stable. But if $M$ has a blocking pair $(m,w)$, then $w$ was proposed to by $m$ before $m$ proposed to $M(w)$, and since $(m,w)$ are not matched in $M$, it must be the case that $w$ prefers $M(w)$ over $m$, so $(m,w)$ cannot be a blocking pair after all.

This brings us to the following claim:

> [!tip]- Finding a stable matching
>
> Given a matching $M$ between $n$ men and $n$ women and their preferences over each other, it is possible to find a stable matching $M$ in $O(n^3)$ time.


The output of the Gale-Shapley algorithm has a couple of interesting properties. First off, it turns out that the output is not just stable, but also qualitatively very good. Let us define, for a man $m$, their optimal match as the best woman that $m$ can be matched to in any stable matching. It turns out that $M$ matches all men to their optimal matches!

> [!tip]- The Men Are Lucky
>
> Let $M$ be the output of the GS algorithm. For all men $m$, there is no stable matching $M^\star$ where $m$ prefers $M^\star(m)$ over $M(m)$.


Also, the output of GS is _weakly Pareto optimal_, which is to say that there is _no matching_ (stable or otherwise), where _all_ the men are better off.

> [!tip]- The GS matching is weakly PO
>
> Let $M$ be the output of the GS algorithm. There is no matching $M^\star$ for which it is true that _all_ men $m$ prefer $M^\star(m)$ over $M(m)$.


We state these claims above without proof. The interested reader should look them up!

### References

1. [Numberphile video about the algorithm](https://www.youtube.com/watch?v=Qcv1IqHWAzg)
2. [Numberphile video about the proof](https://www.youtube.com/watch?v=LtTV6rIxhdo)
3. [Notes on implementation details](https://cse.buffalo.edu/faculty/atri/courses/331/fall14/handouts/GS-details.pdf)
4. [Interactive Essay](https://uw-cse442-wi20.github.io/FP-cs-algorithm/)

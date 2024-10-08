---
{"dg-publish":true,"permalink":"/exercises/multi-part-objective/0000-the-game-of-death-csp-edition/"}
---

> [!reference]- Source (spoiler) 
> The Game of Death is a renaming of the [Lights Out!](https://mathworld.wolfram.com/LightsOutPuzzle.html) puzzle. 

> [!note]- Game of Death: Background
> In the *game of death*, we have an array of $N$ rows and $N$ columns (i.e, $N^2$ locations in all), each of which are *alive* or *dead*. A move consists of *poking* a single location.
> 
> When you poke a location, you flip the living state of the location that was poked, and of all its vertical and horizontal neighbors. Given an initial configuration of locations which are alive, the object is to poke a sequence of locations so that all locations are dead at the end.
> 
> The following is an example of a sequence of pokes that achieves this objective:
> ![An example run of the game of death](/img/user/Exercises/Multi-Part-Objective/figures/0000.png)
> 
> Given an initial configuration which specifies which locations are alive, we would like to know if we can win this game, i.e, if there is a sequence of pokes that renders all locations dead. In this problem, we will setup a CSP that could be used to solve this problem for $N = 2$. We use $(1,1)$ to denote the bottom-left corner, $(1,2)$ to denote the bottom-right corner, $(2,1)$ to denote the top-left corner, and $(2,2)$ to denote the top-right corner. Let $L := \{(1,1),(1,2),(2,1),(2,2)\}$.

> [!question]- Part 1.
> You are given an initial configuration $C$. Suppose $C$ can be solved by poking locations $(1,2) \rightarrow (2,1) \rightarrow (2,2)$ in that order. You poke the locations $(2,2) \rightarrow (2,1) \rightarrow (1,2)$ in that order. Do you win the game?
> 
> - [ ] Yes, for any initial configuration $C$.
> - [ ] No, this would never work.
> - [ ] It depends on the initial configuration $C$.

> [!answer]- Spoilers
> The final state of any cell depends on the total number of times that it and its neighbors were poked. This number is the same for any ordering of a given (multi-)set of pokes, so if we have a sequence of pokes that solves $C$, we can interpret the sequence as a set and execute it any order to achieve the same result.

> [!question]- Part 2.
> You are given an initial configuration $C$. Suppose $C$ can be solved by poking locations $(1,2) \rightarrow (2,1) \rightarrow (2,2) \rightarrow (2,1)$ in that order. You poke the locations $(2,2) \rightarrow (1,2)$ in that order. Do you win the game?
> 
> - [ ] Yes, for any initial configuration $C$.
> - [ ] No, this would never work.
> - [ ] It depends on the initial configuration $C$.

> [!answer]- Spoilers
> From the previous part we know that the order does not matter. Thus, given any sequence of pokes, WLOG, reorder it so that pokes at the same location appear together. Now note that poking any fixed location twice consecutively is the same as not poking it at all, so we can delete any location that appears twice consecutively in this sequence. Therefore, in this example, the shorter sequence is as good as the original.

> [!question]- Part 3.
> For expressing this game as a CSP, we would like to have domain that can describe all possible states of the game. Define $D$ as the collection of all subsets of $L$. What is the size of $D$?

> [!answer]- Spoilers
> 16

> [!question]- Part 4.
> Suppose we want to devise a CSP that expresses the following: poking the locations $p_1 \rightarrow p_2 \rightarrow \cdots \rightarrow p_k$ turns the state $S_0$ to the state $S_\emptyset$, where $S_0 \subseteq L$ is a given initial state, and $S_\emptyset$ is the state where all locations are dead.
> 
> In other words, we want the CSP to determine if it is possible to win the given instance of the game of death using exactly $k$ pokes. We first define the variables of our CSP. For $0 \leqslant i \leqslant k$, let $x_i$ be the state of the game after the $i^{th}$ poke, and for $1 \leqslant i \leqslant k$, let $y_i$ be the location of the $i^{th}$ poke.
> 
> In general, what is the domain of these variables?
> 
> - [ ] $x_i$ can take on any value in $D$, and $y_i$ can take on any value in $L$.
> - [ ] $x_i$ can take on any value in $L$, and $y_i$ can take on any value in $D$.
> - [ ] $x_i$ can take on any value in $L$, and $y_i$ can take on any value in $L$.
> - [ ] $x_i$ can take on any value in $D$, and $y_i$ can take on any value in $D$.

> [!answer]- Spoilers
> $x_i$ can take on any value in $D$, and $y_i$ can take on any value in $L$.

> [!question]- Part 5.
> Let $I(x_0)$ denote the constraint that $x_0$ is the initial state of the game and $F(x_k)$ denote the constraint that $x_k$ is the final state of the game.
> 
> What are the values that $x_0$ and $x_k$ can take on if they have to satisfy these constraints?
> 
> - [ ] $x_0 = \emptyset$ and $x_k = S_0$.
> - [ ] $x_0 = S_0$ and $x_k = L$.
> - [ ] $x_0 = S_0$ and $x_k = \emptyset$.
> - [ ] $x_0 = L$ and $x_k = S_0$.

> [!answer]- Spoilers
> $x_0 = S_0$ and $x_k = \emptyset$.

> [!question]- Part 6.
> We now want a constraint $R(x_a, y, x_b)$ that ensures that poking location $y$ in state $x_a$ results in state $x_b$. The constraint table for $R$ consists of all triplets $(\alpha,\beta,\gamma)$ where $\alpha$ and $\gamma$ are elements of the domains of $x_a$ and $x_b$ respectively, and $\beta$ is an element of the domain of $y$ that represent valid transitions. Which of the following are valid triplets?
> 
> - [ ] $(\emptyset, (1,1), \emptyset)$
> - [ ] $(\emptyset, (1,1), \{(1,1),(1,2),(2,1)\})$
> - [ ] $(\{(1,1),(1,2)\}, (1,1), \{(1,1),(1,2)\})$
> - [ ] $(\{(1,1),(1,2)\}, (1,1), \emptyset)$
> - [ ] $(\{(1,2),(2,1),(2,2)\}, (2,2), \emptyset)$
> - [ ] $(\{(1,2),(2,1),(2,2)\}, (2,2), (1,1))$

> [!answer]- Spoilers
> The correct answers:
> - [x] $(\emptyset, (1,1), \{(1,1),(1,2),(2,1)\})$
> - [x] $(\{(1,2),(2,1),(2,2)\}, (2,2), \emptyset)$

> [!question]- Part 7.
> Note that the constraint table of $R(x_a, y, x_b)$ is a list of all satisfying assignments to the variables $x_a, y, x_b$. How many triplets does this constraint table have?

> [!answer]- Spoilers
> 64

> [!question]- Part 8.
> Recall that we wanted to design a CSP that describes the following: poking the locations $p_1 \rightarrow p_2 \rightarrow \cdots \rightarrow p_k$ turns the state $S_0$ to the state $S_\emptyset$, where $S_0 \subseteq L$ is a given initial state, and $S_\emptyset$ is the state where all locations are dead. Which of the following is such a CSP?
> 
> - [ ] $\left(I(x_0) \land F(x_k)\right) \bigwedge \left(\bigwedge_{i=1}^{k} R(x_{i}, y_i, x_{i+1})\right)$
> - [ ] $\left(I(x_0) \land F(x_k)\right) \bigwedge \left(\bigwedge_{i=1}^{k} R(x_{i-1}, y_i, x_i)\right)$
> - [ ] $\left(I(y_1) \land F(y_k)\right) \bigwedge \left(\bigwedge_{i=1}^{k} R(x_{i}, y_i, x_{i+1})\right)$
> - [ ] $\left(I(y_1) \land F(y_k)\right) \bigwedge \left(\bigwedge_{i=1}^{k} R(x_{i-1}, y_i, x_i)\right)$

> [!answer]- Spoilers
> $\left(I(x_0) \land F(x_k)\right) \bigwedge \left(\bigwedge_{i=1}^{k} R(x_{i-1}, y_i, x_i)\right)$

> [!question]- Part 9.
> You have developed a CSP that can validate if there is a solution to a given initial state $S_0$ that uses $k$ steps. Observe that you can use this CSP to check if the initial state has a solution at all, by trying different values of $k$. Let $F(x_0,\ldots,x_k,y_1,\ldots,y_k)$ denote the formula you chose in the previous answer. Which of the following is a valid way to check if the initial state has a solution?
> 
> *Hint: consider your answers to the first two parts of this question.*
> 
> - [ ] $\bigvee_{k=0}^{k=4} \left(F(x_0,\ldots,x_k,y_1,\ldots,y_k)\right)$
> - [ ] $\bigvee_{k=0}^{k=8} \left(F(x_0,\ldots,x_k,y_1,\ldots,y_k)\right)$
> - [ ] $\bigvee_{k=0}^{k=16} \left(F(x_0,\ldots,x_k,y_1,\ldots,y_k)\right)$
> - [ ] $\bigvee_{k=0}^{k=65536} \left(F(x_0,\ldots,x_k,y_1,\ldots,y_k)\right)$
> - [ ] None of the above

> [!answer]- Spoilers
> The correct answer(s):
> - [x] $\bigvee_{k=0}^{k=4} \left(F(x_0,\ldots,x_k,y_1,\ldots,y_k)\right)$
> - [x] $\bigvee_{k=0}^{k=8} \left(F(x_0,\ldots,x_k,y_1,\ldots,y_k)\right)$
> - [x] $\bigvee_{k=0}^{k=16} \left(F(x_0,\ldots,x_k,y_1,\ldots,y_k)\right)$
> - [x] $\bigvee_{k=0}^{k=65536} \left(F(x_0,\ldots,x_k,y_1,\ldots,y_k)\right)$

---
{"dg-publish":true,"permalink":"/exercises/short-answer/0026-dr-nim-game-tree/"}
---

> [!question]- Dr Nim Game Tree
> 
> _Dr. Nim_ is a two-player turn based game that starts with $N$ marbles. On their turn, a player can remove 1,2, or 3 marbles. The player who has no marbles left on their turn loses.
  >
> The game tree of Dr. Nim is given below, with the root node describing the state with 5 marbles. The numbers in the boxes indicate the state of the game, which is fully determined by the number of marbles currently available.
> 
> Label this tree with utilities from the max player's perspective. At the leaves (nodes labeled $0$), the utility is $1$ if it is the min player's turn, and $-1$ if it is the max player's turn. What is the utility at the root?  
> 
> ![0026.png](/img/user/Exercises/Short-Answer/figures/0026.png)
>
> >[!bug]+ Evaluation Note
> > You get one point for a fully correct labeling, and one point for the final answer.

> [!answer]- Spoilers
> The final utility is +1. 
> And indeed, the max player has a win by removing just one marble.
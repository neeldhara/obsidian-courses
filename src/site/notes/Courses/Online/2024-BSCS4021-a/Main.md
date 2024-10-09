---
{"dg-publish":true,"dg-path":"2024-IITM-AA1","permalink":"/2024-iitm-aa-1/","hide":true}
---


_Course Duration:_ **May Term** in [the program](https://study.iitm.ac.in/ds/academics.html#AC2).


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/descriptions/bscs-4021/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




> [!NOTE]- About the Course
> When we think about designing algorithms, we are usually very demanding in how we go about it: we require our algorithms to be fast and accurate on all conceivable inputs. This is asking for quite a bit, and perhaps it is not surprising that we cannot afford this luxury all the time. The good news is that most of the time we can make meaningful progress by relaxing just one of these demands:
> 
> 1. _Give up on accuracy, but not completely._ Look for solutions that are good enough (approximation) and/or work with algorithms that report the right solution most of the time (Las-Vegas style randomization).
> 
> 2. _Give up on coverage, a little bit._ Let your algorithms work well on structured inputs. Hopefully the structure is such that it is not too limiting and is interesting enough for some application scenario, and is also enough to give you algorithmic leverage, i.e, there’s enough that you can exploit to make fast and accurate algorithms.
> 
> 3. _Give up on speed, to some extent._ Going beyond the traditional allowance of polynomial time, which is the holy grail of what is considered efficient, takes you places. You could either allow for your algorithms have super-polynomial running times, and optimize as much as possible while being accurate on all inputs (exact algorithms), or allow for bad running times on a bounded subset of instances (Monte-Carlo style randomization).
> 
> One potentially unifying approach that tackles all of these tradeoffs at once is to take what is now called a “multivariate approach” to the analysis of running times, which essentially involves appreciating that to describe a problem instance just in terms of its size is like describing a movie by a rating, which is unfortunate because there’s so much more nuance. And yet we report — and think about — worst-case running times in only terms of the sizes of the instances. In the multivariate approach, we allow for the running time to depend on multiple parameters of the input instance, and thinking about problems from a parameter-first perspective leads to a rich theory of algorithm design.
>
> In this course, we will explore some early glimpses all of these approaches in the context of a few fundamental algorithmic problems. We will also explore reductions between problems employed both with the goal of solving problems as well as demonstrating hardness.

> [!TLDR]- Target Audience
> Undergraduate students who have already done a basic data structures/algorithms course.

> [!Tip]- Pre-requisites
> A first course in (undergraduate level) data structures and algorithms, and discrete mathematics.

> [!reference]- References
> 
> 1. Cormen, Leiserson, Rivest, and Stein. Introduction to Algorithms. 2nd ed. Cambridge, MA: MIT Press, 2001.
> 2. Marek Cygan, Fedor V. Fomin, Lukasz Kowalik, Daniel Lokshtanov, Dániel Marx, Marcin Pilipczuk, Michal Pilipczuk, Saket Saurabh. [Parameterized Algorithms.](https://www.mimuw.edu.pl/~malcin/book/parameterized-algorithms.pdf) Springer-Verlag, 2015. 
> 3. David P. Williamson and David B. Shmoys, The Design of Approximation Algorithms
> 4. Daniel Lokshtanov, Meirav Zehavi, Saket Saurabh, Fedor V. Fomin. Kernelization: Theory of Parameterized Preprocessing. Cambridge University Press, 2019

> [!info]- Grading Policy
> The grading policy, applicable to all students pursuing this course for credit, is as per general IITM norms, which is typically the following:
> 
> 
> Total Course Score (T) = Average Quiz Score Q (out of 50) + End Term Score E (out of 50)
> A candidate is deemed to have passed a course IF Total Course Score (T) >= 50/100.

---



</div></div>


> [!calendar]- Registration & Evaluation Logistics
> 
> 1. Registration is through the IIT Madras online BS program platform.
> 2. Weekly assignments will be issued through the IITM portal, and are typically due within ~10 days of release.
> 3. Two quizzes will be conducted at the end of Weeks 4 and 8 based on the content of Weeks 1-4 and 1-8 respectively. These quizzes are invigilated. 
> 4. At the end of a term, there will be an end-term exam of 1.5 hours duration, which is invigilated as well.

---
#### Course Plan: 

_Note: the lecture videos and assignments for this course are made available through the IITM portal and are currently unavailable on this website, however, we hope to gradually release materials from the lectures, assignments and possibly the exams in due course._

| Week | Topic                                                          | Start Date        |
| ---- | :------------------------------------------------------------- | :---------------- |
| 1    | Greedy Algorithms                                              | 02 June 2023      |
| 2    | Matroids                                                       | 09 June 2023      |
| 3    | Dynamic Programming                                            | 16 June 2023      |
| 4    | Treewidth and DP over Tree Decompositions                      | 23 June 2023      |
| 5    | Reductions - I: Network Flows and ILP                          | 30 June 2023      |
| 6    | Reductions - II: NP-completeness and SAT                       | 07 July 2023      |
| 7    | Approximation Algorithms                                       | 14 July 2023      |
| 8    | Randomized Algorithms                                          | 21 July 2023      |
| 9    | Exact Algorithms                                               | 28 July 2023      |
| 10   | Parameterized Algorithms                                       | 04 August 2023    |
| 11   | Kernelization                                                  | 11 August 2023    |
| 12   | Reductions - III: Fine-grained hardness frameworks             | 18 August 2023    |


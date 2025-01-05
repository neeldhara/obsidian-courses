---
{"dg-publish":true,"dg-path":"2025-CS614","permalink":"/2025-cs-614/","hide":true}
---

## Advanced Algorithms
##### AY 2024-25, Sem II
_co-taught with Prof Manoj Gupta_

A link to the materials from the second half of the course will be shared here shortly.

---


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/descriptions/cs-614-v-a/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">





> [!NOTE]- About the Course
> Data structures give us principled ways to stow away information. It’s important to do this nicely: and what that means is to work backwards from what you want to _do_ with your information, so that your storage style is optimized for the specific way in which you need to work with your data.
>
> For example, the notes you might be taking in this class is a kind of information.
> 
> If you have no plans of revisiting them later, you can take them as you please, or better yet, not take them at all!
>
> However, you want your notes optimised for giving you quality company during a 2AM revision session on exam day, competing with Maggi for attention, you want your notes to be competently taken: they don’t have to be neat, and it’s enough for them to be useful.
>
> On the other hand, if you are taking notes so that a special someone who will inevitably miss a few classes will almost certainly ask for later, then you would be making notes to impress, and that potentially requires a different approach.
>
> Throughout this course, we will understand such trade-offs in several scenarios.
> 
> > [!NOTE]+ Topics
> > sequential data (arrays, dynamic arrays, linked lists and variants) • dequeues, stacks, queues • graph representations • graph traversals (BFS/DFS) and applications (connected components, bipartiteness, topological sort) • searching and sorting • heaps • BSTs • (2,3)-trees

> [!TLDR]- Target Audience
> This course is aimed at students interested in modern methods in the design and analysis of algorithms with a predominantly theoretical perspective. 

> [!Tip]- Pre-requisites
> We expect learners to be familiar with topics typically taught in an introductory discrete math course (especially graphs, discrete probability, and linear algebra), and elementary algorithm design techniques.

> [!reference]- References
> 1. [Open Data Structures](https://opendatastructures.org/) by Pat Morin
> 2. [Lecture notes](https://www.cs.bham.ac.uk/~jxb/DSA/dsa.pdf) by John Bullinaria
> 3. [Data Structures Using C & C++](https://www.amazon.in/Data-Structures-Using-C/dp/8131703282) by Aaron M. Tenebaum; Moshe J. Augenstein; Yedidyah Lansam
> 4. [Data Structures and Algorithms](https://www.amazon.in/Structures-Algorithms-Addison-Wesley-Computer-Information/dp/0201000237) by A. Aho, J. Hopcroft, J. Ullman
> 5. [Algorithms](http://jeffe.cs.illinois.edu/teaching/algorithms/) by Jeff Erickson

---



</div></div>


> [!calendar]+ Timings and Venue
> 
> Mondays and Thursdays, 11.30AM, 11/206

> [!info]- Registration & Evaluation Logistics
> 
> Please register as usual through IMS. This course will have materials posted to this website, but assessments will be managed through Gradescope and announcements will be made over Google Classroom.
> 
> All assessments will be processed through Gradescope, and will use the enrolment code **3RVXNG**. You will be able to add yourself as a student.
> 
> _New users:_ If you don’t have a Gradescope account yet, go to the Gradescope website, click Sign Up in the upper right corner, select Student, and put in your entry code in the sign-up form. Note that your instructor may choose to disable the entry code and not allow students to use entry codes to enroll. If the entry code doesn’t work, please email me for details on how to access the course.
> 
> _Existing users:_ If you already have a Gradescope account, log into that account and navigate to your Account Dashboard by clicking the Gradescope logo in the top left, and click Add Course in the bottom right corner. Then enter your course code. you will be able to add yourself as a student.
> 
> For announcements, please enroll on Google Classroom via [this link](https://classroom.google.com/c/NzQzMzk3MTE4Njc3?cjc=qrquvxi) or via code **qrquvxi**. 

> [!info]- Grading Policy
> 
> The first part of the course accounts for 50% of your total marks in the course. 
> 
> There will be 12 worksheets in this course, each associated with a lecture. Each worksheet is worth 5 points. Your total marks from worksheets will be capped at 40.
> 
> There will also be a mid-term exam worth 10 points. The format of the exam will be shared shortly.

---
#### Course Plan: 

| Lec # | Date   | Topic                                                                 | References | Slides |
| ----- | ------ | --------------------------------------------------------------------- | ---------- | ------ |
| 1     | 6 Jan  | Introduction to Approximation Algorithms<br>_Example: Load Balancing_ |            |        |
| 2     | 9 Jan  | Introduction to Linear Programming<br>_Example: Vertex Cover_         |            |        |
| 3     | 13 Jan | LP rounding<br>_Example: Bin Packing_                                 |            |        |
| NA    | 16 Jan | **Worksheet Discussion**                                              |            |        |
| 4     | 20 Jan | Randomized Rounding<br>_Example: Set Cover_                           |            |        |
| 5     | 23 Jan | Randomized Rounding<br>_Example: Multiway Cut_                        |            |        |
| 6     | 27 Jan | Primal-Dual Approximation<br>_Vertex Cover Again_                     |            |        |
| NA    | 30 Jan | **Worksheet Discussion**                                              |            |        |
| 7     | 3 Feb  | Primal-Dual Approximation<br>_Steiner Forest_                         |            |        |
| 8     | 6 Feb  | Primal-Dual Approximation<br>_Facility Location_                      |            |        |
| 9     | 10 Feb | Approximation Schemes<br>_Knapsack_                                   |            |        |
| NA    | 13 Feb | **Worksheet Discussion**                                              |            |        |
| 10    | 17 Feb | Approximation Schemes<br>_Traveling Salesman_                         |            |        |
| 11    | 20 Feb | Semi-Definite Programming<br>_Maximum Cut_                            |            |        |
| 12    | 24 Feb | Semi-Definite Programming<br>_Maximum Cut (contd)_                    |            |        |
| NA    | 27 Feb | **Worksheet Discussion**                                              |            |        |


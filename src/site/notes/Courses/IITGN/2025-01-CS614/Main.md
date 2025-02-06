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
> This course will be an exploration of approximation algorithms, focusing on techniques designed to find near-optimal solutions to computationally hard problems. Students will learn how to analyze the performance of these algorithms and apply them to various practical problems in computer science and operations research. This is one kind of _coping strategy_ for problems that are theoretically hard. See here for an overview of other algorithmic paradigms in this context.
> 
> We will introduce the approximation paradigm with a motivating example (Load Balancing). We will then focus on a numbe rof LP-based methods for various problems, including Vertex Cover, Set Cover, Facility Location, Steiner Forest, Multiway Cut, Bin Packing, and so on. After getting familiar with encoding problems as linear programs, we will learn about deterministic and randomized rounding methods for deriving approximate solutions efficiently. We will also learn about primal-dual based approximation algorithms. Finally, we will introduce approximation schemes (in the context of Knapsack) and SDP-based methods (for maximum cut).
> 
> _Problems:_ Load Balancing • Vertex Cover • Knapsack • Bin Packing • Set Cover • Multiway Cut • Steiner Forest • Facility Location • Traveling Salesman 
> 
> _Techniques_: LP • SDP • Randomized Rounding • Primal-Dual • PTASes

> [!TLDR]+ Target Audience
> This course is aimed at students interested in modern methods in the design and analysis of algorithms with a predominantly theoretical perspective. 

> [!Tip]+ Pre-requisites
> We expect learners to be familiar with topics typically taught in an introductory discrete math course (especially graphs, discrete probability, and linear algebra), and elementary algorithm design techniques.

> [!reference]+ References
> 
> 1. [The Design of Approximation Algorithms](https://www.designofapproxalgs.com/book.pdf) by David P. Williamson and David B.Shmoys
> 2. [Approximation Algorithms](https://athena.nitc.ac.in/~kmurali/Courses/CombAlg2014/vazirani.pdf) by Vijay V Vazirani

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
> _New users:_ If you don’t have a Gradescope account yet, go to the Gradescope website, click Sign Up in the upper right corner, select Student, and put in your entry code in the sign-up form. If the entry code doesn’t work, please email me for details on how to access the course.
> 
> _Existing users:_ If you already have a Gradescope account, log into that account and navigate to your Account Dashboard by clicking the Gradescope logo in the top left, and click Add Course in the bottom right corner. Then enter your course code. you will be able to add yourself as a student.
> 
> For announcements, please enroll on Google Classroom via [this link](https://classroom.google.com/c/NzQzMzk3MTE4Njc3?cjc=qrquvxi) or via code **qrquvxi**. 

> [!info]- Grading Policy
> 
> The first part of the course accounts for 50% of your total marks in the course. 
> 
> There will be 12 worksheets in this course, each associated with a lecture. Each worksheet will be released at 7PM on the day of the lecture (on Gradescope), and will be due within 24 hours, i.e, 7PM on the next day. Exceptions may be made for circumstances that are beyond your control, please email me if you need an extension.
> 
> Each worksheet is worth 5 marks. Your total marks from worksheets will be scaled to 40% of your total marks (note that this is not capping: for example, if you score `30/60` from the worksheets, your total marks will be `20/40`, and your final score from the worksheets will be `40/40` if and only if you earn a total of `60` points across all worksheets).
> 
> There will also be a mid-term exam worth 10 points. The format of the exam will be shared shortly.

---
#### Course Plan: 

| Lec # | Date   | Topic                                                                                                                 | Slides                                                                                                                     | Lecture                                                                                          |
| ----- | ------ | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| 1     | 6 Jan  | Introduction to Approximation Algorithms<br>_Example: Load Balancing_                                                 | [PDF](https://www.dropbox.com/scl/fi/e0whsgsw6rfiwkrc47q63/slides-load-balancing.pdf?rlkey=sz0p3henbxxdo7mjv1opojfd2&dl=0) | [YT](https://youtube.com/live/t0NNDCL6HFw)                                                       |
| 2     | 9 Jan  | Introduction to Linear Programming<br>_Example: Vertex Cover_                                                         | [PDF](https://www.dropbox.com/s/tnes3v2319sdc65/slides-lp-intro-vertex-cover.pdf?dl=0)                                     | [YT](https://www.youtube.com/live/E9eILR944no)^[Sorry about choppy audio!]                       |
| 3     | 13 Jan | Adaptive rounding <br>_Example: Bin Packing_                                                                          | [PDF](https://www.dropbox.com/s/luaig62u5v95u35/slides-bin-packing.pdf?dl=0)                                               | [Part 1](https://youtube.com/live/eYmvsNsOY7Q)<br>[Part 2](https://youtube.com/live/iNsC49vkLWI) |
| NA    | 16 Jan | **Worksheet Discussion**<br>_Remark: we spent most of this class concluding <br>our discussion of adaptive rounding._ |                                                                                                                            |                                                                                                  |
| 4     | 20 Jan | Randomized Rounding<br>_Example: Set Cover_                                                                           | [PDF](https://www.dropbox.com/scl/fi/wgan6f2f9w2bztr5mpz3e/slides-set-cover.pdf?rlkey=wdush8lpgd7srww08381keiot&dl=0)      | [YT](https://youtube.com/live/SUNxfFF7Yi0`)                                                      |
| 5     | 23 Jan | General Techniques<br>_Multiway Cut via Isolating Cuts_                                                               | [PDF](https://www.dropbox.com/s/e3b6w689ibzjniq/slides-multiway-cut.pdf?dl=0)                                              | NA                                                                                               |
| 6     | 27 Jan | Randomized Rounding<br>_Multiway Cut_                                                                                 | (same)                                                                                                                     | NA                                                                                               |
| NA    | 30 Jan | **Worksheet Discussion**<br>_Remark: we spent most of this class concluding <br>our discussion of multiway cut._      |                                                                                                                            |                                                                                                  |
| 7     | 3 Feb  | Primal-Dual Approximation<br>_Vertex Cover_                                                                           | PDF                                                                                                                        | NA                                                                                               |
| NA    | 6 Feb  | _Remark: this class is canceled._                                                                                     |                                                                                                                            |                                                                                                  |
| 8     | 10 Feb | Primal-Dual Approximation<br>_Steiner Forest_                                                                         |                                                                                                                            |                                                                                                  |
| 9     | 13 Feb | Primal-Dual Approximation<br>_Facility Location_                                                                      |                                                                                                                            |                                                                                                  |
| NA    | 17 Feb | **Worksheet Discussion**                                                                                              |                                                                                                                            |                                                                                                  |
| 10    | 20 Feb | Approximation Schemes<br>_Knapsack_                                                                                   |                                                                                                                            |                                                                                                  |
| 11    | 24 Feb | Approximation Schemes<br>_Traveling Salesman_                                                                         |                                                                                                                            |                                                                                                  |
| 12    | 27 Feb | Semi-Definite Programming<br>_Maximum Cut_                                                                            |                                                                                                                            |                                                                                                  |

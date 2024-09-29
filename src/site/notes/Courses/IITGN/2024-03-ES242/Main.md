---
{"dg-publish":true,"dg-path":"2024-es242","permalink":"/2024-es242/","hide":true}
---


## Data Structures and Algorithms - I
---


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/descriptions/es-242/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




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
> This course is aimed at undergraduates in their first or second year, as a first introduction to data structures and algorithms.

> [!Tip]- Pre-requisites
> The course is largely self-contained. Working familiarity with a programming language will be useful for the labs, where solutions are expected to be written out in C.

> [!reference]- References
> 1. [Open Data Structures](https://opendatastructures.org/) by Pat Morin
> 2. [Lecture notes](https://www.cs.bham.ac.uk/~jxb/DSA/dsa.pdf) by John Bullinaria
> 3. [Data Structures Using C & C++](https://www.amazon.in/Data-Structures-Using-C/dp/8131703282) by Aaron M. Tenebaum; Moshe J. Augenstein; Yedidyah Lansam
> 4. [Data Structures and Algorithms](https://www.amazon.in/Structures-Algorithms-Addison-Wesley-Computer-Information/dp/0201000237) by A. Aho, J. Hopcroft, J. Ullman
> 5. [Algorithms](http://jeffe.cs.illinois.edu/teaching/algorithms/) by Jeff Erickson

---



</div></div>


> [!calendar]- Timings and Venue
> 
> Classes: Tuesdays and Thursdays · 5PM · 10/103
> Labs: Wednesdays · 11.30AM · Jasubhai Auditorium
> Office Hours: by appointment

> [!info]- Registration & Evaluation Logistics
> 
>  ![Static Badge](https://img.shields.io/badge/-classroom-blue?logo=google&logoColor=white)
> The course is hosted on Google classroom (code `amsscja`).
> 
> Please join the classroom to be informed of announcements and to participate in weekly quizzes. These are typically short 15-minute quizzes held in-class, but are open (so you can look things up or discuss the problems). However, giving the quiz from outside the classroom **will be considered a violation of the honor code**.
> 
> Lab exams will be held in the labs and will be evaluated by TAs.
> The midsem and endsem exams will be held as per the institute schedule, and will be pen and paper exams with mostly objective-type questions and a small number of subjective questions. You are allowed to bring a cheat sheet or notebooks or books (within reason), but electronic devices are prohibited.

> [!info]- Grading Policy
> 
>
> - Lab Exams: 10 + 15
> - Midsem and Endsem: 10 + 20
> - In-class worksheets: 20 X 3 (capped at 40)
> - Viva: 5 (every candidate will have one interview on a Saturday afternoon)

---
#### Course Plan: Part I

Note: most relevant resources (slides, notes, pointers to references) to classroom instruction re linked to below. For materials related to the lab, please refer to the announcements posted to Google classroom.

| Date                 | Lecture Topic                                                                                                                                                                                                                                       | Slides & Notes                                                                                            | Remarks | Other References                                                                                                       |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------- |
| 06 Aug 2024<br>*Tue* | What we value and how we measure it<br>_Activity: Baby Hummer_                                                                                                                                                                                      | [Slides](https://slides.com/neeldhara/dsaslides-introduction) · [[Materials/DSA/Introduction\|Notes]]                   | No Quiz | NA                                                                                                                     |
| 08 Aug 2024<br>_Thu_ | Sequential Data Structures<br>& Introduction to Stable Marriage                                                                                                                                                                                     | [Slides](https://slides.com/neeldhara/sequential-data-structures) · [[Materials/DSA/Sequential Data Structures\|Notes]] | [[Courses/IITGN/2024-03-ES242/Q01\|Courses/IITGN/2024-03-ES242/Q01]] | NA                                                                                                                     |
| 13 Aug 2024<br>_Tue_ | Stable Marriage <br>([analysis](https://www.unipa.it/dipartimenti/matematicaeinformatica/.content/documenti/2018_Seminario_Erasmus_Lecture_Stable_Marriage_Problem.pdf) and [interactive essay](https://uw-cse442-wi20.github.io/FP-cs-algorithm/)) | [Slides](https://slides.com/neeldhara/stable-matchings) · [[Materials/DSA/Stable Matchings\|Notes]]                     | [[Courses/IITGN/2024-03-ES242/Q02\|Q02]] | [Implementation](https://cse.buffalo.edu/faculty/atri/courses/331/fall14/handouts/GS-details.pdf)                      |
| 20 Aug 2024<br>_Tue_ | Lists and Arrays<br>(examples and trade-offs)                                                                                                                                                                                                       | *contd.*                                                                                                  | [[Courses/IITGN/2024-03-ES242/Q03\|Q03]] | [visualgo (arrays)](https://visualgo.net/en/array?slide=1)<br>[visualgo (lists)](https://visualgo.net/en/list?slide=1) |
| 22 Aug 2024<br>_Thu_ | Introduction to Graphs<br>_Activity: [Contagions](https://slides.com/neeldhara/stable-matchings/edit)_ by [Nicky Case](https://ncase.me)                                                                                                            | [Slides](https://slides.com/neeldhara/graphs) · [[Materials/DSA/Graphs\|Notes]]                                         | No Quiz | [Book Chapter](https://jeffe.cs.illinois.edu/teaching/algorithms/book/05-graphs.pdf)                                   |
| 23 Aug 2024<br>_Fri_ | Properties of Graphs<br>(definitions and examples)                                                                                                                                                                                                  | *contd.*                                                                                                  | [[Courses/IITGN/2024-03-ES242/Q04\|Q04]] | NA                                                                                                                     |
| 27 Aug 2024<br>_Tue_ | Graph Representations<br>(examples and trade-offs)                                                                                                                                                                                                  | *contd.*                                                                                                  | [[Courses/IITGN/2024-03-ES242/Q05\|Q05]] | NA                                                                                                                     |
| 29 Aug 2024<br>_Thu_ | An Introduction to Euler Tours<br>_Activity: [bridges on Mathigon](https://mathigon.org/course/graph-theory/bridges)_                                                                                                                               | [Slides](https://slides.com/neeldhara/euler-tours) · [[Materials/DSA/Euler Tours\|Notes]]                               | [[Courses/IITGN/2024-03-ES242/Q06\|Q06]] | NA                                                                                                                     |
| 03 Sep 2024<br>_Tue_ | More on Euler Tours<br>(algorithm for finding Euler Tours)                                                                                                                                                                                          | *contd.*                                                                                                  | [[Courses/IITGN/2024-03-ES242/Q07\|Q07]] | [Video](https://www.youtube.com/watch?v=8MpoO2zA2l4)                                                                   |
| 10 Sep 2024<br>_Tue_ | Finding De Bruijn Sequences<br>_Activity: The 5-Card Reveal_                                                                                                                                                                                        | [Slides](https://slides.com/neeldhara/de-bruijn) · [[Materials/DSA/De Bruijn Sequences\|Notes]]                         | [[Courses/IITGN/2024-03-ES242/Q08\|Q08]] | NA                                                                                                                     |
| 12 Sep 2024<br>_Thu_ | Introduction to Traversals<br>_Activity: friends in class_                                                                                                                                                                                          | [[Materials/DSA/Traversals\|Notes]]                                                                                     | No Quiz | [visualgo](https://visualgo.net/en/dfsbfs?slide=1)                                                                     |
| 17 Sep 2024<br>_Tue_ | Breadth First Search<br>Distance Properties + Bipartite                                                                                                                                                                                             | *contd.*                                                                                                  | [[Courses/IITGN/2024-03-ES242/Q09\|Q09]] | [Video](https://www.youtube.com/watch?v=oDqjPvD54Ss&list=PLDV1Zeh2NRsDGO4--qE8yH72HFL1Km93P&index=6)                   |
| 19 Sep 2024<br>_Thu_ | Guest Lecture<br>by _John Azariah_                                                                                                                                                                                                                  | TBA                                                                                                       | [[Courses/IITGN/2024-03-ES242/Q10\|Q10]] | NA                                                                                                                     |
| 24 Sep 2024<br>_Tue_ | Depth First Search<br>Intuitive Implementation                                                                                                                                                                                                      | [Slides](https://slides.com/neeldhara/dfs)                                                                | No Quiz | [Video](https://www.youtube.com/watch?v=7fujbpJ0LB4&list=PLDV1Zeh2NRsDGO4--qE8yH72HFL1Km93P&index=5)                   |
| 26 Sep 2024<br>_Thu_ | Depth First Search<br>pre/post notions & types of edges                                                                                                                                                                                             | *contd.*                                                                                                  | No Quiz | [Book Chapter](https://jeffe.cs.illinois.edu/teaching/algorithms/book/06-dfs.pdf)                                      |

---

Note: the class on 5th September was canceled. 

#### Course Plan: Part II

TBA.


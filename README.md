
**[Avisha Dhisle](https://www.linkedin.com/in/avisha-dhisle/)** (adhisle) and **[Prerit Rodney](https://www.linkedin.com/in/preritrodney/)** (prodney)

<style>a.nav { color: #585858; border-radius: 5px; background: #E6E6E6; padding: .2em .7em; text-decoration: none; margin: .5em .5em; display:inline-block; }a.nav:hover { background: #D8D8D8; color: black;}a.nav.selected { background: #D8D8D8; font-weight: bold; }small{color: #5e5e5e; display:block;text-align:center;margin-bottom: 1em;}</style>
<div style="text-align: center;">
<a class="nav" href="https://millenniumfalcon418.github.io/hyperdrive/proposal" >Proposal</a>
<a class="nav"  href="https://millenniumfalcon418.github.io/hyperdrive/checkpoint">Checkpoint Report</a>
<a class="nav"  href="https://millenniumfalcon418.github.io/hyperdrive/final_report">Final Report</a>
<a class="nav" href="https://millenniumfalcon418.github.io/hyperdrive/Hyperdrive" >Presentation</a></div>

## OVERVIEW
Quite often in numerical analysis, the solution to partial differential equations, non-linear systems and optimization problems leads to a system of linear equations. From economic models to large-scale and complex network analysis, the solutions involve numerical computations on matrices that are sparse, dense or structured. Today, linear algebraic calculations on sparse matrices of the order of thousands of tens are trite. They are commonly used in circuit and physical simulations, computer vision, machine learning and various other graph-based applications.

When storing and manipulating sparse matrices on a computer, it is beneficial and often necessary to use specialized algorithms and data structures that take advantage of the sparse structure of the matrix. Operations using standard dense-matrix structures and algorithms are slow and inefficient when applied to large sparse matrices as processing and memory are wasted on the zeroes. Sparse data is by nature more easily compressed and thus require significantly less storage. Therefore, there are special algorithms and data structures that are used while dealing with such matrices. Here, we look at one such method called the conjugate gradient method for solving linear systems of sparse matrices.

### Conjugate Gradient Method
The conjugate gradient method is an algorithm for the numerical solution of particular systems of linear equations, namely those whose matrices are symmetric and positive-definite. The conjugate gradient algorithm is implemented as a direct method or an iterative method. 
With a direct method, there is a definite amount of work that needs to be done. To get a solution, the algorithm needs to run until the end. Typically, the solution you get will then be close to the exact one. With iterative methods, the old guess is updated in the hope that we get a bit closer to the true solution. This means that the amount of work to be done can be decided on how much accuracy is needed.

For our project we chose to parallelize the iterative Conjugate Gradient method with Preconditioning. More details in the Proposal, Checkpoint and Final Report Sections.

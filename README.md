
**[Avisha Dhisle](https://www.linkedin.com/in/avisha-dhisle/)** (adhisle) and **[Prerit Rodney](https://www.linkedin.com/in/preritrodney/)** (prodney)

<style>a.nav { color: #585858; border-radius: 5px; background: #E6E6E6; padding: .2em .7em; text-decoration: none; margin: .5em .5em; display:inline-block; }a.nav:hover { background: #D8D8D8; color: black;}a.nav.selected { background: #D8D8D8; font-weight: bold; }small{color: #5e5e5e; display:block;text-align:center;margin-bottom: 1em;}</style>
<div style="text-align: center;">
<a class="nav" href="https://millenniumfalcon418.github.io/hyperdrive/proposal" target="_blank">Proposal</a>
<a class="nav"  href="https://millenniumfalcon418.github.io/hyperdrive/checkpoint" target="_blank">Checkpoint Report</a></div>

## OVERVIEW
Quite often in numerical analysis, the solution to partial differential equations, non-linear systems and optimization problems leads to a system of linear equations. From economic models to large-scale and complex network analysis, the solutions involve numerical computations on matrices that are sparse, dense or structured. Today, linear algebraic calculations on sparse matrices of the order of thousands of tens are trite. They are commonly used in circuit and physical simulations, computer vision, machine learning and various other graph-based applications.

When storing and manipulating sparse matrices on a computer, it is beneficial and often necessary to use specialized algorithms and data structures that take advantage of the sparse structure of the matrix. Operations using standard dense-matrix structures and algorithms are slow and inefficient when applied to large sparse matrices as processing and memory are wasted on the zeroes. Sparse data is by nature more easily compressed and thus require significantly less storage. Therefore, there are special algorithms and data structures that are used while dealing with such matrices. Here, we look at one such method called the conjugate gradient method for solving sparse matrices of linear systems.

### Conjugate Gradient Method
The conjugate gradient method is an algorithm for the numerical solution of particular systems of linear equations, namely those whose matrices are symmetric and positive-definite. The conjugate gradient algorithm is implemented as a direct method or an iterative method. 
With a direct method, there is a definite amount of work that needs to be done. To get a solution, the algorithm needs to run until the end. Typically, the solution you get will then be close to the exact one. With iterative methods, the old guess is updated in the hope that we get a bit closer to the true solution. This means that the amount of work to be done can be decided on how accuracy is needed. 

## THE CHALLENGE
CG is known to converge to the exact solution in N steps for a matrix of size N, which can lead to a lot of computation time for matrices having a very high value of N, as so often happens with real world solutions. Therefore, to reduce this time, the algorithm would be required to stop its iterations much earlier and still obtain a very good approximation after much fewer than N steps.
To achieve this, a certain amount of preconditioning is required. An appropriate preconditioner that can produce the fastest convergence under the given code conditions needs to be selected.

Another challenge was be to prevent the code from being bandwidth-bound. For this, it will be essential to store the sparse matrix in a compressed format that does not take up much storage. Memory overhead increases largely with extremely huge matrices. Therefore, it is important to make efficient use of storage. Also, the compressed format should enable faster access to reduce element retrieval time.

## DELIVERABLES
### OUR ASPIRATIONS
We will attempt to use either the Jacobian preconditioner or the Symmetric Successive Over-Relaxation (SSOR) preconditioner. The use of a preconditioner can significantly help us converge faster, thereby reducing computation time.
An efficient structure to store the sparse matrix will be implemented, so as to avoid being bandwidth-limited.
A parallel implementation in CUDA and/or using OpenMP primitives will be targeted so as to achieve a significant speedup. Both the implementations will be compared against each other and the best possible implementation of the sequential code for analysis. The analysis will also contain a profiling of both the parallel methodologies so as to provide a quantitative comparison of the two.

### DEMO
For the demo, we will demonstrate a code that implements the conjugate-gradient algorithm with preconditioning and compressed storage format and plot graphs that analyze the speedup and overheads in each methodology. This can help provide a holistic view of which implementation can be better than the other at a particular value of N.

## RESOURCES
GHC machines with NVIDIA Geforce GTX 1080

## REFERENCES
1. https://en.wikipedia.org/wiki/Sparse_matrix#Solving_sparse_matrix_equations
2. https://en.wikipedia.org/wiki/Conjugate_gradient_method
3. https://www.sharcnet.ca/help/index.php/Solving_Systems_of_Sparse_Linear_Equations
4. http://www.idi.ntnu.no/~elster/tdt24/tdt24-f09/cg.pdf
5. http://people.sc.fsu.edu/~jburkardt/cpp_src/cg/cg.html
6. http://math.nist.gov/MatrixMarket/index.html
7. Michele Benzi, "Preconditioning Techniques for Large Linear Systems: A Survey," Journal of Computational Physics 182, 418–477 (2002)
8. https://www.cise.ufl.edu/research/sparse/matrices/
9. Jonathan Richard Shewchuk, "An Introduction to the Conjugate Gradient Method Without the Agonizing Pain" 


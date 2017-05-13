## THE CHALLENGE
1) Since the CG algorithm deals with large matrices, the problem can easily be bandwidth-bound. Hence, it was essential to store the sparse matrix in a compressed format that does not take up much storage and also enables faster access to reduce element retrieval time.

2) CG is known to converge to the exact solution in N steps for a good-conditioned matrix of size N, which can lead to a lot of computation time for matrices having a very high value of N. Therefore, to reduce this time, the algorithm would be required to stop its iterations much earlier and still obtain a very good approximation after much fewer than N steps. To achieve this, a certain amount of preconditioning is required. An appropriate preconditioner that can produce the fastest convergence under the given code conditions was selected.

3) The algorithm involved many operations like two matrix-vector products, scalar-vector products, etc., all of which are computationally intensive and hence require a lot of time in a single-threaded program.

## CAPABILITIES OF OUR CONJUGATE GRADIENT SOLVER
1) Provides a preconditioned sequential implementation of the CG solver
2) Includes a multithreaded implementation of the Preconditioned Conjugate Gradient (PCG) solver using OpenMP primitives
3) Presents a GPU implementation of the PCG using CUDA

## INPUT AND OUTPUT CONSTRAINTS
For the linear system Ax = b
### Input Constraints
Matrix A must be-
1) Symmetric
2) Positive definite
3) Banded, diagonally heavy
Matrix B must be a vector of size equal to order of A.
## Output Constraints
1) Solution x is computed as the result of the algorithm
2) L2 norm of the residual vector must be less than e-05 to declare convergence

## VISUAL REPRESENTATIONS OF TEST MATRICES USED

## OUR APPROACH
### Compressed Row Storage Format
In order to mitigate the bandwidth-bound problem, we stored the sparse matrices in the compressed row storage format. As per the CRS format, we used three 1-D arrays, such that one array stored only the non-zero elements, the second one stored their corresponding column numbers and the third one gave the row number as well as stored the number at which we index into the other two arrays to retrieve the required element.
We observed a reduction in memory storage of about 99.907% for our largest test matrix of size 90449.
<br>
<img src="https://millenniumfalcon418.github.io/hyperdrive/images/CRS.png"/>

### Jacobi Preconditioning
As mentioned before, for a good-conditioned matrix, the CG algorithm would converge in N steps. However, for a poor-conditioned matrix A, the same would take even more than N steps for convergence. As a result, preconditioning the matrix is crucial to performance.

Preconditioning is basically the application of a preconditioning matrix that conditions a problem so that its condition number is reduced. Condition number of a function with respect to an argument measures how much the output value X of the function can change for a small change in the input argument i.e. it gives a measure of the sensitivity of the function. The lower the condition number, the better is the preconditioning of the matrix and an ill-conditioned matrix has a high condition number.  Therefore, if the condition number is large, even a small error in b may cause a large error in x. On the other hand, if the condition number is small then the error in x will not be much bigger than the error in b.

We implemented three preconditioners, namely, the Symmetric Successive Over-Relaxation, Jacobi and Blocked Jacobi and studied them to obtain the best performing preconditioning. We observed that for our requirements of the matrices (diagonally heavy, banded) the Jacobi preconditioner gave convergence for the lowest number of iterations. Although SSOR is known to precondition the matrix better, our studies showed that it is a strongly serial code due to forward/backward propagations. Therefore, we preconditioned our matrix using the Jacobi preconditioner, since it required the least number of iterations and also had the most scope for parallelization.

### Multithreaded implementation using OpenMP

### GPU implementation

## GRAPHS AND ANALYSIS

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

For the 1806x1806 matrix,
| Sr. No.   |      Name      |  No.of iters |  Execution Time(s) |  Norm(temp,n) |  Norm(r,n) |
|:----------:|:-------------:|:------:|:------:|
|1	|Plain conjugate gradient	|16141|144.4692|9.67575e-09|0.00223618|
|2	|Plain Conjugate Gradient with OpenMP primitives	|16141|28.6728|9.67575e-09|0.00223618|
|3	|Conjugate Gradient with Jacobi Preconditioning	|520|9.17206|2.22108e-09|0.00284359|
|4	|Conjugate Gradient with Jacobi Preconditioning and OpenMP primitives	|520|1.92164|2.22108e-09|0.00284359|

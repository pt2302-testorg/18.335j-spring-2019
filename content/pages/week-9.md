---
content_type: page
description: This section covers Lectures 24-26.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Week 9
uid: 79b67382-5292-f6a0-b115-ef7aad0acfff
---
## Lecture 24: Sparse-Direct Solvers

### Summary

**Sparse-direct solvers:** For many problems, there is an intermediate between the dense Θ(m3) solvers of LAPACK and iterative algorithms: for a sparse matrix A, we can sometimes perform an LU or Cholesky factorization while maintaining sparsity, storing and computing only nonzero entries for vast savings in storage and work. In particular, did a MATLAB demo, a few experiments with a simple test case: the "discrete Laplacian" center-difference matrix on uniform grids that we've played with previously in this course. In 1d, this matrix is tridiagonal and LU/Cholesky factorization produces a bidiagonal matrix: Θ(m) storage and work! For a 2d grid, there are 4 off-diagonal elements, and showed how elimination introduces Θ(√m) nonzero entries in each column, or Θ(m3/2) nonzero entries in total. This is still not too bad, but we can do better. First, showed that this "fill-in" of the sparsity depends strongly on the ordering of the degrees of freedom: as an experiment, tried a *random* reordering, and found that we obtain Θ(m2) nonzero entries (~10% nonzero). Alternatively, one can find re-orderings that greatly reduce the fill-in. One key observation is that the fill-in only depends on the pattern of the matrix, which can be interpreted as a [graph](http://en.wikipedia.org/wiki/Graph_%28mathematics%29): m vertices, and edges for the nonzero entries of A (an [adjacency matrix](http://en.wikipedia.org/wiki/Adjacency_matrix) of the graph), and sparse-direct algorithms are closely related to graph-theory problems. For our simple 2d Laplacian, the graph is just the picture of the grid connecting the points. One simple algorithm is the [nested dissection](https://en.wikipedia.org/wiki/Nested_dissection) algorithm: recursively find a separator of the graph, then re-order the vertices to put the separator last. This reorders the matrix into a mostly block-diagonal form, with large blocks of zeros that are preserved by elimination, and if we do this recursively we greatly reduce the fill-in. Did a crude analysis of the fill-in structure, resulting in the time/space complexity on the last page of the handout, for our 2d grid where separators are obvious; for more general matrices finding separators is a hard and important problem in graph theory.

- Lecture 24 handout: {{% resource_link "bcd746dc-a8cb-f0d5-a890-f01a72d8ef64" "Sparse Matrix Algorithms (PDF)" %}} (Courtesy of Per-Olof Persson. Used with permission.)
- Lecture 24 notebook: [Sparse-Direct Solvers in Julia](http://nbviewer.jupyter.org/github/mitmath/18335/blob/spring19/notes/Nested-Dissection.ipynb)

### Further Reading

- [Nested Dissection: A Survey and Comparison of Various Nested Dissection Algorithms](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.58.9722) by Manpreet S. Khaira.
- [Direct Solvers for Sparse Matrices](http://www.cs.utk.edu/~dongarra/etemplates/node388.html) by Jack Dongarra.
- Davis, Timothy. *Direct Methods for Sparse Linear Systems*. SIAM: Society for Industrial and Applied Mathematics, 2006. ISBN: 9780898716139.

## Take-Home Midterm Exam

The exam is open notes and open book (including any material posted for the class: pset solutions and handouts). No other materials may be used (closed Internet).

It will cover everything in this course up to and including Lecture 20 and Pset 4.

{{< tableopen >}}{{< theadopen >}}{{< tropen >}}{{< thopen >}}
Midterm Exams
{{< thclose >}}{{< thopen >}}
Solutions
{{< thclose >}}{{< trclose >}}{{< theadclose >}}{{< tbodyopen >}}{{< tropen >}}{{< tdopen >}}
{{% resource_link "cd4c4e8f-10d0-1c21-8132-e5175cc246cb" "Spring 2019 Exam (PDF)" %}}
{{< tdclose >}}{{< tdopen >}}
{{% resource_link "c5965be4-1637-4a0e-73af-6191dc0ee5e7" "Spring 2019 Solutions (PDF)" %}}
{{< tdclose >}}{{< trclose >}}{{< tropen >}}{{< tdopen colspan="2" >}}
Midterm Exams and Solutions from Previous Years
{{< tdclose >}}{{< trclose >}}{{< tropen >}}{{< tdopen >}}
{{% resource_link "76c7450e-e3bd-88ec-160f-00b4f1998990" "Fall 2008 Exam (PDF)" %}}
{{< tdclose >}}{{< tdopen >}}
{{% resource_link "a3ff57be-1aa3-0fdd-eed5-830282ca74ca" "Fall 2008 Solutions (PDF)" %}}
{{< tdclose >}}{{< trclose >}}{{< tropen >}}{{< tdopen >}}
{{% resource_link "20a56c0b-fff5-40e7-b417-874251bcf327" "Fall 2009 Exam (PDF)" %}}
{{< tdclose >}}{{< tdopen >}}
\[No Solutions\]
{{< tdclose >}}{{< trclose >}}{{< tropen >}}{{< tdopen >}}
{{% resource_link "e016fea2-d146-129c-a018-f310660130c5" "Fall 2010 Exam (PDF)" %}}
{{< tdclose >}}{{< tdopen >}}
{{% resource_link "fcfa3b06-e876-cbfb-798b-5774aa6e870f" "Fall 2010 Solutions (PDF)" %}}
{{< tdclose >}}{{< trclose >}}{{< tropen >}}{{< tdopen >}}
{{% resource_link "bb00dd1d-b805-cb68-678d-a9c0d452f273" "Fall 2011 Exam (PDF)" %}}
{{< tdclose >}}{{< tdopen >}}
{{% resource_link "0b133489-e352-62fd-38a4-bb24a196ee0b" "Fall 2011 Solutions (PDF)" %}}
{{< tdclose >}}{{< trclose >}}{{< tropen >}}{{< tdopen >}}
{{% resource_link "b47966fd-23ef-6c1d-c7a2-032cbc9e6644" "Fall 2012 Exam (PDF)" %}}
{{< tdclose >}}{{< tdopen >}}
{{% resource_link "57ae7fa1-7a58-3481-f70f-6f15bd527b2c" "Fall 2012 Solutions (PDF)" %}}
{{< tdclose >}}{{< trclose >}}{{< tropen >}}{{< tdopen >}}
{{% resource_link "00d62118-648e-41e9-1201-664d982d4aed" "Fall 2013 Exam (PDF)" %}}
{{< tdclose >}}{{< tdopen >}}
{{% resource_link "0395a77e-d3f7-402c-2c0a-1028f5419710" "Fall 2013 Solutions (PDF)" %}}
{{< tdclose >}}{{< trclose >}}{{< tropen >}}{{< tdopen >}}
{{% resource_link "12e3a26f-4486-4ef0-1baf-4839119a2994" "Spring 2015 Exam (PDF)" %}}
{{< tdclose >}}{{< tdopen >}}
{{% resource_link "701f1458-203d-924d-48f9-029d909ecbda" "Spring 2015 Solutions (PDF)" %}}
{{< tdclose >}}{{< trclose >}}{{< tbodyclose >}}{{< tableclose >}}

## Lecture 25: Overview of Optimization Algorithms

### Summary

Several of the iterative algorithms so far have worked, conceptually at least, by turning the original linear-algebra problem into a minimization problem. It is natural to ask, then, whether we can use similar ideas to solve more general optimization problems, which will be the next major topic in this course.

Broad overview of optimization problems (see handout). The most general formulation is actually quite difficult to solve, so most algorithms (especially the most efficient algorithms) solve various special cases, and it is important to know what the key factors are that distinguish a particular problem. There is also something of an art to the problem formulation itself, e.g. a nondifferentiable minimax problem can be reformulated as a nicer differentiable problem with differentiable constraints.

CG easily generalizes to the [nonlinear conjugate gradient method](https://en.wikipedia.org/wiki/Nonlinear_conjugate_gradient_method) to (locally) minimize an *arbitrary* twice-differentiable f(x): the only changes are that r=-∇f is not simply b-Ax and that the successive line minimizations min f(x+αd) need to be done numerically (an “easy” 1d optimization problem). The key point being that, near a local minimum of a smooth function, the objective is typically roughly quadratic (via Taylor expansion), and when that happens CG greatly accelerates convergence. (Mentioned Polak–Ribiere heuristic to help "reset" the search direction to the gradient if we are far from the minimum and convergence has stalled; see the Hager survey below for many more.)

Outlined application of nonlinear CG to Hermitian eigenproblems by minimizing the Rayleigh quotient (this is convex, and furthermore we can use the Ritz vectors to shortcut both the conjugacy and the line minimization steps). The generalization of this is the [LOBPCG](http://en.wikipedia.org/wiki/LOBPCG) algorithm.

- Lecture 25 handout: {{% resource_link "b9aa5a39-48b1-d993-b8e6-2cff9fd1bdf2" "A Brief Overview of Optimization Problems (PDF)" %}}

### Further Reading

- Bertsekas, Dimitri P. *Nonlinear Programming*. Athena Scientific, 2016. ISBN: 9781886529052.
- Online book [*Convex Optimization*](http://web.stanford.edu/~boyd/cvxbook/) by Stephen Boyd and Lieven Vandenberghe.
- Conn, Andrew R. et al. *Introduction to Derivative-Free Optimization*. SIAM: Society for Industrial and Applied Mathematics, 2009. ISBN: 9780898716689.
- A useful review of topology-optimization methods can be found in [Topology Optimization Approaches](https://link.springer.com/article/10.1007/s00158-013-0978-6) by Ole Sigmund and Kurt Maute.
- There are many variants of nonlinear conjugate-gradient, mainly to avoid bad behavior far from the minimum, as surveyed by William Hager and Hongchao Zhang, [A Survey of Nonlinear Conjugate Gradient Methods (PDF)](http://people.cs.vt.edu/~asandu/Public/Qual2011/Optim/Hager_2006_CG-survey.pdf). *Pacific J. Optim.* 2, pp. 35-58 (2006).

## Lecture 26: Adjoint Methods

### Summary

Introduction to adjoint methods and the remarkable fact that one can compute the gradient of a complicated function with about the same number of additional operations as computing the function once. The adjoint method is a numerical method for efficiently computing the gradient of a function or operator in a numerical optimization problem. 

- Lecture 26 handout: {{% resource_link "35b30d8c-4896-f952-64ee-1b135fe031f2" "Adjoint Methods (PDF)" %}}

### Further Reading

- [Backpropagation](https://en.wikipedia.org/wiki/Backpropagation) on Wikipedia
- [Automatic Differentiation (AD)](https://en.wikipedia.org/wiki/Automatic_differentiation) on Wikipedia
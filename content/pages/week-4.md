---
content_type: page
description: This section covers Lectures 9-11.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Week 4
uid: 0b66ee6d-f323-1973-fa0b-b51b7f5d56aa
---
## Lecture 9: Solving the Normal Equations by QR and Gram-Schmidt

### Summary

Discussed solution of normal equations. Discussed condition number of solving normal equations directly, and noted that it squares the condition number—not a good idea if we can avoid it.

Introduced the alternative of QR factorization (finding an orthonormal basis for the column space of the matrix). Explained why, if we can do it accurately, this will give a good way to solve least-squares problems.

Gave the simple, but unstable, construction of the Gram-Schmidt algorithm, to find a QR factorization. Analyzed its O(mn{{< sup "2" >}}) complexity (specifically, 2mn{{< sup "2" >}} flops), and commented that the "same" projection qqᵀa requires O(m{{< sup "2" >}}) operations if you perform it as (qq{{< sup "T" >}})a but O(m) operations if you perform it as q(q{{< sup "T" >}}a) — matrix operations are associative (but not commutative), but where you put the parentheses can make a big difference in performance!

Discussed loss of orthogonality in classical Gram-Schmidt, using a simple example, especially in the case where the matrix has nearly dependent columns to begin with.

### Further Reading

- Read “Lectures 7, 8, 18, and 19” in the textbook *Numerical Linear Algebra*.
- {{% resource_link "be0cdadd-9de5-6ff8-d20d-9a0c6d6d9206" "Gram-Schmidt Orthogonalization (PDF)" %}} (Courtesy of Per-Olof Persson. Used with permission.)
- [Gram-Schmidt process](https://en.wikipedia.org/wiki/Gram%E2%80%93Schmidt_process) on Wikipedia.

## Lecture 10: Modified Gram-Schmidt and Householder QR

### Summary

Discussed loss of orthogonality in classical Gram-Schmidt, using a simple example, especially in the case where the matrix has nearly dependent columns to begin with. Showed modified Gram-Schmidt and argued how it (mostly) fixes the problem. Numerical examples (see notebook below).

Re-interpreted Gram-Schmidt in matrix form as Q = AR1R2…, i.e. as multiplying A on the right by a sequence of upper-triangular matrices to get Q. The problem is that these matrices R may be very badly conditioned, leading to an inaccurate Q and loss of orthogonality.

Instead of multiplying A on the right by R's to get Q, however, we can instead multiply A on the left by Q's to get R. This leads us to the Householder QR algorithm. Introduced Householder QR, emphasized the inherent stability properties of multiplying by a sequence of unitary matrices (as shown in Problem set 2). Showed how we can convert a matrix to upper-triangular form (superficially similar to Gaussian elimination) via unitary Householder reflectors.

- Lecture 10 handout: {{% resource_link "24dd28c5-8f71-fa98-f333-597707ff8684" "Householder Reflectors and Givens Rotations (PDF)" %}} (Courtesy of Per-Olof Persson. Used with permission.)
- Lecture 10 notebook: [Classical vs. Modified Gram-Schmidt](http://nbviewer.jupyter.org/github/mitmath/18335/blob/spring19/notes/Gram-Schmidt.ipynb)

### Further Reading

- Read “Lectures 7, 8, 16, 18, and 19” in the textbook *Numerical Linear Algebra*. It turns out that modified GS is backwards stable in the sense that the product QR is close to A, i.e. the function f(A) = Q\*R is backwards stable in MGS; this is why solving systems with Q, R (appropriately used as discussed in Trefethen Lecture 19) is an accurate approximation to solving them with A.
- For a review of the literature on backwards-stability proofs of MGS, see Paige, Christopher C., Miroslav Rozlozník, and Zdenvek Strakos "[Modified Gram-Schmidt (MGS), Least Squares, and Backward Stability of MGS-GMRES](https://epubs.siam.org/doi/10.1137/050630416)." *SIAM J. Matrix Anal. Appl.* 28, pp. 264–284.

## Lecture 11: Matrix Operations, Caches, and Blocking

### Summary

Finished Householder QR derivation, including the detail that one has a choice of Householder reflectors…we choose the sign to avoid taking differences of nearly-equal vectors. Gave flop count, showed that we don't need to explicitly compute Q if we store the Householder reflector vectors.

Counting arithmetic operation counts is no longer enough. Illustrate this with some performance experiments on a much simpler problem, matrix multiplication (see handouts). This leads us to analyze memory-access efficiency and caches and points the way to restructuring many algorithms.

Outline of the memory hierarchy: CPU, registers, L1/L2 cache, main memory, and presented simple 2-level ideal-cache model that we can analyze to get the basic ideas.

Analyzed cache complexity of simple row-column matrix multiply, showed that it asymptotically gets no benefit from the cache. Presented blocked algorithm, and showed that it achieves optimal Θ(n³/√Z) cache complexity.

Discussed some practical difficulties of the blocked matrix multiplication: algorithm depends on cache-size Z, and multi-level memories require multi-level blocking. Discussed how these ideas are applied to the design of modern linear-algebra libraries (LAPACK) by building them out of block operations (performed by an optimized BLAS).

- Lecture 11 handout: {{% resource_link "90a515a9-caf1-cbbe-7065-48d90e659d5a" "Performance Experiments with Matrix Multiplication (PDF)" %}}
- {{% resource_link "36335ea8-264f-bf78-790a-08b710fdf280" "Ideal-Cache Terminology (PDF)" %}}

### Assignment

- {{% resource_link "d7797a57-5cf3-9e9b-be5f-68b3595190a4" "Problem set 3 (PDF)" %}}
- {{% resource_link "2340346a-23cf-b535-2794-9b2b8c15f2f2" "Problem set 3 solutions (PDF)" %}}

### Further Reading

- Wikipedia has a reasonable introduction to "[Locality of Reference](http://en.wikipedia.org/wiki/Locality_of_reference)" that you might find useful.
- The optimized matrix multiplication shown on the handouts is called "[Automatically Tuned Linear Algebra Software (ATLAS)](http://math-atlas.sourceforge.net/)."
- "[Cache-Oblivious Algorithms](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.34.7911)" describes ideal cache model and analysis for various algorithms.
- "[MATLAB Incorporates LAPACK](https://www.mathworks.com/company/newsletters/articles/matlab-incorporates-lapack.html)" is about the switch from LINPACK to LAPACK/BLAS in MATLAB.
- The lecture video "[Cache-Efficient Algorithms](/courses/6-172-performance-engineering-of-software-systems-fall-2018/pages/lecture-videos/lecture-14-caching-and-cache-efficient-algorithms)" in [*6.172 Performance Engineering of Software Systems*](/courses/6-172-performance-engineering-of-software-systems-fall-2018) include discussions of matrix multiplication.
---
content_type: page
description: This section covers Lectures 3-5.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Week 2
uid: e81728f3-82ce-c39a-1a67-9d027dc38ee9
---
## Lecture 3: Floating-Point Summation and Backwards Stability

### Summary

Analyzed the accumulated floating-point roundoff errors (see handouts below), explaining the results that we observed experimentally in the Julia notebook of the previous lecture. In those experiments, all of the inputs were non-negative, so that the "condition number" factor in the derivation equalled 1. In general, though, if you have *cancellations* between summands of opposite signs, the same analysis shows that the relative error of the output can be arbitrarily large.

**Stability:** Gave the obvious definition of accuracy, what we might call "forwards stability" = almost the right answer for the right input. Showed that this is often too strong; e.g. adding a sequence of numbers is not forwards stable. (Basically because the denominator in the relative forwards error, which is the exact sum, can be made arbitrarily small via cancellations.)

Define asymptotic notation O(ε): *f*(ε) is O(*g*(ε)) if there exist some constants C, ε{{< sub "0" >}} > 0 such that |*f*(ε)| \< C|*g*(ε)| for all |ε|\<ε\\(\_0\\). That is, *g*(ε) is an asymptotic *upper bound* for *f*(ε) as ε goes to zero, ignoring constant factors C. (A similar notation is used in computational complexity theory, but in the limit of large arguments *n*.) In the definitions of stability, we technically require [uniform convergence](https://en.wikipedia.org/wiki/Uniform_convergence): we must have O(ε) errors with the same constants C and ε\\(\_0\\) independent of the inputs *x*. (The constants can depend on the dimension of *x*, however.)

More generally, we apply a weaker condition: "stability" = almost the right answer for almost the right input.

Often, it is sufficient to prove "backwards stability" = right answer for almost the right input. Showed that, in our example of adding a sequence of numbers, backwards stability seems to work where forwards stability failed. Then more rigorously proved that floating-point summation of *n* numbers is backwards stable.

- Lecture 3 handout 1: ![This resource may not render correctly in a screen reader.](https://old.ocw.mit.edu/images/inacessible.gif)[Notes on the Accuracy of Naive Summation (PDF)](https://old.ocw.mit.edu/courses/mathematics/18-335j-introduction-to-numerical-methods-spring-2019/week-2/MIT18_335JS19_lec3-1.pdf)
- Lecture 3 handout 2: ![This resource may not render correctly in a screen reader.](https://old.ocw.mit.edu/images/inacessible.gif)[Backwards Stability of Recursive Summation (PDF)](https://old.ocw.mit.edu/courses/mathematics/18-335j-introduction-to-numerical-methods-spring-2019/week-2/MIT18_335JS19_lec3-2.pdf)

### Further Reading

- [What Every Computer Scientist Should Know About Floating Point Arithmetic](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.22.6768) by David Goldberg.
- [How Java’s Floating-Point Hurts Everyone Everywhere (PDF)](http://www.cs.berkeley.edu/~wkahan/JAVAhurt.pdf) by William Kahan and Joseph Darcy. This article contains a nice discussion of floating-point myths and misconceptions.
- Read “Lectures 3 and 13–15” in the textbook *Numerical Linear Algebra*.
- Wikipedia article on "[Big O Notation](https://en.wikipedia.org/wiki/Big_O_notation)"; note that for expressions like O(ε) we are looking in the limit of small arguments rather than of large arguments (as in complexity theory), but otherwise the ideas are the same.

## Lecture 4: Norms on Vector Spaces

### Summary

When quantifying errors, a central concept is a norm, and we saw in our proof of backwards stability of summation that the choice of norm seems important. Defined norms (as in Lecture 3 of Trefethen): for a vector space *V*, a norm takes any *v* ∈ *V* and gives you a real number ‖*v*‖ satisfying three properties:

- Positive definite: ‖*v*‖ ≥ 0, and = 0 if and only if *v* = 0
- Scaling: ‖α*v*‖ = |α|⋅‖*v*‖ for any scalar α.
- [Triangle inequality](https://en.wikipedia.org/wiki/Triangle_inequality): ‖*v*+*w*‖ ≤ ‖*v*‖ + ‖*w*‖

There are many norms, for many different vector spaces. Gave examples of norms of column vectors: L\\(\_p\\) norms (usually \\(p\\) = 1, 2, or \\(\\infty\\)) and weighted L\\(\_2\\) norms. A complete (= continuous, essentially) normed vector space is called a [Banach space](https://en.wikipedia.org/wiki/Banach_space), and these error concepts generalize to *f*(*x*) when *f* and *x* are in any Banach spaces (including scalars, column vectors, matrices, …though infinite-dimensional Banach spaces are trickier).

Especially important in numerical analysis are functions where the inputs and/or outputs are matrices, and for these cases we need matrix norms. The most important matrix norms are those that are related to matrix operations. Started with the Frobenius norm. Related the Frobenius norm ‖*A*‖*F* to the square root of the sum of eigenvalues of *A*\**A*, which are called the *singular values* σ{{< sup "2" >}}; we will do much more on singular values later, but for now noted that they equal the squared eigenvalues of *A* if *A*\*=*A* (Hermitian). Also defined the induced matrix norm, and bounded it below by the maximum eigenvalue magnitude of *A* (if *A* is square). For the L{{< sub "2" >}} induced norm, related it (without proof for now) to the maximum singular value. A useful property of the induced norm is ‖*AB*‖ ≤ ‖*A*‖⋅‖*B*‖. Multiplication by a unitary matrix *Q* (*Q*\* = *Q*{{< sup "\-1" >}}) preserves both the Frobenius and L{{< sub "2" >}} induced norms.

**Equivalence of norms:** Described fact that any two norms are equivalent up to a constant bound, and showed that this means that stability in one norm implies stability in all norms. Sketched proof (*only skimmed this*): (i) show we can reduce the problem to proving any norm is equivalent to e.g. L{{< sub "1" >}} on (ii) the unit circle; (iii) show any norm is continuous; and (ii) use a result from real analysis: a continuous function on a closed/bounded (compact) set achieves its maximum and minimum, the [extreme value theorem](http://en.wikipedia.org/wiki/Extreme_value_theorem). See handout below.

- Lecture 4 handout: {{% resource_link "bcea0470-68e4-6ab8-7f39-8bdd4209c7f5" "Notes on the Equivalence of Norms (PDF)" %}}

### Further Reading

- Read “Lecture 3” in the textbook *Numerical Linear Algebra*.
- If you don't immediately recognize that A\*A has nonnegative real eigenvalues (it is positive semidefinite), now is a good time to review your linear algebra; see also “Lecture 24” in the textbook *Numerical Linear Algebra*.

## Lecture 5: Condition Numbers

### Summary

Related backwards error to forwards error, and backwards stability to forwards error (or "accuracy" as the book calls it). Show that, in the limit of high precision, the forwards error can be bounded by the backwards error multiplied by a quantity κ, the relative condition number. The nice thing about κ is that it involves only exact linear algebra and calculus, and is completely separate from considerations of floating-point roundoff. Showed that, for differentiable functions, κ can be written in terms of the induced norm of the Jacobian matrix.

Calculated condition number for square root, summation, and matrix-vector multiplication, as well as solving *Ax* = *b*, similar to the book. Defined the condition number of a matrix: for *f*(*x*) = *Ax*, the condition number is ‖*A*‖⋅‖*x*‖/‖*Ax*‖, which is bounded above by κ(*A*) = ‖*A*‖⋅‖*A*{{< sup "\-1" >}}‖.

Related matrix L{{< sub "2" >}} norm to eigenvalues of *B* = *A*\**A*. *B* is obviously Hermitian (*B*\* = *B*), and with a little more work showed that it is positive semidefinite: *x*\**Bx* ≥ 0 for any *x*. Reviewed and re-derived properties of eigenvalues and eigenvectors of Hermitian and positive-semidefinite matrices. Hermitian means that the eigenvalues are real, the eigenvectors are orthogonal (or can be chosen orthogonal). Also, a Hermitian matrix must be diagonalizable (I skipped the proof for this; we will prove it later in a more general setting). Positive semidefinite means that the eigenvalues are nonnegative.

Proved that, for a Hermitian matrix *B*, the Rayleigh quotient R(*x*) = *x*\**Bx*/*x*\*x is bounded above and below by the largest and smallest eigenvalues of *B* (the "min–max theorem"). Hence showed that the L{{< sub "2" >}} induced norm of *A* is the square root of the largest eigenvalue of *B* = *A*\**A*. Similarly, showed that the L{{< sub "2" >}} induced norm of *A*{{< sup "\-1" >}}, or more generally the supremum of ‖*x*‖/‖*Ax*‖, is equal to the square root of the inverse of the smallest eigenvalue of *A*\**A*.

Understanding norms and condition numbers of matrices therefore reduces to understanding the eigenvalues of *A*\**A* (or *AA*\*). However, looking at it this way is unsatisfactory for several reasons. First, we would like to solve one eigenproblem, not two. Second, working with things like *A*\**A* explicitly is often bad numerically, because it squares the condition number \[showed that κ(*A*\**A*) = κ(*A*){{< sup "2" >}}\] and hence exacerbates roundoff errors. Third, we would really like to get some better understanding of *A* itself. All of these concerns are addressed by the singular value decomposition or SVD, which we will derive next time.

### Assignment

- {{% resource_link "d858a0ae-21eb-a3ab-afcf-ef7f1b9843a8" "Problem set 2 (PDF)" %}}
- {{% resource_link "15cb5aa5-98e5-5798-893e-f4839a6e8309" "Problem set 2 solutions (PDF)" %}}

### Further Reading

- Read “Lectures 12, 14, 15, and 24” in the textbook *Numerical Linear Algebra*.
- Any linear-algebra textbook for a review of eigenvalue problems, especially Hermitian/real-symmetric ones.
- [Errors, Norms, and Condition Numbers](https://nbviewer.jupyter.org/github/stevengj/1806/blob/fall18/lectures/Conditioning.ipynb)
---
content_type: page
description: This section covers Lectures 18-20.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Week 7
uid: affe9479-9772-5585-db9a-db2649d56ea8
---
## Lecture 18: Krylov Methods and the Arnoldi Algorithm

### Summary

Gave simple example of power method, which we already learned. This, however, only keeps the most recent vector Anv and throws away the previous ones. Introduced Krylov subspaces, and the idea of Krylov subspace methods: find the best solution in the whole subspace 𝒦{{< sub "n" >}} spanned by {b,Ab,…,A{{< sup "n-1" >}}b}.

Presented the Arnoldi algorithm. Unlike the book, I start the derivation by viewing it as a modified Gram-Schmidt process, and prove that it is equivalent (in exact arithmetic) to GS on {b,b,Ab,A²b,…}, so it is an orthonormal basis for 𝒦{{< sub "n" >}}. Then we showed that this corresponds to partial Hessenberg factorization: AQ{{< sub "n" >}} = Q{{< sub "n" >}}H{{< sub "n" >}} + h{{< sub "(n+1)n" >}}q{{< sub "n+1" >}}e{{< sub "n" >}}ᵀ where H{{< sub "n" >}} is upper-Hessenberg.

Discussed what it means to find the "best" solution in the Krylov subspace 𝒦{{< sub "n" >}}. Discussed the general principle of Rayleigh-Ritz methods for approximately solving the eigenproblem in a subspace: finding the Ritz vectors/values (= eigenvector/value approximations) with a residual perpendicular to the subspace (a special case of a Galerkin method).

For Hermitian matrices A, I showed that the max/min Ritz values are the maximum/minimum of the Rayleigh quotient in the subspace, via the min-max theorem. In fact, in this case H{{< sub "n" >}} is Hermitian as well, so H{{< sub "n" >}} is tridiagonal and most of the dot products in the Arnoldi process are zero. Hence Arnoldi reduces to a three-term recurrence, and the Ritz matrix is tridiagonal. This is called the Lanczos algorithm.

Noted that n steps of Arnoldi requires Θ(mn²) operations and Θ(mn) storage. If we only care about the eigenvalues and not the eigenvectors, Lanczos requires Θ(mn) operations and Θ(m+n) storage. However, this is complicated by rounding problems that we will discuss in the next lecture.

### Further Reading

- Read “Lectures 31–34” in the textbook *Numerical Linear Algebra*.
- Online book [*Templates for the Solution of Linear Systems: Building Blocks for Iterative Methods*](http://www.netlib.org/linalg/html_templates/Templates.html) by Richard Barrett et al.
- Online book [*Templates for the Solution of Algebraic Eigenvalue Problems: A Practical Guide*](http://www.cs.utk.edu/~dongarra/etemplates/book.html) by Zhaojun Bai et al.

## Lecture 19: Arnoldi and Lanczos with Restarting

### Summary

Showed some computational examples (notebook above) of Arnoldi convergence. Discussed how rounding problems cause a loss of orthogonality in Lanczos, leading to "ghost" eigenvalues where extremal eigenvalues re-appear. In Arnoldi, we explicitly store and orthogonalize against all qj vectors, but then another problem arises: this becomes more and more expensive as n increases.

A solution to the loss of orthogonality in Lanczos and the growing computational effort in Arnoldi is restarting schemes, where we go for n steps and then restart with the k "best" eigenvectors. If we restart with k=1 *every* step, then we essentially have the power method, so while restarting makes the convergence worse the algorithm still converges, and converges significantly faster than the power method for k>1.

Explained why restarting properly is nontrivial for k>1: we need to restart in such a way that maintains the Arnoldi (or Lanczos) property AQ{{< sub "n" >}} = Q{{< sub "n" >}}H{{< sub "n" >}} + r{{< sub "n" >}}e{{< sub "n" >}}ᵀ where H{{< sub "n" >}} is upper-Hessenberg, r{{< sub "n" >}} is orthogonal to Q{{< sub "n" >}}, and e{{< sub "n" >}}ᵀ is only nonzero in the last column. In particular, showed that the "obvious" naive restarting algorithm using k Ritz vectors *almost* works, but messes up the e{{< sub "n" >}}ᵀ property. See the handout and notebook below.

- Lecture 19 handout: {{% resource_link "fa98fed4-3acb-3e23-11f6-d9328ca31d04" "Why Restarting Arnoldi/Lanczos is not Trivial (PDF)" %}}
- Lecture 19 notebook: [Experiments with Arnoldi Iterations](http://nbviewer.jupyter.org/github/mitmath/18335/blob/spring19/notes/Arnoldi.ipynb)

### Further Reading

- See the section on [Implicitly Restarted Lanczos Method](http://www.cs.utk.edu/~dongarra/etemplates/node117.html) in [*Templates for the Solution of Algebraic Eigenvalue Problems: A Practical Guide*](http://www.cs.utk.edu/~dongarra/etemplates/book.html) by Zhaojun Bai et al.

## Lecture 20: The GMRES Algorithm and Convergence of GMRES and Arnoldi

### Summary

Introduced the GMRES algorithm: compute the basis Q{{< sub "n" >}} for 𝒦{{< sub "n" >}} as in Arnoldi, but then minimize the residual ‖Ax-b‖{{< sub "2" >}} for x∈𝒦{{< sub "n" >}} using this basis. This yields a small (n+1)×n least-squares problem involving H{{< sub "n" >}}.

Discussed the convergence rate of GMRES and Arnoldi in terms of polynomial approximations. Following the book closely, showed that the relative errors (the residual norm ‖Ax-νx‖ or ‖Ax-b‖) can be bounded by minimizing the value p(λ) of a polynomial p(z) evaluated at the eigenvalues, where p has degree *n* after the *n*{{< sup "th" >}} iteration. In Arnoldi, the λ{{< sup "n" >}} coefficient of p(λ) is 1, whereas in GMRES the constant coefficient p(0)=1. (There is also a factor of the condition number of the eigenvector matrix in GMRES, so it is favorable for the eigenvectors to be near-orthogonal, i.e. for the matrix to be near-normal, see [normal matrix](http://en.wikipedia.org/wiki/Normal_matrix).)

Using this, we can see that the most favorable situation occurs when the eigenvalues are grouped into a small cluster, or perhaps a few small clusters, since we can then make p(λ) small with a low-degree polynomial that concentrates a few roots in each cluster. This means that Arnoldi/GMRES will achieve small errors in only a few iterations. Moreover we can see that a few outlying eigenvalues aren't a problem, since p(z) will quickly attain roots there and effectively eliminate those eigenvalues from the error—this quantifies the intuition that Krylov methods "improve the condition number" of the matrix as the iteration proceeds, which is why the condition-number bounds on the error are often pessimistic. Conversely, the worst case will be when the eigenvalues are all spread out uniformly in some sense. Following examples 35.1 and 35.2 in the book, you can actually have two matrices with very similar small condition numbers but very different GMRES convergence rates, if in one case the eigenvalues are clustered and in the other case the eigenvalues are spread out in a circle around the origin (i.e. with clustered magnitudes |λ| but different phase angles).

Contrasted convergence with Arnoldi/Lanczos. As in the book, showed that Arnoldi also minimizes a polynomial on the eigenvalues, except that in this case the coefficient of the *highest* degree term is constrained to be 1. (We proceeded somewhat backwards from the book: the book started with polynomial minimization and derived the Rayleigh-Ritz eigenproblem, whereas we went in the reverse direction.) Showed that this set of polynomials is shift-invariant, which explains why (as we saw experimentally) Arnoldi convergence is identical for A and A+μI. This is *not* true for GMRES, and hence GMRES convergence is not shift-invariant—this is not surprising, since solving Ax=b and (A+μI)x=b can be very different problems.

Like Arnoldi/Lanczos, if GMRES does not converge quickly we must generally restart it, usually with a subspace of dimension 1; restarting GMRES repeatedly after k steps is called GMRES(k). Unfortunately, unlike Arnoldi for the largest |λ|, restarted GMRES is *not guaranteed to converge*. If it doesn't converge, we must do something to speed up convergence: preconditioning (next time).

In many practical cases, unfortunately, the eigenvalues of A are *not* mostly clustered, so convergence of GMRES may be slow (and restarted GMRES may not converge at all). The solution to this problem is preconditioning: finding an easy-to-invert M such that M{{< sup "\-1" >}}A has clustered eigenvalues (and is not nearly defective).

### Assignment

- {{% resource_link "6bef264d-4a50-ec59-3caf-8b6a2acadcde" "Problem set 4 (PDF)" %}}
- {{% resource_link "dde57038-ba3a-6408-f0cc-90d23c511b4f" "Problem set 4 solutions (PDF)" %}}

### Further Reading

- Read “Lectures 34, 35, and 40” in the textbook *Numerical Linear Algebra*.
- The convergence of GMRES for very non-normal matrices is a complicated subject; see e.g. [The Convergence of Krylov Subspace Methods for Large Unsymmetric Linear Systems](http://citeseer.ist.psu.edu/viewdoc/summary?doi=10.1.1.48.1733) by Zhongxiao Jia.
- [Iterative methods for solving Ax=b, GMRES/FOM versus QMR/BiCG](http://link.springer.com/article/10.1007%2FBF02127693) (by Jane Cullum) reviews the relationship between GMRES and a similar algorithm called FOM that is more Galerkin-like (analogous to Rayleigh-Ritz rather than least-squares).
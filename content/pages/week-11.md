---
content_type: page
description: This section covers Lectures 29-31.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Week 11
uid: 29b83d59-c75d-f1e9-d0bc-358816146102
---
## Lecture 29: Lagrange Dual Problems

### Summary

Started by reviewing the basic idea of Lagrange multipliers to find an extremum of one function f\\(_0\\)(x) and one equality constraint h\\(_1\\)(x)=0. We instead find an extremum of L(x,ν\\(_1\\))=f\\(_0\\)(x)+ν\\(_1\\)h\\(_1\\)(x) over x and the *Lagrange multiplier* ν\\(_1\\). The ν\\(_1\\) partial derivative of L ensures h\\(_1\\)(x)=0, in which case L=f\\(_0\\) and the remaining derivatives extremize f\\(_0\\) along the constraint surface. Noted that ∇L=0 then enforces ∇f\\(_0\\)\=0 in the direction parallel to the constraint, whereas perpendicular to the constraint ν\\(_1\\) represents a "force" that prevents x from leaving the h\\(_1\\)(x)=0 constraint surface.

Generalized to the Lagrangian L(x,λ,ν) of the general optimization problem (the "primal" problem) with both inequality and equality constraints, following chapter 5 of the Boyd and Vandenberghe book (see below) (section 5.1.1).

Described the KKT conditions for a (local) optimum/extremum (Boyd, section 5.5.3). These are true in problems with strong duality, as pointed out by Boyd, but they are actually true in much more general conditions. For example, they hold under the "LICQ" condition in which the gradients of all the active constraints are linearly independents. Gave a simple graphical example to illustrate why violating LICQ requires a fairly weird optimum, at a cusp of two constraints.

Lecture 29 handout: [Lagrangian, Lagrange Dual Function and Dual Problem (PDF)](https://github.com/mitmath/18335/blob/spring19/notes/boyd-ch5-slides.pdf) in the online book [*Convex Optimization*](http://www.stanford.edu/~boyd/cvxbook/) by Stephen Boyd and Lieven Vandenberghe.

### Further Reading

- Chapter 5 in the online book [*Convex Optimization*](http://www.stanford.edu/~boyd/cvxbook/) by Stephen Boyd and Lieven Vandenberghe.
- There are many sources on [Lagrange multipliers](http://en.wikipedia.org/wiki/Lagrange_multipliers) (the special case of equality constraints) online that can be found by googling.

## Lecture 30: Quasi-Newton Methods and the BFGS Algorithm; Lecture 31: Derivation of the BFGS Update

### Summary

Began discussing quasi-Newton methods in general, and the Broyden–Fletcher–Goldfarb–Shanno (BFGS) algorithm in particular, following the handout below. Quasi-Newton methods are methods used to either find zeroes or local maxima and minima of functions, as an alternative to Newton's method. In numerical optimization, the BFGS algorithm is an iterative method for solving unconstrained nonlinear optimization problems.

- Lectures 30–31 handout: {{% resource_link "1b52b607-c223-977b-35ba-1d826e4d8df1" "Quasi-Newton Optimization: Origin of the BFGS Update (PDF)" %}}

### Further Reading

- [Quasi-Newton method](http://en.wikipedia.org/wiki/Quasi-Newton_methods) on Wikipedia
- [Broyden-Fletcher-Goldfarb-Shanno algorithm](http://en.wikipedia.org/wiki/BFGS_method) on Wikipedia
- [A New Derivation of Symmetric Positive Definite Secant Updates (PDF - 1.4MB)](https://www.sciencedirect.com/science/article/pii/B9780124686625500124) by J.E. Dennis, Jr and Robert B. Schnabel.
- [The Linear Algebra of Block Quasi-Newton Algorithms (PDF)](http://www.cs.umd.edu/~oleary/reprints/j39.pdf) by Dianne P. O'Leary and A. Yeremin.
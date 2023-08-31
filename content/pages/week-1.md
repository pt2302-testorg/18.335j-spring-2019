---
content_type: page
description: This section covers Lectures 1-2.
draft: false
learning_resource_types: []
ocw_type: CourseSection
title: Week 1
uid: 6950d4a0-73bc-0d04-aa63-962ae31c42a2
---
## Lecture 1: Course Overview, Newton's Method for Root-Finding

### Summary

Brief overview of the huge field of numerical methods and outline of the small portion that this course will cover. Key new concerns in numerical analysis, which don't appear in more abstract mathematics, are (i) performance (traditionally, arithmetic counts, but now memory access often dominates) and (ii) accuracy (both floating-point roundoff errors and also convergence of intrinsic approximations in the algorithms).

As a starting example, we considered the convergence of Newton's method (as applied to square roots); see the handout and Julia notebook below.

- Lecture 1 handout: {{% resource_link "0a734ecc-94b6-0a26-2134-88e68588bc8d" "Square Roots via Newton's Method (PDF)" %}}
- Lecture 1 notebook: [Square Roots](http://nbviewer.jupyter.org/github/mitmath/18335/blob/spring19/notes/Newton-Square-Roots.ipynb)

### Assignment

- {{% resource_link "6e673088-5b20-bd04-6cbd-e805d15a4835" "Problem set 1 (PDF)" %}}
- Problem set 1 notebook: [Problem set 1](https://nbviewer.jupyter.org/github/mitmath/18335/blob/spring19/psets/pset1.ipynb)
- {{% resource_link "e03746c6-51f0-a76f-651d-918a0aa0dd10" "Problem set 1 solutions (PDF)" %}}
- Problem set 1 solutions notebook: [Problem set 1 solutions](http://nbviewer.jupyter.org/github/mitmath/18335/blob/spring19/psets/pset1sol.ipynb)

### Further Reading

- [Newton's method](https://en.wikipedia.org/wiki/Newton's_method) from Wikipedia is a reasonable starting point. Googling "Newton's method" can find lots of references.
- Beware that the terminology for the [rate of convergence](https://en.wikipedia.org/wiki/Rate_of_convergence) (linear, quadratic, etc.) is somewhat different in this context from the terminology for discretization schemes (first-order, second-order, etc.); see e.g. the linked Wikipedia article.

## Lecture 2: Floating-Point Arithmetic

### Summary

The basic issue is that, for computer arithmetic to be fast, it has to be done in hardware, operating on numbers stored in a fixed, finite number of digits (bits). As a consequence, only a *finite subset* of the real numbers can be represented, and the question becomes *which subset* to store, how arithmetic on this subset is defined, and how to analyze the errors compared to theoretical exact arithmetic on real numbers.

In floating-point arithmetic, we store both an integer coefficient and an exponent in some base: essentially, scientific notation. This allows large dynamic range and fixed *relative* accuracy: if fl(*x*) is the closest floating-point number to any real *x*, then |fl(*x*)-*x*| \< ε|*x*| where ε is the *machine precision*. This makes error analysis much easier and makes algorithms mostly insensitive to overall scaling or units, but has the disadvantage that it requires specialized floating-point hardware to be fast. Nowadays, all general-purpose computers, and even many little computers like your cell phones, have floating-point units.

Went through some simple examples in Julia (see notebook below), illustrating basic syntax and a few interesting tidbits, in particular on the accuracy of summation algorithms, that we will investigate in more detail later.

Overview of floating-point representations, focusing on the IEEE 754 standard (see also handout from previous lecture). The key point is that the nearest floating-point number to *x*, denoted fl(*x*), has the property of *uniform relative precision* (for |*x*| and 1/|*x*| less than some *range*, ≈10308 for double precision) that |fl(*x*)−*x*| ≤ εmachine|*x*|, where εmachine is the relative "machine precision" (about 10−16 for double precision). There are also a few special values: ±Inf (e.g. for [overflow](https://en.wikipedia.org/wiki/Arithmetic_overflow)), [NaN](https://en.wikipedia.org/wiki/NaN), and ±0 (e.g. for [underflow](https://en.wikipedia.org/wiki/Arithmetic_underflow)).

- Lecture 2 handout:
- [Floating-Point Arithmetic](http://nbviewer.jupyter.org/github/mitmath/18335/blob/spring19/notes/Floating-Point-Intro.ipynb)
- {{% resource_link "88129903-3165-275f-3b15-ae8b172e6de8" "Some Myths about Floating-Point Arithmetic (PDF)" %}}

### Further Reading

- [What Every Computer Scientist Should Know About Floating Point Arithmetic](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.22.6768) by David Goldberg.
- [How Java’s Floating-Point Hurts Everyone Everywhere (PDF)](http://www.cs.berkeley.edu/~wkahan/JAVAhurt.pdf) by William Kahan and Joseph Darcy. This article contains a nice discussion of floating-point myths and misconceptions.
- Read “Lecture 13” in the textbook *Numerical Linear Algebra*.

## Julia Tutorial

We introduced [the Julia Programming Language](http://julialang.org/) that we will use this term.

- {{% resource_link "fb66800c-466e-fd52-4aa5-d76ddf928bf5" "Julia & IJulia Cheat-Sheet (PDF)" %}}
- {{% resource_link "ff680e9d-d985-7804-f64e-6f3bf523f80e" "Introduction to Julia (PDF)" %}}
- [Julia for Numerical Computation in MIT Courses](https://github.com/mitmath/julia-mit/blob/master/README.md)
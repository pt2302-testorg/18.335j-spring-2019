---
content_type: page
description: This section includes course meeting times, prerequisites, required textbook,
  additional reading, course requirements, grading, etc.
learning_resource_types: []
ocw_type: CourseSection
title: Syllabus
uid: c9f4954b-780b-4086-171e-810d3bd7f338
---

Course Meeting Times
--------------------

Lectures: 3 sessions / week, 1 hour / session

Prerequisites
-------------

[_18.06 Linear Algebra_](/courses/18-06sc-linear-algebra-fall-2011), [_18.700 Linear Algebra_](/courses/18-700-linear-algebra-fall-2013), or equivalents

Description
-----------

This course is an advanced introduction to numerical linear algebra and related numerical methods. Topics include direct and iterative methods for linear systems, eigenvalue decompositions and QR/SVD factorizations, stability and accuracy of numerical algorithms, the IEEE floating-point standard, sparse and structured matrices, and linear algebra software. Other topics may include memory hierarchies and the impact of caches on algorithms, nonlinear optimization, numerical integration, FFTs, and sensitivity analysis. Problem sets will involve use of [Julia](https://julialang.org/), a MATLAB®-like environment (little or no prior experience required; you will learn as you go).

Required Textbook
-----------------

Trefethen, Lloyd N. and David Bau III. _Numerical Linear Algebra_. SIAM: Society for Industrial and Applied Mathematics, 1997. ISBN: 9780898713619.

Additional Readings
-------------------

Barrett, Richard, Michael Berry, et al. [_Templates for the Solution of Linear Systems: Building Blocks for Iterative Methods_](http://www.netlib.org/linalg/html_templates/Templates.html). SIAM: Society for Industrial and Applied Mathematics, 1987. ISBN: 9780898713282.

Bai, Zhaojun, James Demmel, et al. [_Templates for the Solution of Algebraic Eigenvalue Problems: a Practical Guide_](http://www.cs.utk.edu/~dongarra/etemplates/index.html). SIAM: Society for Industrial and Applied Mathematics, 1987. ISBN: 9780898714715.

Course Requirements
-------------------

There are four problem sets, a take-home midterm exam, and a final project.

Collaboration Policies
----------------------

Talk to anyone you want to and read anything you want to, with three exceptions: First, you may not refer to homework solutions from the previous terms. Second, make a solid effort to solve a problem on your own before discussing it with classmates or googling. Third, no matter whom you talk to or what you read, write up the solution on your own, without having their answer in front of you.

Final Project
-------------

The final project will be a 8–15 page paper (single-column, single-spaced, ideally using the style template from the [_SIAM Journal on Numerical Analysis_](https://www.siam.org/Publications/Journals/About-SIAM-Journals/Information-for-Authors)), reviewing some interesting numerical algorithm not covered in the course. \[Since this is not a numerical Partial Differential Equations course, the algorithm should not be an algorithm for turning PDEs into finite/discretized systems; however, your project may take a PDE discretization as a given "black box" and look at some other aspect of the problem, e.g. iterative solvers.\] Your paper should be written for an audience of your peers in the class, and should include example numerical results (by you) from application to a realistic problem (small-scale is fine), discussion of accuracy and performance characteristics (both theoretical and experimental), and a fair comparison to at least one competing algorithm for the same problem. Like any review paper, you should thoroughly reference the published literature (citing both original articles and authoritative reviews/books where appropriate \[rarely web pages\]), tracing the historical development of the ideas and giving the reader pointers on where to go for more information and related work and later refinements, with references cited throughout the text (enough to make it clear what references go with what results). (Note: you may re-use diagrams from other sources, but all such usage must be _explicitly credited_; not doing so is [plagiarism](http://writing.mit.edu/wcc/avoidingplagiarism).) Model your paper on academic review articles (e.g. read _SIAM Review_ and similar journals for examples).

Frequently asked questions about the final project:

1.  _Does it have to be about numerical linear algebra?_ No. It can be any numerical topic (basically, anything where you are computing a conceptually real result, not integer computations), excluding algorithms for discretizing PDEs.
2.  _Can I use a matrix from a discretized PDE?_ Yes. You can take a matrix from the PDE as input and then talk about iterative methods to solve it, etcetera. I just don't want the paper to be about the PDE discretization technique itself.
3.  _How formal is the proposal?_ Very informal—one page describing what you plan to do, with a couple of references that you are using as starting points. Basically, the proposal is just so that I can verify that what you are planning is reasonable and to give you some early feedback.
4.  _How much code do I need to write?_ A typical project (there may be exceptions) will include a working proof-of-concept implementation, e.g. in Julia or Python or MATLAB, that you wrote to demonstrate that you understand how the algorithm works. Your code does not have to be competitive with "serious" implementations, and I encourage you to download and try out existing "serious" implementations (where available) for any large-scale testing and comparisons.
5.  _How should I do performance comparisons?_ Be very cautious about timing measurements: unless you are measuring highly optimized code or only care about orders of magnitude, timing measurements are more about implementation quality than algorithms. Better to measure something implementation independent (like flop counts, or matrix-vector multiplies for iterative algorithms, or function evaluations for integrators/optimizers), although such measures have their own weaknesses.

Grading
-------

{{< tableopen >}}
{{< theadopen >}}
{{< tropen >}}
{{< thopen >}}
ACTIVITIES
{{< thclose >}}
{{< thopen >}}
PERCENTAGES
{{< thclose >}}

{{< trclose >}}

{{< theadclose >}}
{{< tropen >}}
{{< tdopen >}}
Problem sets
{{< tdclose >}}
{{< tdopen >}}
33%
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
Mid-term exam
{{< tdclose >}}
{{< tdopen >}}
33%
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
Final project
{{< tdclose >}}
{{< tdopen >}}
34%
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}
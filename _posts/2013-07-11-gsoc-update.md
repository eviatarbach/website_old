---
layout: post
title: Google Summer of Code status update
---

My work was delayed for a few days due to having to deal with some registration issues at my university.

I now have all the main features of hypergeometric functions working, with an initial patch at [#2516](http://trac.sagemath.org/sage_trac/ticket/2516), and also fixed a bug dependency with [#14858](http://trac.sagemath.org/sage_trac/ticket/14858). Now I am just expanding the documentation and adding tests.

I also wrote a patch for unholding expressions with held operations, [#10034](http://trac.sagemath.org/sage_trac/ticket/10034), which I thought initially I would use for implementing simplification of hypergeometric functions, but ended up doing it differently. It is useful for other purposes, however.

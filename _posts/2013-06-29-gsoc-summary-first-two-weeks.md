---
layout: post
title: Google Summer of Code&#58; Summary of the first two weeks
---

It has been two weeks since I started my Google Summer of Code project for Sage.

Before the start date, I began on the benchmark framework and adding SymPy conversions to functions that lacked them. The latter will make conversions from Sage to SymPy expressions better, although the reverse is still a problem. This is because Sage doesn't parse SymPy expressions as it would for Maxima, for example; it calls a `_sage_` method on the SymPy objects, which means that Sage has to rely on SymPy developers to add the conversions, which hasn't been reliable so far. Maybe this should be changed in the future.

For the first week I was fortunate to be at [Sage Days 48](http://wiki.sagemath.org/days48), ostensibly organized for working on the Sage Notebook, although some, including me, worked on different parts of Sage. I really enjoyed it and learned a lot. Burcin Erocal wrote some patches adding dynamic attributes to symbolic expressions ([#9556](http://trac.sagemath.org/sage_trac/ticket/9556)) and allowing symbolic functions to take tuple arguments ([#14780](http://trac.sagemath.org/sage_trac/ticket/14780)), which lays the foundation for implementing hypergeometric functions smoothly. I worked on getting some special function-related patches merged, including making Bessel functions symbolic ([#4102](http://trac.sagemath.org/sage_trac/ticket/4102)), making Airy functions symbolic ([#12455](http://trac.sagemath.org/sage_trac/ticket/12455)), and fixing numerical evaluation of `log_gamma` ([#12521](http://trac.sagemath.org/sage_trac/ticket/12521), a palindrome ticket!). I also started working on hypergeometric functions.

This past week I have been mostly working on the hypergeometric functions (see [here](https://www.math.umass.edu/~cattani/hypergeom_lectures.pdf) for an introduction), building on Fredrik Johansson's code in [#2516](http://trac.sagemath.org/sage_trac/ticket/2516). It needs some modification, since it was implemented in a way to work around the aforementioned limitations of symbolic expressions that have now been removed with Burcin's patches. I've been making progress and should have a patch next week.

I'm going to make sure I'm diligent with uploading and following through with patches, since I've heard this is sometimes a problem with GSoC projects.

---
layout: post
title: Confluent hypergeometric functions in Sage
math: true
---

The [confluent hypergeometric functions](http://en.wikipedia.org/wiki/Confluent_hypergeometric_function) are solutions to Kummer's differential equation, \\(z\frac{d^2w}{dz^2} + (b-z)\frac{dw}{dz} - aw = 0.\\) Two linearly independent solutions are functions denoted as \\(M\\) and \\(U\\), which I implemented symbolically in Sage (\\(U\\) was already implemented, but only numerically).

Here are some things it can do:

{% highlight python %}
sage: (hypergeometric_M(1, 1, 1) +
....:  hypergeometric_U(1, 2, 1)).simplify_hypergeometric()
e + 1
sage: hypergeometric_U(1, 3, x).simplify_hypergeometric()
(x + 1)/x^2
sage: hypergeometric_M(1, 3/2, 1).simplify_hypergeometric()
1/2*sqrt(pi)*e*erf(1)
sage: hypergeometric_U(2, 2, x).series(x == 3, 100).subs(x=1).n()
0.403652637676806
sage: hypergeometric_U(2, 2, 1).n()
0.403652637676806
{% endhighlight %}

As far as I can tell, no open-source computer algebra system has this level of simplification of confluent hypergeometric functions; Maxima is used here, but it is not wrapped like this in Maxima. I hope this will prove useful for those working with hypergeometric functions or differential equations in Sage.

It's fairly trivial to implement the [Whittaker functions](http://en.wikipedia.org/wiki/Whittaker_function) in a similar way; the reason I haven't yet is because I didn't want to make the patch larger and stall review, and because the Maxima conversions are a bit trickier.

The newly implemented [dynamic attributes for symbolic expressions](http://trac.sagemath.org/sage_trac/ticket/9556) have proved enormously useful for this ticket, as well as for the generalized hypergeometric functions and for [Volker Braun's new implementation of piecewise functions](http://trac.sagemath.org/sage_trac/ticket/14801). I may write a new section for the Developer's Guide which explains symbolic functions in detail, including the dynamic attributes.

I uploaded a patch at <a href="http://trac.sagemath.org/sage_trac/ticket/14896">#14896</a>; however, since it makes use of the generalized hypergeometric framework of <a href="http://trac.sagemath.org/sage_trac/ticket/2516">#2516</a>, that patch has to be merged first. Any help with review would be greatly appreciated!

---
layout: post
title: Dual numbers and automatic differentiation
math: true
---

[Dual numbers](http://en.wikipedia.org/wiki/Dual_number) are an extension of the real numbers that can be written in the form \\(a + b\varepsilon\\), \\(a, b\in\mathbb{R}\\), with the property that \\(\varepsilon^2=0\\).

An interesting consequence is that

\\[f(a + b\varepsilon)=f(a) + bf'(a)\varepsilon,\\]

where \\(f\\) is a smooth function and \\(f'\\) is its derivative.

This can be used for [automatic differentiation](http://en.wikipedia.org/wiki/Automatic_differentiation), a way of computing numerical derivatives that *is neither symbolic nor a finite difference approximation*. Basically, it computes the derivative by applying the atomic operations that constitute the function to a dual number. To compute \\(\frac{d}{dx} \frac{1}{x}\\) at \\(x=3\\), simply calculate the dual component of \\(\frac{1}{3 + \varepsilon}\\).

Here is some code I wrote in Python 2.7 that implements dual numbers with basic operations and very basic automatic differentiation (see [ScientificPython](http://dirac.cnrs-orleans.fr/plone/software/scientificpython/)'s similar implementation):

{% highlight python %}
class DualNumber:
    def __init__(self, real, dual):
        self.real = real
        self.dual = dual

    def __add__(self, other):
        if isinstance(other, DualNumber):
            return DualNumber(self.real + other.real,
                              self.dual + other.dual)
        else:
            return DualNumber(self.real + other, self.dual)
    __radd__ = __add__

    def __sub__(self, other):
        if isinstance(other, DualNumber):
            return DualNumber(self.real - other.real,
                              self.dual - other.dual)
        else:
            return DualNumber(self.real - other, self.dual)

    def __rsub__(self, other):
        return DualNumber(other, 0) - self

    def __mul__(self, other):
        if isinstance(other, DualNumber):
            return DualNumber(self.real * other.real,
                              self.real * other.dual + self.dual * other.real)
        else:
            return DualNumber(self.real * other, self.dual * other)
    __rmul__ = __mul__

    def __div__(self, other):
        if isinstance(other, DualNumber):
            return DualNumber(self.real/other.real,
                              (self.dual*other.real - self.real*other.dual)/(other.real**2))
        else:
            return (1/other) * self

    def __rdiv__(self, other):
        return DualNumber(other, 0).__div__(self)

    def __pow__(self, other):
        return DualNumber(self.real**other,
                          self.dual * other * self.real**(other - 1))

    def __repr__(self):
        return repr(self.real) + ' + ' + repr(self.dual) + '*epsilon'

def auto_diff(f, x):
    return f(DualNumber(x, 1.)).dual
{% endhighlight %}

To see the advantage of automatic differentiation over finite difference approximations, consider \\(\frac{d}{dx}\frac{1}{x^5}\\) at \\(x=0.01\\). Compare SciPy's `scipy.misc.derivative` to automatic differentiation:

{% highlight python %}
>>> import scipy.misc
>>> scipy.misc.derivative(lambda x:1./(x**5), 0.01, dx=1e-5), auto_diff(lambda x:1./(x**5), 0.01)
(-5000035000125.6943, -4999999999999.998)
{% endhighlight %}

Even with a spacing of \\(10^{-5}\\), finite difference is much more inaccurate, and also slower (around 5 times slower for this input).

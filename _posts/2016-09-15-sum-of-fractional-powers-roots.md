---
layout: post
title: Finding roots of a sum of fractional powers
math: true
---

Suppose we want to find numerically all the nonnegative, real roots of a sum of fractional powers. More precisely, we want the nonnegative roots of functions of the type
\[f(x) = c_0 x^{\frac{n_0}{d_0}} + c_1 x^{\frac{n_1}{d_1}} + \ldots + c_m x^{\frac{n_m}{d_m}},\]
with \(x\) and the coefficients \(c_i\) real, and the exponents \(\big\{\frac{n_i}{d_i}\big\}\) nonnegative rationals expressed in lowest terms. These types of functions are sometimes called fractional polynomials (since they resemble polynomials, but have rational exponents).

Root-finding of nonlinear equations is not always easy, especially when we want all the roots, and a bounded domain on which they occur is unknown. Fortunately, in this case we can make a substitution to transform the function into a polynomial, for which there exist algorithms to find all the roots. I have not found a description of this elsewhere, so I thought I would make a post about it.

Let \(l=\operatorname{lcm}\{d_i\}\) and \(g=\gcd\{n_i\}\). Then, \(f\left(y^{\frac{l}{g}}\right)\) is a polynomial in \(y\), since all the \(\{d_i\}\) are factors of \(l\) and all the \(\{n_i\}\) are multiples of \(g\). The roots of this polynomial, \(\{y^\ast_i\}\), can then be found numerically using polynomial root-finding routines. Transforming back, the roots of \(f(x)\) will be \(\left\{{y^\ast_i}^{\frac{l}{g}}\right\}\).

I may later post some details on efficiency, applicability, etc.

Below is a Python implementation of this using the `fractions` standard library module and NumPy. I don't know if NumPy's algorithm for polynomial roots is state-of-the-art, however. Note that the `RationalPowers` class is initialized only with the exponents, and the coefficients are provided as inputs in the root-finding and evaluation methods. This is because, for my own work, I needed to do root-finding multiple times with the same exponents but different coefficients, and the exponent logic needs to be done only once.

Usage examples are provided in the docstrings.

{% gist e6373f9b7096936de86da4b0d3779999 %}

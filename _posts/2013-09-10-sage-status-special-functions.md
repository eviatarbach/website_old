---
layout: post
title: Status of special functions in Sage
math: true
---

Hello,

Sorry for not posting status updates in a while, but much of what I've been working on would not be interesting to a general audience of Sage users.

The Digital Library of Mathematical Functions has a [Software Index](http://dlmf.nist.gov/software/), which lists the software that implement certain mathematical function. For Sage, that list is extremely out of date. Despite having sent an email to the DLMF with updates (the editor has confirmed that the table will be updated in the next release of the DLMF), I still think it's valuable to give a more detailed outline of the status of special functions in Sage so that gaps can be filled (especially the blue and violet entries, which have patches available!). Sorry about the excessive colour; I wanted to make it easy to discern the categories.

<table>
<th>Legend</th>
<tr>
<td style="background-color:lightgreen">Green: Available in Sage</td>
</tr>
<tr>
<td style="background-color:lightblue">Blue: Patch implementing it is available</td>
</tr>
<tr>
<td style="background-color:lightyellow">Yellow: Partially available</td>
</tr>
<tr>
<td style="background-color:violet">Violet: Available, and patch with improvements exists</td>
</tr>
<tr>
<td style="background-color:orange">Orange: Implemented in mpmath but not in Sage</td>
</tr>
<tr>
<td style="background-color:lightpink">Pink: Not available in mpmath nor Sage</td>
</tr>
</table>

<table>
    <tr>
        <th style="background-color:lightgreen">4&nbsp;Elementary Functions</th>
        <td></td>
    </tr>
    <tr>
        <th>5&nbsp;Gamma Function</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;5.24(ii) \(\mathop{\Gamma}\nolimits\!\left(x\right), x\in\mathbb{R}\)</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;5.24(iii) \(\mathop{\psi}\nolimits\!\left(x\right), \mathop{\psi^{(n)}}\nolimits\!\left(x\right), x\in\mathbb{R}\)</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;5.24(iv) \(\mathop{\Gamma}\nolimits\!\left(z\right), \mathop{\psi}\nolimits\!\left(z\right), \mathop{\psi^{(n)}}\nolimits\!\left(z\right), z\in\mathbb{C}\)</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;5.24(v) \(\mathop{\mathrm{B}}\nolimits\!\left(a,b\right), a,b\in\mathbb{R}\)</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightblue">&sect;5.24(vi) \(\mathop{\mathrm{B}}\nolimits\!\left(a,b\right), a,b\in\mathbb{C}\)</td>
        <td><a href="http://trac.sagemath.org/ticket/12521">12521</a> would fix this, but a better solution (both for speed and precision) would be to use mpmath.</td>
    </tr>
    <tr>
        <th style="background-color:lightgreen">6&nbsp;Exponential, Logarithmic, Sine, and Cosine Integrals</th>
        <td>✓</td>
    </tr>
    <tr>
        <th>7&nbsp;Error Functions, Dawson&rsquo;s and Fresnel Integrals</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;7.25(ii) \(\mathop{\mathrm{erf}}\nolimits x, \mathop{\mathrm{erfc}}\nolimits x, \mathop{\mathrm{i}^{n}\mathrm{erfc}}\nolimits\!\left(x\right), x\in\mathbb{R}\)</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightyellow">&sect;7.25(iii) \(\mathop{\mathrm{erf}}\nolimits z, \mathop{\mathrm{erfc}}\nolimits z, z\in\mathbb{C}\)</td>
        <td>\(\mathrm{erfc}\) is not yet implemented for complex numbers.</td>
    </tr>
    <tr>
    <tyle="background-color:lightblue">Blue: Patch implementing it is av│      Regenerating: 1 file(s) changed at 2015-07-12 19:41:39 ...done in
d style="background-color:orange">&sect;7.25(iv) \(\mathop{C}\nolimits\!\left(x\right), \mathop{S}\nolimits\!\left(x\right), \mathop{\mathrm{f}}\nolimits\!\left(x\right), \mathop{\mathrm{g}}\nolimits\!\left(x\right), x\in\mathbb{R}\)</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;7.25(v) \(\mathop{C}\nolimits\!\left(z\right), \mathop{S}\nolimits\!\left(z\right), z\in\mathbb{C}\)</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightpink">&sect;7.25(vi) \(\mathop{\mathcal{F}}\nolimits\!\left(x\right), \mathop{G}\nolimits\!\left(x\right), \mathop{\mathsf{U}}\nolimits\!\left(x,t\right), \mathop{\mathsf{V}}\nolimits\!\left(x,t\right), x\in\mathbb{R}\)</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightpink">&sect;7.25(vii) \(\mathop{\mathcal{F}}\nolimits\!\left(z\right), \mathop{G}\nolimits\!\left(z\right), z\in\mathbb{C}\)</td>
        <td></td>
    </tr>
    <tr>
        <th>8&nbsp;Incomplete Gamma and Related Functions</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;8.28(ii) Incomplete Gamma Functions for Real Argument and Parameter</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;8.28(iii) Incomplete Gamma Functions for Complex Argument and Parameter</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;8.28(v) Incomplete Beta Functions for Complex Argument and Parameters</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;8.28(vi) Generalized Exponential Integral for Real Argument and Integer Parameter</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;8.28(vii) Generalized Exponential Integral for Complex Argument and Parameter</td>
        <td>✓</td>
    </tr>
    <tr>
        <th>9&nbsp;Airy and Related Functions</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;9.20(ii) \(\mathop{\mathrm{Ai}}\nolimits\!\left(x\right), {\mathop{\mathrm{Ai}}\nolimits^{\prime}}\!\left(x\right), \mathop{\mathrm{Bi}}\nolimits\!\left(x\right), {\mathop{\mathrm{Bi}}\nolimits^{\prime}}\!\left(x\right), &nbsp;x\in\mathbb{R}\)</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightblue">&sect;9.20(iii) \(\mathop{\mathrm{Ai}}\nolimits\!\left(z\right), {\mathop{\mathrm{Ai}}\nolimits^{\prime}}\!\left(z\right), \mathop{\mathrm{Bi}}\nolimits\!\left(z\right), {\mathop{\mathrm{Bi}}\nolimits^{\prime}}\!\left(z\right), &nbsp;z\in\mathbb{C}\)</td>
        <td>See&nbsp;<a href="http://trac.sagemath.org/ticket/12455">12455</a></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;9.20(iv) Real and Complex Zeros</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightblue">&sect;9.20(v) Integrals of \(\mathop{\mathrm{Ai}}\nolimits\!\left(x\right), \mathop{\mathrm{Bi}}\nolimits\!\left(x\right), x\in\mathbb{R}\)</td>
        <td>See&nbsp;<a href="http://trac.sagemath.org/ticket/12455">12455</a></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;9.20(vi) Scorer Functions</td>
        <td></td>
    </tr>
    <tr>
        <th>10&nbsp;Bessel Functions</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;10.77(ii) Bessel Functions&ndash;Real Argument and Integer or Half-Integer Order (including Spherical Bessel Functions)</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;10.77(iii) Bessel Functions&ndash;Real Order and Argument</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightyellow">&sect;10.77(iv) Bessel Functions&ndash;Integer or Half-Integer Order and Complex Arguments, including Kelvin Functions</td>
        <td>Kelvin functions are not implemented. They are in mpmath however.</td>
    </tr>
    <tr>
        <td style="background-color:lightblue">&sect;10.77(v) Bessel Functions&ndash;Real Order and Complex Argument (including Hankel Functions)</td>
        <td>See <a href="http://trac.sagemath.org/ticket/15024">15024</a></td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;10.77(viii) Bessel Functions&ndash;Complex Order and Argument</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;10.77(ix) Integrals of Bessel Functions</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;10.77(x) Zeros of Bessel Functions</td>
        <td></td>
    </tr>
    <tr>
        <th>11&nbsp;Struve and Related Functions</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;11.16(ii) Struve Functions</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightpink">&sect;11.16(iii) Integrals of Struve Functions</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;11.16(iv) Lommel Functions</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;11.16(v) Anger and Weber Functions</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightpink">&sect;11.16(vi) Integrals of Anger and Weber Functions</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">12 Parabolic Cylinder Functions</td>
        <td></td>
    </tr>
    <tr>
        <th>13 Confluent Hypergeometric Functions</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:violet">&sect;13.32(ii) Real Argument and Parameters</td>
        <td>See&nbsp;<a href="http://trac.sagemath.org/ticket/14896">14896</a></td>
    </tr>
    <tr>
        <td style="background-color:violet">&sect;13.32(iii)Complex Argument and/or Parameters</td>
        <td>See&nbsp;<a href="http://trac.sagemath.org/ticket/14896">14896</a></td>
    </tr>
    <tr>
        <th>14&nbsp;Legendre and Related Functions</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;14.34(ii)Legendre Functions: Real Argument and Parameters</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;14.34(iii)Legendre Functions: Complex Argument and/or Parameters</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightpink">&sect;14.34(iii)Legendre Functions: Complex Argument and/or Parameters</td>
        <td></td>
    </tr>
    <tr>
        <th>15&nbsp;Hypergeometric Function</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightblue">&sect;15.20(ii)&nbsp;Real Parameters and Argument</td>
        <td>See <a href="http://trac.sagemath.org/ticket/2516">2516</a></td>
    </tr>
    <tr>
        <td style="background-color:lightblue">&sect;15.20(iii) Complex Parameters and Argument</td>
        <td>See <a href="http://trac.sagemath.org/ticket/2516">2516</a></td>
    </tr>
    <tr>
        <th>16 Generalized Hypergeometric Functions and Meijer G-Function</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightblue">&sect;16.27(ii) Real Argument and Parameters</td>
        <td>See <a href="http://trac.sagemath.org/ticket/2516">2516</a></td>
    </tr>
    <tr>
        <td style="background-color:lightblue">&sect;16.27(iii) Complex Argument and/or Parameters</td>
        <td>See <a href="http://trac.sagemath.org/ticket/2516">2516</a></td>
    </tr>
    <tr>
        <th style="background-color:lightgreen">18 Orthogonal Polynomials</th>
        <td>✓</td>
    </tr>
    <tr>
        <th>19 Elliptic Integrals</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:violet">&sect;19.39(ii) Legendre&rsquo;s and Bulirsch&rsquo;s Complete Integrals</td>
        <td>See&nbsp;<a href="http://trac.sagemath.org/ticket/15046">15046</a></td>
    </tr>
    <tr>
        <td style="background-color:violet">&sect;19.39(iii) Legendre&rsquo;s and Bulirsch&rsquo;s Incomplete Integrals</td>
        <td>See&nbsp;<a href="http://trac.sagemath.org/ticket/15046">15046</a></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;19.39(iv) Symmetric Integrals</td>
        <td></td>
    </tr>
    <tr>
        <th style="background-color:orange">20 Theta Functions</th>
        <td></td>
    </tr>
    <tr>
        <th style="background-color:lightpink">21 Multidimensional Theta Functions</th>
        <td></td>
    </tr>
    <tr>
        <th style="background-color:violet">22 Jacobian Elliptic Functions</th>
        <td>See <a href="http://trac.sagemath.org/ticket/14996">14996</a></td>
    </tr>
    <tr>
        <th style="background-color:lightpink">23 Weierstrass Elliptic and Modular Functions</th>
        <td></td>
    </tr>
    <tr>
        <th style="background-color:lightyellow">24 Bernoulli and Euler Polynomials</th>
        <td>Euler polynomials are not implemented.</td>
    </tr>
    <tr>
        <th>25 Zeta and Related Functions</th>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;25.21(ii) Zeta Functions for Real Arguments</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;25.21(iii) Zeta Functions for Complex Arguments</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:violet">&sect;25.21(iv) Hurwitz Zeta Function</td>
        <td>See&nbsp;<a href="http://trac.sagemath.org/ticket/15095">15095</a></td>
    </tr>
    <tr>
        <td style="background-color:lightgreen">&sect;25.21(v) Dilogarithms, Polylogarithms</td>
        <td>✓</td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;25.21(vi) Clausen&rsquo;s Integral</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:lightpink">&sect;25.21(vii) Fermi&ndash;Dirac and Bose&ndash;Einstein Integrals</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;25.21(viii) Lerch&rsquo;s Transcendent</td>
        <td></td>
    </tr>
    <tr>
        <td style="background-color:orange">&sect;25.21(ix) Dirichlet L-series</td>
        <td></td>
    </tr>
    <tr>
        <th style="background-color:lightgreen">26 Combinatorial Analysis</th>
        <td>✓</td>
    </tr>
    <tr>
        <th style="background-color:lightgreen">27 Functions of Number Theory</th>
        <td>✓</td>
    </tr>
    <tr>
        <th style="background-color:lightpink">28 Mathieu Functions and Hill&rsquo;s Equation</th>
        <td></td>
    </tr>
    <tr>
        <th style="background-color:lightpink">30 Spheroidal Wave Functions</th>
        <td></td>
    </tr>
    <tr>
        <th style="background-color:orange">33 Coulomb Functions</th>
        <td></td>
    </tr>
    <tr>
        <th style="background-color:lightgreen">34 3j,6j,9j Symbols</th>
        <td>✓</td>
    </tr>
    <tr>
        <th style="background-color:lightpink">35 Functions of Matrix Argument</th>
        <td></td>
    </tr>
</table>

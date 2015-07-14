---
layout: post
title: Getting matching colours from a list
---

There are plenty of tools for generating colour schemes automatically. However, I could not find any that would generate colour schemes using only colours provided by the user, so I wrote my own.

## What are "matching" colours?

Of course, to find matching colours one must have some matching criterion. I don't know much about colour theory, but I found a paper by Cohen-Or et al.[^1] that defines sectors of the hue wheel that correspond to "harmonic" colours, the idea being that combinations of colours from these sectors are aesthetically pleasing (of course, I'm sure there are cultural differences).

The following figure (Figure 2 in the paper) shows different "templates", each of which defines sectors which can be rotated arbitrarily. The precise angles are also given in the paper, in the Appendix. The reflection of L is also a template, and is referred to as L2 in the code.

![Harmonic sectors on the hue wheel]({{ site.url }}/assets/harmonic_sectors.png)

As you can see, some templates allow for very narrow colour combinations (i type) while others are more permissive (X type).

## Implementation

I wrote a script in Python to find matching colours in a list based on the match criteria above. The user inputs a template, a list of colours in RGB, and the number of colours that they want in the scheme, and the script will attempt to find such a scheme, returning an error if it fails.

It works by rotating the sectors by a discrete amount (the step size can be modified), checking which of the given colours in can fit in the sectors, and returning as soon as it succeeds in fitting the desired number of colours into the sectors. There is some randomness involved: the rotations are performed in a randomorder, and if more colours can be fit than requested, some will be randomly removed. The algorithm can be modified to generate all the possible colour schemes under the given inputs, but the number of such schemes grows very quickly with the list of colours provided.

## Example

Let's test out the script on a random set of colours. I'll use [Sage](http://www.sagemath.org/) to plot the colours as circles, although it's a bit of overkill. I'm generating the colours uniformly at random in RGB space, which doesn't necessarily correspond to uniformly at random in human colour perception. In any case, here goes:

{% highlight python %}
sage: colours = [(randint(0, 255), randint(0, 255), randint(0, 255)) for _ in range(10)]
sage: def plot_colours(colours):
....:     plot([circle((2*i, 0), 1, rgbcolor=colour, fill=True) for i, colour in enumerate(map(lambda c: (c[0]/255, c[1]/255, c[2]/255), colours))], axes=False, aspect_ratio=1).show()
....:
sage: plot_colours(colours)
{% endhighlight %}

![Random colours]({{ site.url }}/assets/random_colours.png)

This is the list of colours we'll be using. Now let's try picking three of these that fit in the L template:

{% highlight python %}
plot_colours(fit(colours, 'L', 3))
{% endhighlight %}

![L colours]({{ site.url }}/assets/L_colours.png){:height="77px"}

Now four in the i template:

{% highlight python %}
plot_colours(fit(colours, 'i', 4))
{% endhighlight %}

![i colours]({{ site.url }}/assets/i_colours.png){:height="77px"}

## Code

{% gist bca5fb04edc14893edab %}

[^1]: D. Cohen-Or, O. Sorkine, R. Gal, T. Leyvand, and Y.-Q. Xu, "Color Harmonization," in *ACM SIGGRAPH 2006 Papers*, New York, NY, USA, 2006, pp. 624–630.

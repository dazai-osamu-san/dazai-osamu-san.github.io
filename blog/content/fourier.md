---
title: "What is Fourier Series and How it Came to Be?"
date: 2023-05-03
draft: false
tags: ["mathematics", "fourier", "signal-processing"]
math: true
---

The Fourier series is a mathematical concept which was developed by the French mathematician Jean-Baptiste Fourier in the early 19th century. He engraved his name in the mathematics hall of fame with the groundbreaking discovery of Fourier series.

Fourier's key insight was that any function could be decomposed into a sum of sine and cosine waves with different amplitudes and frequencies. This discovery laid the foundation many areas science like physics, telecommunication etc.

Fourier derived a formula which is now known as the Fourier series which provides a systematic way of expressing any function (provided it matches Dirichlet's[^1] conditions) as an infinite sum of sines and cosines.

All of this is quite a bit to understand just through words, so lets look at a small animation which will help us understand a bit easier. (This animation was taken from 3b1b's video on this very topic. Watch the video after reading this!)

![Fourier Animation]("/blog/StickAround.gif")

Pretty cool right!? Now lets take a look at the maths.

## The Formula

According to the statement lets consider a function $f(x)$ with a period $T$ defined on an interval $[-\pi, \pi]$. Then the Fourier series representation of $f(x)$ is given by:

$$f(t) = a_0 + \sum_{n=1}^{\infty}[a_n\cos{n\omega t} + b_n\sin{n\omega t}]$$

where

- $a_0$ is the constant term
- $a_n$ and $b_n$ are called Fourier coefficients and $n$ is a positive integer
- $\omega$ is the fundamental frequency

## Calculating Fourier Coefficients and the Constant

The Fourier coefficients can be found using these formulae:

$$a_{0} = \frac{1}{2\pi} \int^{\pi}_{-\pi}f(x) dx$$

$$a_n = \frac{1}{\pi} \int_{-\pi}^{\pi}f(x)\cos{nx}dx$$

$$b_n = \frac{1}{\pi} \int^{\pi}_{-\pi} f(x)\sin{nx}dx$$

Where $\forall n \in \mathbb{N}$

## Breaking Down the Math

Looking at the statement we can very easily understand how the formula came to be.

As we know, a Fourier series is a decomposition of a function into sine and cosine waves, and the sum of these waves of different frequencies up till infinity very closely represents the original function $f(x)$, thus the term 

$$\sum_{n=1}^{\infty}$$

which means sum of all terms for $n = 1$ to infinity.

Obviously there is no such thing as *infinite*, but the more number of terms you add the closer it represents to the original function, so *tending* to infinity.

Now the coefficients are what decide the frequency and amplitude of each of the waves. Now the constant term $a_0$ is the average of all the outputs of the function over the certain interval, yielding equation $a_{0} = \frac{1}{2\pi} \int^{\pi}_{-\pi}f(x) dx$.

If we break this down into $f(x)$ into the sums again and integrate individual terms, there will be only one term whose integral will be a constant number and all others will be 0. This one constant term is $a_0$.

Wow if we multiply $f(x)$ by some other term, and then repeat the above step again, then some nth term will be the constant term, which is actually $a_n$! Here we are multiplying each term with a sine wave, thus the equation:

$$a_n = \frac{1}{\pi} \int_{-\pi}^{\pi}f(x)\sin{nx}dx$$

And similarly we can also calculate $b_n$.

Lets understand this better by solving a question. Consider the following function:

$$f(x) = \begin{cases}
-k & \text{when } -\pi < x < 0 \\
+k & \text{when } 0 < x < \pi
\end{cases}$$

The graph of the function will look like this:

![Function Graph](/blog/static/graph1.png)

Now we need to find the right sum of sines and cosines which will closely represent this function. First we need to find the constant $a_0$. Let's use the formula:

$$a_{0} = \frac{1}{2\pi} \int^{\pi}_{-\pi}f(x) dx$$

Since this function is discontinuous we can break it down into two, so from $-\pi$ to $0$ the value of the function $f(x)$ will be $-k$ and from $0$ to $\pi$ it will be $k$, $\therefore$

$$a_0 = \frac{1}{2\pi}\left[ \int_{-\pi}^{0}-k dx + \int_{0}^{\pi}k dx\right]$$

Solving this integral we get the answer:

$$a_0 = 0$$

To the keen eyes, this result was obvious, as $a_0$ is the average value over the entire period, it is in fact 0 in this case. Let's move on to calculating $a_n$ now; using the formula:

$$a_n = \frac{1}{\pi} \int_{-\pi}^{\pi}f(x)\cos{nx}dx$$

Now break it down as before and solve the integral and we get:

$$a_n = 0$$

This means that there are no terms of cosine present in the Fourier series.

Repeating the same we find $b_n$ and get the following result:

Now we get two cases when n is odd and n is even, lets consider them individually.

### Case 1: n is even

When n is even and you substitute values you get 0. This means there are no even terms.

### Case 2: n is odd

When n is odd, we obtain this equation:

$$b_n = \frac{4k}{n\pi}$$

So for all odd values of n we get:

$$b_1 = \frac{4k}{\pi},\ b_2 = \frac{4k}{3\pi},\ b_3= \frac{4k}{5\pi}$$

and so on.

Substituting all the values in the original formula we get:

$$f(x) = 0 + \sum_{n=1}^{\infty}(0 + b_n\sin{nx})$$

$\therefore$ we can say,

$$f(x) = \frac{4k}{\pi}\left(\sin{x} + \frac{1}{3}\sin{3x} + \frac{1}{5}\sin{5x} + ...\right)$$

Now if we plot this function against the original graph we get this:

![Desmos Graph Comparison](/blog/static/desmos-graph.png)

*Red line: original function | Black line: calculated function*

Hence we can say that any function $f(x)$ can be represented as a sum of sine and cosine waves.

As we can see the function we just calculated is very close to what the original function looks.

That's it for this blog.

Thanks for reading!~

[^1]: Dirichlet's conditions

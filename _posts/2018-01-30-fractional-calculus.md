---
layout: post
title: Fractional Calculus
tags: math calculus
---
## Basic Differentiation
In general terms, derivatives are a measure of how a function changes with respect to another variable. Not all functions have derivatives, but those that do are called **differentiable**.

The derivative of a function is itself a function and thus can be further differentiated. This means we can define things like the **second derivative** which is obtained by successively taking the derivative of a function twice.

Take the function $$x^3$$. It's first derivative is usually denoted:

$$\frac{\mathrm{d} }{\mathrm{d} x}x^3=3x^2$$

It's second derivative is denoted:

$$\frac{\mathrm{d} }{\mathrm{d} x}\left(\frac{\mathrm{d} }{\mathrm{d} x}x^3\right)=\frac{\mathrm{d^2} }{\mathrm{d} x^2}x^3=6x$$

We can extend this idea (and its notation) to any integer $$n$$ forming the nth derivative of a function $$f(x)$$:

$$\frac{\mathrm{d^n} }{\mathrm{d} x^n}f(x)$$

<!--more-->

#### Differential operator
Before we go any further, let's introduce a less cumbersome notation for differentiation:

$$\frac{\mathrm{d} }{\mathrm{d} x}f(x)=D[f(x)]=Df\\
\frac{\mathrm{d^n} }{\mathrm{d} x^n}f(x)=D^n[f(x)]=D^nf$$

*This is called the [differential operator](https://en.wikipedia.org/wiki/Differential_operator) its used in other fields of calculus. Since all our functions are of one variable ($$x$$) there is no ambiguity in using it. Also note that the operators are not being raised to a power, it's just notation*

Also note that the differential operator also includes antidifferentiation, or integration. The indefinite integral of a function $$f$$ is just:

$$\int{f(x)}\,\mathrm{d}x=D^{-1}[f(x)]=D^{-1}f$$

And further integrals can be defined as you'd expect:

$$\iint{f(x)}\,\mathrm{d}x=D^{-2}[f(x)]=D^{-2}f\\
\iiint{f(x)}\,\mathrm{d}x=D^{-3}[f(x)]=D^{-3}f$$

<!-- ## Halving Operators
Before we get to fractional derivatives, we need to understand what it means to extend an operator to non-integer forms.

#### Exponentiation
Take exponentiation. It is naively defined as repeated multiplication:

$$x^n=\underbrace{x\times x\times x\cdots}_{n\text{ times}}$$

So a number, say 5, to the power of 3 is simply:

$$5^3=5\times 5\times 5=125$$

But what if I plugged in $\frac{1}{2}$ for n? What does it mean to multiply $x$ by itself half a time?

#### Adding Exponents
Let's take a step back to regular exponentiation, the kind with integer exponents. One of the properties of exponentiation is that multiplying two numbers of the same base is the same as adding their exponents together:

$$x^n\times x^m=x^{n+m}$$

This should be clear with an example:

$$x^3\times x^2=(x\times x\times x)\times(x\times x)=x^5$$

So what? Well, if our notion of 'fractional' exponents is to hold we, it should satisfy this property (i.e $x^{1/2}\times x^{1/2}=x^{1/2+1/2}=x$).

This is what we call the **square root** of a number $x$. -->

## Fractional Differentiation
Naturally, one might ask the question "What about derivatives of a non-integer order?" What might such a nonstandard derivative look like? Well, too help us out, let's take a look at a property of derivatives.

$$D^n(D^mf)=D^{n+m}f$$

That is, the $$n$$th derivative of the $$m$$th derivative of a function is equivalent to the $$(n+m)$$th derivative of the function. This should come as no surprise as the definition of the second, third, etc. derivatives are just repeated use of the differential operator:

$$
\begin{align*}
D(Df)=D^2f \tag{Because 1+1=2}\\
D(D^2f)=D^3f \tag{Because 1+2=3}\\
D(D^3f)=D^4f \tag{Because 1+3=4}\\
\end{align*}
$$

*This should remind you of exponents and their properties. As well as the fact that it is not immediately clear what $$x^{1/2}$$ means.*

It should follow that there exists half derivatives, or **semiderivatives**, of functions. This semiderivative has to satisfy the following:

$$D^{1/2}D^{1/2}f=Df \tag{Because 1/2+1/2=1}$$

#### Power Rule
But how do we calculate $$D^{1/2}f$$? Let's assume $$f(x)$$ is some polynomial function. If that's the case we can apply the power rule to find the first and second derivatives:

$$Dx^n=nx^{n-1}\\
D^2x^n=n(n-1)x^{n-2}$$

As we find higher and higher derivatives a pattern emerges:

$$D^kx^n=\frac{n!}{(n-k)!}x^{n-k}$$

*If that wasn't clear, realize that as we successively apply the power rule we multiply the expression by its power then subtract its power by 1 and so on forming a partial factorial. To deal with the fact that these terms don't form a full factorial, we divide by the missing terms which are encapsulated by $$(n-k)!$$*

#### The Gamma Function
This formula works for any integer order derivative but if we attempt to plug, say 1/2, into the expression we're left with:

$$D^{1/2}x^n=\frac{n!}{(n-\frac{1}{2})!}x^{n-\frac{1}{2}}$$

When $$n$$ is an integer, $$n-\frac{1}{2}$$, will always be a rational number. This means we cannot evaluate the denominator because the factorial function $$x!$$ is only defined for integer $$x$$.

But luckily there is a way to amend the factorial function such that it accepts any real (and even complex) numbers. This done by a process known as [**analytical continuation**](https://en.wikipedia.org/wiki/Analytic_continuation), resulting in a *unique* generalized function.

The generalized factorial function is called the [**gamma function**](https://en.wikipedia.org/wiki/Gamma_function) and is denoted: $$\Gamma(x)$$

![gamma graph](/assets/math/fractional-calculus/gamma_function.png?style=centerme)

In the graph above you'll see that the gamma function returns the same result as factorial for integer values, but is shifted over by 1:

$$\Gamma(x+1)=x!\tag{for all integer x}$$

*Why is the gamma function shifted over by 1? Well no particular reason, it's just an unfortunate turn of mathematical history*

There is so much interesting math that makes use of the Gamma Function that I couldn't even hope to touch on it here. For the rest of this article I'll assume you know how to google a ['gamma function calculator'](https://www.wolframalpha.com/input/?i=gamma+(x)) for evaluating it.

#### Fractional Power Rule
We now have all the necessary machinery to derive an expression for fractional (and indeed complex) order derivatives of polynomial functions. It's as simple as replacing the factorial function in our original definition of the power rule with the continuous gamma function:

$$D^kx^n=\frac{n!}{(n-k)!}x^{n-k} \rightarrow \frac{\Gamma(n+1)}{\Gamma(n-k+1)}x^{n-k}$$

*Remember, we added 1 to each of the function's arguments because the gamma function is shifted from factorial.*

And so now we have a general formula for the fractional derivative (or integral if $$k$$ is negative) of any polynomial.

#### An Example
Now we can finally take the semiderivative of a function. Let's start off with a simple one: $$f(x)=x$$

$$\begin{align*}
D^{1/2}x&=\frac{\Gamma(1+1)}{\Gamma(1-1/2+1)}x^{1-1/2}\\
&=\frac{\Gamma(2)}{\Gamma(3/2)}\sqrt x \\
&=\frac{1}{\frac{\sqrt{\pi}}{2}}\sqrt x \\
&=2\sqrt{\frac{x}{\pi}}
\end{align*}$$

Below, we can see the derivative of $$y=x$$ changing between it's first derivative which is just the constant function $$y=1$$ and it's first integral (i.e $$D^{-1}x$$) which is $$y=\frac{x^2}{2}$$

![continuous fractional derivative](https://upload.wikimedia.org/wikipedia/commons/a/ac/Fractional_Derivative_of_Basic_Power_Function_%282014%29.gif?style=centerme)

If we pause this animation at the semiderivative, $$2\sqrt{\frac{x}{\pi}}$$, we get:

![graph of semiderivative of x](https://upload.wikimedia.org/wikipedia/commons/thumb/9/92/Half-derivative.svg/434px-Half-derivative.svg.png?style=centerme)

*In blue is the function $$x$$, in red it's first derivative, $$1$$, and in purple it's semiderivative.*

#### A More **Complex** Example
Let's take a more complex example, the $$(1+i)$$th derivative of $$3x^4$$:

$$\begin{align*}
D^{1+i}3x^4&=\frac{\Gamma(4+1)}{\Gamma(3-(1+i)+1)}3x^{4-(1+i)}\\
&=\frac{\Gamma(5)}{\Gamma(3-i)}3x^{3-i}\\
&=\frac{24}{0.96+1.34i}3x^{3-i}\\
&=(25.48+35.44i)x^{3-i}
\end{align*}$$

Unfortunately, the gamma function of complex numbers aren't usually nice looking. As such, we have to use an approximate value for $$\Gamma{(3-i)}$$.

*If you're wondering how to raise a number to a complex power, I've written about it and other consequences of Euler's formula [here](https://medium.com/@ozanerhansha/applications-of-eulers-formula-857bf60ba32d)*

## Fractional Derivatives of other Common Functions
You may have noticed that the above **fractional power rule** for finding the fractional derivatives of polynomials isn't very general. What about terms with negative exponents (i.e $$x^{-5}$$)? The power rule above doesn't work for them because the gamma function isn't defined for negative integers (it is defined for all other negative real and complex numbers):

![full real gamma function](https://upload.wikimedia.org/wikipedia/commons/5/52/Gamma_plot.svg?style=centerme)

And we haven't even mentioned the fractional derivatives of $$e^{x}$$, $$\sin x$$, and $$\cos x$$...

Deriving the fractional derivatives of these expressions is a lot to cram into one post, so I'll shelve them for now.

<!-- ## Fractional Derivatives of General Functions
What if you wanted to find the fractional/complex derivative of $$\sin x$$? $$e^x$$?, $$\Gamma(x)$$ itself? Well it certainly is possible, and the general formula is as follows:

$$D^{n}f(x)={\frac {1}{\Gamma (1-n)}} \left( \frac{\mathrm{d} }{\mathrm{d} x}\int_{0}^{x}{\frac {f(t)}{(x-t)^{n}}}\,\mathrm{d}t \right)$$

The problem is that the integral part:

$$\int_{0}^{x}{\frac {f(t)}{(x-t)^{n}}}\,\mathrm{d}t$$

Can be quite tricky to evaluate without very advanced techniques. Say we wanted to find the semiderivative of $$\sin x$$:

$$
\begin{align*}
D^{1/2}f(x)&=\frac {1}{\Gamma (1-1/2)} \left(\frac{\mathrm{d}}{\mathrm{d} x}\int_{0}^{x}{\frac {\sin(t)}{(x-t)^{1/2}}}\,\mathrm{d}t \right)
\\
&=\frac {1}{\sqrt\pi} \left(\frac{\mathrm{d}}{\mathrm{d} x}\int_{0}^{x}{\frac{\sin(t)}{\sqrt{x-t}}}\,\mathrm{d}t \right)
\end{align*}
$$

After simplifying the coefficient, we're left with the problem of integrating this expression:

$$\int_{0}^{x}{\frac{\sin(t)}{\sqrt{x-t}}}\,\mathrm{d}t$$

Which I personally cannot do. But that's ok, because others more skilled than I have already solved it for us. Click here for a table of [common fractional derivatives](https://link.springer.com/content/pdf/bbm%3A978-3-642-30898-7%2F1.pdf). -->

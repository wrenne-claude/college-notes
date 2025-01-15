## Derivatives
The tangent line to a curve

After drawing the points on a cartesian plane for a function, after connecting them we can't be certain that that's the final look of your function.
The more points - the closer to the actual state of the graph we are.

let's imagine that points are **little straight intervals**

by stretching one of such points out, we get a straight line:
that line is the $\tan$ to $f(x)$. It's **derived** from the function.

$y=mx+b$ the b decides where the line cuts through y values
$m=\tan\alpha$ => m is the slope.
when $m$ goes to $\infty$ we get a vertical line.
$m=0$ => no slope at all.

slopes to the right are positive, to the left - negative

---
If the following limit exists we call it the **derivative** of $f$ at point $a\in R$.
$$f'\left(a\right)=
\lim_{x\to a} \frac{f(x)-f(a)}{x-a}=
\lim_{\Delta x\to 0} \frac{\Delta f}{\Delta x}=
\lim_{\Delta x\to 0} \frac{f(a+\Delta x)-f(a)}{\Delta x}
$$
+ If the above limit is $\infty$ we denote it by $f'(a)=\infty$
+ If the above limit is $-\infty$ we denote it by $f'(a)=-\infty$
+ If the above limit exists for $x\rightarrow a$, we say that the graph of $y=f(x)$ has a tangent line at $a$.

---
A continuous, nowhere differentiable function.
$$f(x)=\sum^{\infty}_{n=0}a^{n}\cos(b^{n}\pi x), \space \space \space
ab>1+\frac{3}{2}\pi$$
A saw-like function with infinite teeth, e.g. $\sum^{\infty}_{n=0}(\frac{1}{2})^{n}\cos(3^{n}x)$

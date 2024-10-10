# Class 1
Wednesday, 2 October
Krzysztof Borkowski

$log_ab=x$ <==> $a^x=b$
$log_42=\frac{1}{2}$ 

$5^{log_5 77}=77$ 
$log_5 77=x$ 

$a^{log_a x} = x$
$log_a (a^x) = x$

$x^3+4x^2+4x \leq 0$ 
$x(x^2+4x+4) \leq 0$
$x(x+2)^2\leq0$ 
___
### Inverse trigonometric functions
arc sin: $[-1,1]$ -> $[-\frac{\pi}{2}, \frac{\pi}{2}]$ 
arc cos: $[-1,1]$ -> $[0, \pi]$
arc tan: $(-\infty, \infty)$ -> $(-\frac{\pi}{2},\frac{\pi}{2})$ 
arc cot: $(-\infty,\infty)$ -> $(0,\pi)$

$sin\frac{\pi}{6}=\frac{1}{2}$;
$cos\frac{\pi}{6}=\frac{\sqrt3}{2}$;
$sin\frac{\pi}{3}=\frac{\sqrt3}{2}$;
$cos\frac{\pi}{3}=\frac{1}{2}$.

$\arccos(1.4)=y$
$\cos y=1.4$ 

$\arcsin(\sin3\pi)$
$\arcsin(\sin2\pi)$
$\arcsin(\sin\pi)\neq\pi$
$\arcsin(0)=0$

$\sqrt{x^2}=\vert{x}\vert$
$(\sqrt{x})^2=x$  if  $x\geq0$

---
d) $f(x)=\log_{2}(\log_{3}x)$ 
conditions: $x>0$ and $x>1$
$(1;+\infty)$
---
e) $\sqrt[3]{\log_{10}(3x^5+3)}$
$f(x)=3x^5+3$
$g(y)=\log_{10}(y)$
$p(2)=\sqrt[3]2$
---
**10.** Find the indicated composition and determine the natural domain
c) $f(x)=\log_{5}(x+1)$, 
$g(x)=\sqrt{x}$, 
$h(x)=\sin(x-1)$, 
$f(g(h(x)))$,
$h(g(f(x)))$

$x$ -> $\sin(x-1)$ -> $\sqrt{\sin(x-1)}$ -> $\log_{5}(\sqrt{\sin{x-1}+1})$ 
$x$ -> $\log_{5}(x+1)$ -> $\sqrt{\log_{5}(x+1)}$ -> $\sin(\sqrt{\log_{5}(x+1)-1})$

---
# Class 2
Limit of quotient = quotient of limits
$\lim\frac{a_{n}}{b_{n}}=\frac{\lim a_{n}}{\lim a_{n}}$

$\lim\limits_{n\mapsto \infty}f(a_{n})=f(a)$

If the powers are the same, the limit will be a quotient of the coefficients next to the highest powers

b) $a_{n}=\frac{\sqrt{n^{2}+n}+1}{2n}$ write out $a_{2}$ and $a_{2n}$
$a_{2}=\frac{\sqrt{6}+1}{4}$
$a_{2n}=\frac{\sqrt{2n^{2}+2n}+1}{4n}$

d) $a_{k-1}=(k+1)^{k}$ write out $a_{4}$ and $a_{1+n}$
$a_{4}=(5+1)^{5}=6^{5}=...$
$a_{1+n}=((2+n)+1)^{2+n}=(3+n)^{2}*(3+n)^{n}$

Find the limits:
a) $\lim\limits_{k\mapsto\infty}\frac{3k^{1000}+4k^{97}+97k^{4}}{4k^{9997}+97k^{4}}$
$\frac{k^{1000}(3+4\frac{k^{97}}{k^{1000}}+97\frac{k^{4}}{k^{1000}})}{k^{9997}(4+97\frac{k^{4}}{k^{9997}})}=\frac{3+4\frac{k^{97}}{k^{1000}}}{k^{8991}(4+97\frac{k^{4}}{k^{9997}})}$

c) $\lim\limits_{n\mapsto\infty}\arcsin(\log_{e}(e^{\frac{n-1}{n+1}}))$
$\arcsin(\frac{n-1}{n+1})=\arcsin(1)$
$\frac{n(1-\frac{1}{n})}{n(1+\frac{1}{n})}$

f) $\lim\limits_{n\mapsto\infty}\frac{3n}{\sqrt{n^{2}-n}-\sqrt{n^{2}+n}}$
formula $(a-b)(a+b)=a^{2}-b^{2}$  &  $a-b=\frac{a^{2}-b^{2}}{a+b}$
$$\lim\limits_{n\mapsto\infty}\frac{3n}{\sqrt{n^{2}-n}-\sqrt{n^{2}+n}}=
\lim\limits_{n\mapsto\infty}\frac{3n}
{\frac{n^{2}-n-(n^{2}+n)}{\sqrt{n^{2}-n}+\sqrt{n^{2}+n}}}=
\frac{3n}{\frac{-2n}{\sqrt{n^{2}-n}+\sqrt{n^{2}+n}}}=
\frac{3n*(\sqrt{n^{2}-n}+\sqrt{n^{2}+n})}{-2n}$$
---
---
$$\lim\limits_{k\mapsto\infty}
(7^{k}-6^{k}-5^{k})=
\lim\limits_{k\mapsto\infty}7^{k}
(1-\frac{6^{k}}{7^{k}}-\frac{5^{k}}{7^{k}})=\infty$$
Where $\frac{6^{k}}{7^{k}}=(\frac{6}{7})^{k}$

---
**Find the limit(s)**
$$a_{n}=\frac{(n^{4}+4)n!+(n-1)!}{n(n+1)!}$$
$$\lim\limits_{n\mapsto\infty}
\frac{(n^{4}+4)n!+(n-1)!}{n(n+1)!}=
\lim\limits_{n\mapsto\infty}
\frac{(n^{4}+4)n(n-1)!+(n-1)!}{n*(n-1)!*n(n+1)}=
\lim\frac{(n-1)![(n^{4}+4)n+1]}{(n-1)!*n^{2}(n+1)}$$
factorials:
	$n!=1*2*3*...*(n-1)*n$
	$(n-1)!=1*2*3*...*(n-1)$
	$(n+1)!=1*2*3*...*(n-1)n(n+1)$

---
Limit of n-th root of a positive number = 1
e.g. for $8\sqrt[n]{34\frac{1}{2}}$ the limit is 1

---

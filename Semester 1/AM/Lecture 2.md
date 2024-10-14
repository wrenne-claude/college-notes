**Theorem:**
Let $\lim\limits_{n\mapsto\infty}\vert a_{n}\vert=+\infty$,
then $\lim\limits_{n\mapsto\infty}\frac{1}{a_{n}}=0$

Positive and negative infinity
1 over 0^+ means a sequence is pos
1 over 0^- means a sequence is neg and the limit is 0
$$\frac{1}{0^{+}}=+\infty, \frac{1}{0^{-}}=-\infty$$
Theorem:
$$\lim\limits_{n\mapsto\infty}a_{n}=0
\begin{cases}
a_{n}\gt0 \Rightarrow \lim\limits_{n\mapsto\infty}\frac{1}{a_{n}}=+\infty
\\
a_{n}\lt0 \Rightarrow \lim\limits_{n\mapsto\infty}\frac{1}{a_{n}}=-\infty
\end{cases}$$
---
### Rules regarding $[\frac{\infty}{\infty}]$
$$\lim\limits_{n\mapsto\infty}
\frac{a_{m}n^{m}+a_{m-1}n^{m-1}+...+a_{0}}{b_{k}n^{k}+b_{k-1}n^{k-1}+...+b_{0}}=
\left[\frac{\infty}{\infty}\right]=
\begin{cases}
0\space for\space m\lt k \\
\frac{a_{m}}{b_{m}}\space for\space m=k \\
\infty\space for\space m\gt k
\end{cases}$$
$$\lim\limits_{n\mapsto\infty}
\frac{2n^{3}+3n^{2}+4}{5n^{4}+2n+1}\left[\frac{\infty}{\infty}\right]=
\lim\limits_{n\mapsto\infty}\frac
{n^{4}\left(
\frac{2}{n}+3\frac{1}{n^{2}}+\frac{4}{n^{4}}
\right)}
{n^{4}\left(
5+2\frac{1}{n^{3}}+\frac{1}{n^{4}}
\right)}=
\frac{0+0+0}{5+0+0}=0$$
$$\lim\limits_{n\mapsto\infty}
\frac
{2n^{3}+3n^{2}+4}
{5n^{3}+2n+1}
\left[\frac{\infty}{\infty}\right]=
\lim\limits_{n\mapsto\infty}
\frac
{n^{3}\left(2+3\frac{1}{n}+\frac{4}{n^{3}}\right)}
{n^{3}\left(5+2\frac{1}{n^{2}}+\frac{1}{n^{3}}\right)}=
\frac{2+0+0}{5+0+0}=\frac{2}{5}$$
---
$\lim\limits_{n\mapsto\infty}\frac{3^{n}}{n!}=0$  because:
$$0\leq\frac{3^{n}}{n!}=
\frac{3\cdot3\cdot3\cdot...\cdot3}{1\cdot2\cdot3\cdot...\cdot n}\leq\frac{3\cdot3\cdot3}{1\cdot2\cdot3}\cdot
\left(\frac{3}{4}\right)^{n-3}\rightarrow0$$
$\lim\limits_{n\mapsto\infty}\frac{n!}{n^{n}}=0$  because:
$$n\gt1;\space 0\leq\frac{n!}{n^{n}}=
\frac{1\cdot2\cdot3\cdot ...\cdot n}{n \cdot n \cdot n \cdot ... \cdot n}=
\frac{1}{n}\cdot\frac{2\cdot3\cdot ...\cdot n}{n\cdot n\cdot ...\cdot n}\leq
\frac{1}{n}\rightarrow0$$
---
That the form $1^{\infty}$ is indeterminate means that:
If $\lim\limits_{n\mapsto\infty}a_{n}=1$ and $\lim\limits_{n\mapsto\infty}b_{n}=\infty$,
then $\lim\limits_{n\mapsto\infty}a_{n}\space^{b_{n}}[1^{\infty}]=?$ or the limit does not exist.
**NOTE**: The "1" in $[1^{\infty}]$ might NOT be constant =1, but it is a sequence tending to 1, i.e. $a_{n}$
is *close* to 1. If $a_{n}=1$ then, as in the following:
If $a_{n}=1$, then the sequence $a_{n}^{b_{n}}=1$,
so $\lim\limits_{n\mapsto\infty}a_{n}^{b_{n}}=\lim\limits_{n\mapsto\infty}1=1$

---
$$\lim\limits_{n\mapsto\infty}(1+\frac{1}{n})^{n}
\left[1^{\infty}\right]=e$$ ---

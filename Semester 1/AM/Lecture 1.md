Try to understand the lecture --> Use the recommended literature

$N$ = natural numbers = {0,1,2,3,4 ...}
$I$ = integers, whole numbers = {..., -4, -3, -2, -1, 0, 1, 2, 3, 4, ...}
$Q$ = rational numbers = {$\frac{p}{q}:p\in I$ and $q \in N$}
$R$ = real numbers = difficult to define, you **need** calculus. (Defining limits)

Differential calculus
What if we wanted to plot rational numbers on a line?
What if we wanted to put $\sqrt{2}$ on a line?
Real numbers are rational numbers, except we fit in all the wholes as limits.
Our line is continuous (continuity hypothesis) - we don't think of lines filled with holes.

### Infinite sequences
Infinity is **not a number**. It is a useful symbol used to express that some quantities (sequence, function) outgrow any number - grow without bound.

A sequence is a list of numbers written in specified order.

A sequence $f$ is a function:
$f:N$ -> $R$
whose domain is set, or subset, of integers $N$, and the range (codomain) is the set of real numbers.

**Example:**
$a_n = f(n) = \frac{1}{n}$;  i.e $f(x)=1/x$

The function vs. the sequence:
$a_1 = f(1) = \frac{1}{1}$
$a_2=f(2)=\frac{1}{2}$
$a_3=f(3)=\frac{1}{3}$
...
$a_n=f(n)=\frac{1}{n}$

### $arc sin$
$\sin(90^o)=1$ 
$\sin(x^2)=\sin(90^o)^2$ 
degrees of a certain cutout from a circle - length of the arc
arc - angle
$\arcsin(1)=\alpha$ | $\sin(\alpha)=1$
a different notation for $\arcsin$: $sin^{-1}x$
e.g. $\arcsin(x)=\sin^{-1}(x)$ 

### Cartesian coordinates
Sequences can be represented as points in Cartesian coordinates, or as points on a number line.

$a_{n}=(-1)^{n}$  => NO LIMIT



$a_{n}=(-1)^{n+1}\frac{1}{n}$
seq: $1, -\frac{1}{2}, +\frac{1}{3}, -\frac{1}{4}, +\frac{1}{5}, ...$

### Recursive definition
A function defines a sequence and we use a loop
$a_0=const_1, a_2=const_2, ..., a_n=const_n; a_{n+1}=f(a_n,a_{n-1}, ..., a_0);$ 

Recursive definition: $x_{1}=1$, $x_{n}=\cos(x_{n-1})$ 

### Sequence
A sequence ($a_{n}$) tends to the number $L$, which we write
$\lim\limits_{x\mapsto\infty}a_{n}=L$  or  $a_{n}$ -> $\infty$  as  $n$ -> $\infty$
read: the limit of $a_{n}$ as $n$ tends (approaches, goes) to infinity.
Means that terms of $a_{n}$ can get as close to $L$ as we choose

How do we write "$a_{n}$ is close to $L$"?
We set that the distance from $a_{n}$ to $L$ is smaller than $\epsilon$:
$\vert a_{n}-L\vert \lt \epsilon$ 

If the limit of the sequence ($a_{n}$) exists, then we say that the sequence is **convergent**. Otherwise, we say that it's **divergent**.

**A sequence tending to infinity**:
+ i.e. the limit of a sequence is infinity when the sequence increases without a bound. It is not enough for the sequence to be unbounded. Infinitely many terms must always be larger than any chosen number.
+ $\lim\limits_{n\mapsto\infty} a_{n} = \infty$
---
A **subsequence** of the sequence $a_{n}$ is a sequence of the from $a_{x_{n}}$, where the $x_{n}$ are natural numbers with $x_{n} \lt x_{n+1}$ for all $n$.
Intuitively, a **subsequence omits** (loses) some elements of the original sequence.

Let $a_{n}=\frac{1}{n}$, then subsequences are e.g.:
$a_{2k}=\frac{1}{2k}$ all 'even' terms ($\frac{1}{2},\frac{1}{4},\frac{1}{6},...$)
$a_{2k}=\frac{1}{k^{2}}$ terms which are squares ($\frac{1}{1},\frac{1}{4},\frac{1}{9}$)

**Theorem:**
+ A sequence is convergent if and only if **all of its subsequences** converge towards the same limit.
---

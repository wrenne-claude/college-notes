dx - a kind of "right bracket" in antiderivatives

There are many functions whose antiderivatives, even though they exist, cannot be expressed in terms of elementary functions. These functions are called **not elementary integrable** (Liouville Theorem)
$e^{-x^2}$, $\frac{e^x}{x}$, $\sin(x^2)$, $\frac{1}{\ln x}$, $\frac{\sin x}{x}$, $\sqrt{1+x^3}$ 

For example: $\int e^{-x^2}dx$ is calculated using the Gauss Error Function:
$$erf(x) = \frac{2}{\sqrt{\pi}}\int_{0}^{x}e^{-t^2}dt$$

On linearity of an indefinite integral:
1. An integral of a sum equals a sum of integrals
$$\int[f(x)+g(x)]dx = \int f(x)dx + \int g(x)dx$$

Integration by parts:
$$\int f \space dg = f \space g - \int g \space df$$

Homework:
$$\int \cos x \sin x \space dx$$


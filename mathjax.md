---
layout: default
title: MathJax
order: 7
mathjax: true
---

# MathJax

Enable LaTeX math rendering on any page by adding `mathjax: true` to the front matter:

```yaml
---
layout: default
title: My Page
mathjax: true
---
```

MathJax is loaded **only on pages that opt in**, so there is no performance cost on other pages.

## Inline math

Use single dollar signs `$...$` or `\(...\)` for inline equations.

**Markdown:**
```
The quadratic formula is $x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$.
```

**Rendered:**

The quadratic formula is $x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$.

Euler's identity: $e^{i\pi} + 1 = 0$

## Display math

Use double dollar signs `$$...$$` or `\[...\]` for centred display equations.

**Markdown:**
```
$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$
```

**Rendered:**

$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$

## More examples

Maxwell's equations:

$$
\nabla \cdot \mathbf{E} = \frac{\rho}{\varepsilon_0}
\qquad
\nabla \times \mathbf{B} = \mu_0 \mathbf{J} + \mu_0 \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t}
$$

Matrix notation:

$$
A = \begin{pmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{pmatrix}
$$

Summation: the sum of the first $n$ natural numbers is $\displaystyle\sum_{k=1}^{n} k = \frac{n(n+1)}{2}$.

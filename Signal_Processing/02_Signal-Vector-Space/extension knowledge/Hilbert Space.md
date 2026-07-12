---
tags:
---
# Hilbert Space ($\mathcal{H}$)

A Hilbert space is an advanced type of vector space that allows the concepts of geometry (like angles and lengths) to be extended from familiar Euclidean spaces to infinite-dimensional spaces.



## Definition: Hilbert Space

A Hilbert space ($\mathcal{H}$) is a vector space that fulfills two essential criteria:
1. It is equipped with an **inner product**.
2. It is **complete** (it contains no "holes").

## The Inner Product & The "Infinite-Length" Problem

The [[1_Vector-Space#3. Inner product|inner product]] defines a way to multiply two vectors to get a scalar, which allows for the definition of distance, [[Norm-and-Distance|norm (length)]], and [[1_Vector-Space#^a8ccb0|Orthogonality]] z(angles between signals).

### Space Convergence Comparison

| Space | Notation | Convergence | Key Characteristics |
| :--- | :--- | :--- | :--- |
| **Finite Space** | $\mathbb{C}^n$ | Always well-defined. | Uses the conjugate ($x^*$). Always results in a finite value for any two vectors. |
| **Infinite Space** | N/A | **May explode to infinity.** | Simple signals (e.g., the unit step sequence `..., 0, 0, 1, 1, 1, ...`) have an infinite self-inner product. |
| **Square-Summable Space** | $\ell_2(\mathbb{Z})$ | Guaranteed to converge. | Requires the signal to have [[Finite Energy]]. |

### The Solution: $\ell_2(\mathbb{Z})$ Space

To fix the convergence issue with infinite-length signals, we restrict our space to the space of square-summable sequences, denoted as $\ell_2(\mathbb{Z})$. 

> [!MATH] Square-Summable Sequences
> We require sequences to be *square-summable*:
> $$ \sum |x[n]|^2 < \infty $$
> 
> For signals in this space, the infinite sum of the inner product is guaranteed to converge:
> $$ \langle \mathbf{x}, \mathbf{y} \rangle = \sum_{n=-\infty}^{\infty} x^*[n]y[n] $$

> [!WARNING] Important Exclusions
> Because finite energy is required to exist in $\ell_2(\mathbb{Z})$, many important signals are actually **not** in this space. Examples of excluded signals include:
> *   The unit step sequence
> *   Constant signals
> *   Sinusoids

## Completeness ("No Holes")
A vector space is "complete" if it has closure under limits. Every Cauchy sequence of vectors converges to a limit that is also inside the space. Limiting operations must yield vector space elements. This ensures the space doesn't "blow up" or lose signals at its boundaries.

### Key Concepts

| **Concept**              | **Description**                                                                                                                                             |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Closure Under Limits** | If you have an infinite sequence of vectors within the space that converges to a limit, that limit must also exist within the vector space.                 |
| **Formal Definition**    | A sequence of vectors $v_n$ in space $V$ converges to $v$ when for every $\epsilon > 0$, there is an $N$, such that $\|v - v_n\| < \epsilon$, when $n > N$. |
| **Intuition**            | You can think of completeness as a space having no "holes" to fall through when taking limits.                                                              |

### Analogy: The Rational Numbers
The set of rational numbers ($\mathbb{Q}$) is an example of an incomplete space. You can construct a sequence of perfectly rational numbers that converges to an irrational number (like $\sqrt{2}$ or $e$). By taking the limit, you "escape" the rational space and fall through a hole. A complete space prevents this.

> [!MATH] Escaping $\mathbb{Q}$
> 
> As detailed in image_871d42.jpg, we can define a sequence where each term is rational:
> 
> $$ x_n = \sum_{k=0}^n \frac{1}{k!} \in \mathbb{Q} $$
> 
> However, the limit of this sequence falls outside the rational space:
> 
> $$ \lim_{n \to \infty} x_n = e \notin \mathbb{Q} $$

## Key Examples of Hilbert Spaces
Many of the spaces used in signal processing and physics are types of Hilbert spaces. Because they are Hilbert spaces, we know they are complete and have a valid inner product:
- $\mathbb{C}^n$: $n$-dimensional Complex Coordinate Space (finite-length signals).
- $\ell^2(\mathbb{Z})$: The space of square-summable infinite sequences (finite energy discrete-time signals).
- $L^2([a, b])$: The space of square-integrable functions over an interval (finite energy continuous-time signals).
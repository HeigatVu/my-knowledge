---
tags:
  - math
  - vector-space
  - complex-numbers
---
# The Complex Conjugate ($*$)

In mathematics and signal processing, the asterisk symbol ($^*$) denotes the **complex conjugate** of a number, vector, or matrix. *(Note: Some textbooks use an overline like $\overline{z}$ instead).*

## What does it do?
When you apply the complex conjugate to a complex number, you simply **flip the sign of its imaginary component**, while leaving the real component exactly the same.

> [!MATH] Definition
> If we have a complex number $z = a + bi$ (where $a$ is real, $b$ is imaginary, and $i = \sqrt{-1}$):
> $$z^* = a - bi$$

### Quick Examples:
* If $z = 3 + 4i$, then $z^* = 3 - 4i$
* If $z = -2 - 7i$, then $z^* = -2 + 7i$
* If $z = 5$ (a purely real number), then $z^* = 5$ *(real numbers are unaffected)*

## Why is it in the Inner Product axioms?

You will frequently see the conjugate in the **Conjugate Symmetry** axiom:
$$\langle \mathbf{x}, \mathbf{y} \rangle = \langle \mathbf{y}, \mathbf{x} \rangle^*$$

### The "Length" Problem
In standard real numbers ($\mathbb{R}^N$), the inner product is perfectly symmetric: $\langle \mathbf{x}, \mathbf{y} \rangle = \langle \mathbf{y}, \mathbf{x} \rangle$. 

However, in complex spaces ($\mathbb{C}^N$), if we didn't use the conjugate, calculating the length (norm) of a complex vector by taking its inner product with itself ($\langle \mathbf{x}, \mathbf{x} \rangle$) could result in an imaginary number. 

### The Solution
By mathematically forcing the inner product to be *conjugate symmetric*, we guarantee that $\langle \mathbf{x}, \mathbf{x} \rangle$ will **always result in a positive, real number**. 

This allows us to safely calculate physical concepts like:
1. The real **length** of a vector in space.
2. The real **energy** of a continuous signal.

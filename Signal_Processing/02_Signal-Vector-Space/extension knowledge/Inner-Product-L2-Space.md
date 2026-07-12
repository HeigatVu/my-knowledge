---
tags:
  - math
  - vector-space
  - signal-processing
---
# Applications & Intuition in $L_2$ Space

## A. Signal Similarity & Angles
* **Concept:** Measures how "close" two vector signals are to each other.
	* For continuous-time signals (functions) residing in the space of square-integrable functions over a specific interval, such as $L_2[-1, 1]$, the inner product is evaluated using a definite integral rather than a discrete sum.

> [!MATH] Formula: Inner Product in $L_2[-1, 1]$
> $$\langle \mathbf{x}, \mathbf{y} \rangle = \int_{-1}^{1} x(t)y(t) \, dt$$
> 
> **Note:** If these were complex-valued functions rather than purely real ones, you would apply the complex conjugate to the second function, written as $y^*(t)$, to satisfy the Conjugate Symmetry axiom!

* **Geometric Intuition:** Projecting one vector onto another; directly tied to the geometric angle $\theta$ between them.
* **$L_2$ Example:** If a calculation yields an inner product value of $0.78$ (compared to a baseline of $0$), the signals share substantial common characteristics and are **not orthogonal**.
	![[Vector-Space_inner-product-l2.png]]
	![[Vector-Space_inner-product-l2-special-case.png]]

## B. Orthogonality
* **Concept:** Occurs when two vectors are "maximally different" (perpendicular in a generalized sense).
* **Geometric Intuition:** Vectors sit at a strict $90^\circ$ angle relative to each other; their inner product evaluates exactly to zero ($\langle \mathbf{u}, \mathbf{v} \rangle = 0$).
* **Real-World Identifiers:**
  * **Symmetric & Antisymmetric Functions:** The inner product of an even function and an odd function over a symmetric interval equals $0$.
  * **Harmonically Related Sinusoids:** In continuous signal processing, sinusoids of different integer frequencies are completely orthogonal. For example:
    $$\langle \sin(4\pi t), \sin(5\pi t) \rangle = 0$$
    This special orthogonality is the structural pillar underpinning the [[Fourier Series]].

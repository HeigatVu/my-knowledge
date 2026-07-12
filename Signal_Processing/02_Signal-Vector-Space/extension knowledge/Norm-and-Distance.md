---
tags:
  - math
  - vector-space
---
# Norm and Distance: Key Concept Distinctions

> [!WARNING] Crucial Distinction
> It is essential to mathematically separate the definitions of **Norm**, **Distance**, and **Orthogonality**. They describe entirely different structural behaviors.

## Norm (Length)
* **Signal Interpretation:** Measures the total energy or absolute "size" of a signal (linked directly to the **RMS value**).
* **Geometric Intuition:** The physical length of the vector arrow from the origin.
* **Formula:** $\|\mathbf{u}\| = \sqrt{\langle \mathbf{u}, \mathbf{u} \rangle}$
![[Vector-Space_norm.png]]
![[Vector-Space_norm-l2.png]]

## Distance
* **Signal Interpretation:** Measures the "separation" or error between two distinct vector signals.
* **Application:** In $L_2$ spaces, calculating the squared distance between two differing function profiles yields the **Mean Squared Error (MSE)**.
* **Formula:** $d(\mathbf{u}, \mathbf{v}) = \|\mathbf{u} - \mathbf{v}\|$

## Comparison Example: Distance vs. Orthogonality
Consider two vectors in $\mathbb{R}^2$:
$$\mathbf{u} = \begin{bmatrix} 1 \\ 0 \end{bmatrix}, \quad \mathbf{v} = \begin{bmatrix} 0 \\ 100 \end{bmatrix}$$

1. **Orthogonality check via Inner Product:**
   $$\langle \mathbf{u}, \mathbf{v} \rangle = (1)(0) + (0)(100) = 0 \implies \mathbf{\text{Perfectly Orthogonal}}$$
2. **Separation check via Distance Metric:**
   $$d(\mathbf{u}, \mathbf{v}) = \sqrt{(1 - 0)^2 + (0 - 100)^2} = \sqrt{1 + 10000} \approx 100.005 \implies \mathbf{\text{Extremely Far Apart}}$$

This proves that two entities can be completely perpendicular (uncorrelated) while simultaneously being separated by a massive spatial distance.

---
tags:
  - math
  - vector-space
---
# Vector Space

## Definition
- **Challenge** about signal to indicate these finite length, infinite length, periodic, finite support:
	- Each signal type seems to need **different mathematical tools and methods**.
	- Writing separate theories for each would be incredibly complex and inefficient
	==> To solve problem with **vector space to unify framework**
> [!MATH] **Vector Space:** (often over the field of real numbers - $\mathbb{R}$, or complex numbers - $\mathbb{C}$) is a set $V$ whose elements are called **vectors**.

==> This can help use to treat complex signals (like sound or brain waves) using the **same rules for basic geometry**:
- Same framework for different classes of signals (e.g., discrete-time and continuous-time signals).
- Elegant explanation of the Fourier Transform, sampling, and interpolation.
- Mathematical foundation for signal approximation and compression.
- Fundamental in communication system design.

> [!MATH] **Vector** is any mathematical entity that satisfies the formal rules of a **Vector Space.**

---
## Common Vector Spaces

Vector spaces range from intuitive geometric environments to abstract infinite-dimensional spaces used extensively in engineering and physics.

| Category | Space | Name / Description | Domain / Application |
| :--- | :--- | :--- | :--- |
| **Familiar Spaces** | $\mathbb{R}^2, \mathbb{R}^3$ | [[Euclidean Space]] | Geometry, basic physics |
| | $\mathbb{R}^N, \mathbb{C}^N$ | Real / Complex Coordinate Space | Standard [[Linear Algebra]] |
| **Advanced Spaces** | $\ell_2(\mathbb{Z})$ | [[Space of Square-Summable Infinite Sequences]] | Signal processing, discrete systems |
| | $L_2([a, b])$ | [[Space of Square-Integrable Functions]] | Quantum mechanics, Fourier analysis |

> [!TIP] Integration
> All of these spaces are also primary examples of a [[Hilbert Space]], as they are equipped with valid inner products and fulfill the mathematical criteria for completeness.

---
## Operations
A formal vector space $V$ is defined by its ability to perform two fundamental operations while preserving its structure (closure). 
### 1. Vector Addition
Vector addition takes two vectors $u, v \in V$ and produces another vector $u + v$ that remains within the space $V$ ($u + v \in V$).

> [!INFO] Intuition
> * **Signal Definition & [[Superposition]]:** Combining two signals together (e.g., two voices speaking at the exact same time).
> * **Geometric Intuition:** The **"Parallelogram Rule"**—placing vectors tip-to-tail in space.

![[Vector-Space_addition-vector.png]]
![[Vector-Space_addition-l2.png]]
#### Addition Axioms
For all vectors $A, B, C \in V$:
* **Commutative:** $A + B = B + A$ *(order does not matter)*
* **Associative:** $(A + B) + C = A + (B + C)$ *(grouping does not matter)*
* **Zero Element:** $A + 0 = A$ *(adding the zero vector changes nothing)*
* **Additive Inverse:** $A + (-A) = 0$ *(every vector has an equal and opposite vector)*

---
### 2. Scalar Multiplication
Scalar multiplication takes a scalar $c$ from a field (such as the real numbers $\mathbb{R}$ or complex numbers $\mathbb{C}$) and a vector $v \in V$, producing a scaled vector $c \cdot v$ (or simply $cv$) that remains within the space $V$.

> [!INFO] Intuition
> * **Signal Definition:** Changing the amplitude of a signal (e.g., turning up or down the volume knob).
> * **Geometric Intuition:** Stretching or shrinking the vector's length without modifying its underlying directional axis.

![[Vector-Space_multiplication-vector.png]]
![[Vector-Space_multiplcation-l2.png]]
#### Multiplication Axioms
For all vectors $A, B \in V$ and scalars $k, m$:
* **Distributive (Vector):** $k(A + B) = kA + kB$
* **Distributive (Scalar):** $(k + m)A = kA + mA$
* **Associative:** $(km)A = k(mA)$
* **Scalar Identity:** $1 \cdot A = A$ *(multiplying by $1$ changes nothing)*

---
### 3. Inner product
The **inner product** is a mathematical operation that takes two vectors and returns a scalar. It serves as the foundation for defining length, distance, and angles within a [[Hilbert Space]].
#### Mathematical Mapping
Formally, the inner product is a function that maps a pair of vectors to a scalar value:
$$\langle \cdot, \cdot \rangle : V \times V \to \mathbb{C}$$
##### Notation Breakdown
* $\langle \cdot, \cdot \rangle$: The operator placeholder, waiting to accept two vector arguments.
* $V \times V$: The domain, meaning the operation takes two input vectors from the same vector space $V$ (Cartesian product).
* $\to \mathbb{C}$: The codomain, meaning the output of the operation is always a scalar belonging to the field of complex numbers $\mathbb{C}$ (or real numbers $\mathbb{R}$ if the space is purely real).
![[Vector-Space_inner-product-r2.png]]
![[Vector-Space_inner-product-cos.png]]

#### 1. Physical Interpretation of Results

^fdec98

When calculating the inner product $\langle \mathbf{u}, \mathbf{v} \rangle$ of two elements, the resulting scalar value tells us how the vectors relate to one another (often viewed as a measure of similarity or correlation):
* **Large Positive Real Part:** The vectors are **highly correlated** or similar (pointing in a shared direction).
* **Zero ($0$):** The vectors are **completely uncorrelated** or **orthogonal** (perpendicular).
* **Negative Real Part:** The vectors point in **opposite directions** (anti-correlated).

> [!TIP] The Cauchy-Schwarz Inequality
> The magnitude of the inner product is mathematically bounded by the product of the signals' lengths (norms): $|\langle \mathbf{x}, \mathbf{y} \rangle| \le \|\mathbf{x}\| \|\mathbf{y}\|$. This fundamental theorem is the basis for defining the correlation coefficient between two signals, guaranteeing it always falls between -1 and 1.
#### 2. Formal Axiomatic Properties

For vectors $\mathbf{x}, \mathbf{y}, \mathbf{z} \in V$ and scalar $\alpha \in \mathbb{C}$:

| Property | Mathematical Definition |
| :--- | :--- |
| **Additivity** | $$\langle \mathbf{x} + \mathbf{y}, \mathbf{z} \rangle = \langle \mathbf{x}, \mathbf{z} \rangle + \langle \mathbf{y}, \mathbf{z} \rangle$$ |
| **Conjugate Symmetry** | $$\langle \mathbf{x}, \mathbf{y} \rangle = \langle \mathbf{y}, \mathbf{x} \rangle^*$$ |
| **Scalar Multiplication** <br>*(Linear in 1st argument, <br>Conjugate-linear in 2nd)* | $$\begin{align*} \langle \alpha\mathbf{x}, \mathbf{y} \rangle &= \alpha\langle \mathbf{x}, \mathbf{y} \rangle \\ \langle \mathbf{x}, \alpha\mathbf{y} \rangle &= \alpha^*\langle \mathbf{x}, \mathbf{y} \rangle \end{align*}$$ |
| **Positive-Definiteness** | $$\langle \mathbf{x}, \mathbf{x} \rangle \ge 0$$<br>$$\langle \mathbf{x}, \mathbf{x} \rangle = 0 \iff \mathbf{x} = \mathbf{0}$$ |

> [!INFO] Orthogonality Definition
> If $\langle \mathbf{x}, \mathbf{y} \rangle = 0$ and $\mathbf{x}, \mathbf{y} \neq \mathbf{0}$, then $\mathbf{x}$ and $\mathbf{y}$ are called **orthogonal**.

^a8ccb0

---
![[Vector-Space_orthogonoal.png]]
#### Sub-knowledge & Extensions
For deeper dives into these concepts, see the following extension notes:
- **[[Complex-Conjugate|The Complex Conjugate]]**: Why the complex conjugate is used in the inner product and how it works.
- **[[Inner-Product-L2-Space|Applications in L₂ Space]]**: Signal similarity, angles, and orthogonality in $L_2$ space.
- **[[Norm-and-Distance|Norm vs. Distance]]**: Crucial distinctions between Norm (Length), Distance, and Orthogonality.

---
## Signal Space

### Space Definitions

| Space | Notation | Definition | Application | Context |
| :--- | :--- | :--- | :--- | :--- |
| **Standard Space** | $\mathbb{C}^N$ | Length-$N$ tuples (ordered lists) of complex numbers. | Natural home for finite-length [[Discrete-Time Signals]]. | Stating a signal is in $\mathbb{C}^N$ means it is a finite-length discrete-time signal. |
| **Periodic Space** | $\tilde{\mathbb{C}}^N$ | Structurally the exact same mathematical space as $\mathbb{C}^N$. | Used to specifically emphasize the periodicity of the signal. | Differentiates cyclic signals from standard finite signals. |

### Vector Notation

When working in this space, a signal is typically represented as a column vector:

$$ \mathbf{x} = [x_0, x_1, x_2, \dots, x_{N-1}]^T $$

*Note: The $T$ denotes the transpose operation (indicating that this horizontal list is actually a vertical column).*

> [!IMPORTANT] Core Principle
> The same mathematical space can represent completely different types of signals depending on the notation used.

### Inner Product for Signals

> [!MATH] Inner Product Formula of Signals
> $$ \langle \mathbf{x}, \mathbf{y} \rangle = \sum_{n=0}^{N-1} x[n]y^*[n] $$
> 
> *Well defined for all finite-length vectors (i.e., vectors in $\mathbb{C}^N$). The complex conjugate on the second argument ensures that the inner product of a signal with itself yields its real, non-negative **energy**: $\langle \mathbf{x}, \mathbf{x} \rangle = \sum |x[n]|^2$.*

> [!MATH] Infinite-Length Inner Product Formula 
> $$ \langle \mathbf{x}, \mathbf{y} \rangle = \sum_{n=-\infty}^{\infty} x[n]y^*[n] $$

> [!WARNING] Caution Careful: sum may explode!
> Watch example in [[Hilbert Space#1. The Inner Product & The "Infinite-Length" Problem|explode problem and solve solution]]


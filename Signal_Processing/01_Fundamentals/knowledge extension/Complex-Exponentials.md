---
tags:
  - signal
  - complex-exponentials
  - math
---
# Complex Exponentials

### Definition:
- Every oscillation is the projection of a rotation with mathematical description:
	- **Horizontal projection:** $\cos(\omega t)$
	- **Vertical projection:** $\sin(\omega t)$
	- **Example the discrete-time oscillatory heartbeat:** complex exponential $e^{j \omega t}$ $$ \begin{aligned} x[n] &= Ae^{j(\omega n + \phi)} \\ &= A[\cos(\omega n + \phi) + j\sin(\omega n + \phi)] \end{aligned} $$
		- With frequecy $\omega$ (radians)
		- With initial phase $\phi$ (radians)
		- With amplitude $A$ (Strength of oscillation)
		- With sample index $n$ (dimensionless time)
### Why using complex exponentials?
- we can use complex numbers in digital systems
- math is simpler because every sinusoid can be written as a sum of sine and cosine
### The advantages of complex exponentials
- **Example changes the phase of a cosine the "old-school" way** $$\cos(\omega n + \phi) = a \cos(\omega n) - b \sin(\omega n), \quad a = \cos \phi, \quad b = \sin \phi$$
	- Must remember complex trigonometric formulas
	- Carry more terms in equations
- **Example: change the phase of a pure cosine with complex exponentials**
$$\cos(\omega n + \phi) = \text{Re}\{e^{j(\omega n + \phi)}\} = \text{Re}\{e^{j\omega n} e^{j\phi}\}$$

> [!info] Understanding the Real Part ($\text{Re}$) Operator
> * **Definition:** $\text{Re}\{\dots\}$ extracts only the **Real Part** of a complex number or function, discarding the imaginary component.
> * **Euler's Connection:** Since $e^{j\theta} = \cos(\theta) + j\sin(\theta)$, taking the real part leaves you with just the cosine:
>   $$\text{Re}\{e^{j\theta}\} = \cos(\theta)$$
> * **Application:** In signal processing, it is mathematically cleaner to manipulate phase shifts using complex exponentials ($e^{j\omega n} e^{j\phi}$) and apply $\text{Re}$ at the end to recover the real-world cosine signal.
> ![[Signal-Fundamentals_complex-exponential.png]]
> ![[Signal-Fundamentals_complex-exponential-rotation.png]]

> [!warning] Not every sinusoid is periodic in discrete time
> ![[Signal-Fundamentals_complex-exponential-generating-machine.png]]
> ![[Signal-Fundamentals_warning-sinusoid.png]]
> #### Condition for Periodicity
> A discrete-time complex exponential $e^{j\omega n}$ is periodic in $n$ if and only if its angular frequency $\omega$ is a rational multiple of $2\pi$:
> $$e^{j\omega n} \text{ periodic in } n \iff \omega = \frac{M}{N}2\pi, \quad M, N \in \mathbb{N}$$
> #### Mathematical Proof / Derivation
> For a discrete signal to be periodic with a fundamental integer period $N$, it must satisfy $x[n] = x[n + N]$:
> $$
\begin{aligned}
e^{j(\omega n + \phi)} &= e^{j(\omega(n + N) + \phi)} \\
e^{j\omega n}e^{j\phi} &= e^{j\omega n}e^{j\omega N}e^{j\phi} \\
e^{j\omega N} &= 1 \\
\omega N &= 2M\pi, \quad M \in \mathbb{Z} \\
\omega &= \frac{M}{N}2\pi
\end{aligned}
$$

> [!tip] Key Takeaway
> Unlike continuous-time signals $\cos(\Omega t)$, which are *always* periodic for any value of $\Omega$, a discrete-time signal $\cos(\omega n)$ is only periodic if you can find an integer number of cycles $M$ that fit exactly into an integer number of samples $N$. If $\frac{\omega}{2\pi}$ is an irrational number, the signal never perfectly repeats itself.

**---> sine and cosine "live" together, simple multiplication, and simpler notation**

---
tags:
  - basic-digital-signal
  - complex-exponential
  - discrete-time
  - quantization
---
# Discrete-Time Signals & Digital Signals

This note covers the mathematical and structural specifics of digital signals, building upon the basic definitions in [[Signal-Fundamentals]].

## Discrete Time (Sampling)

A discrete-time signal is a sequence of complex numbers (one-dimensional).

- **Notation:** $x[n]$, where brackets `[]` indicate an integer index.
- **Domain:** Two-sided sequences map from $\mathbb{Z} \to \mathbb{C}$.
- **Index $n$:** It is a dimensionless "time" counter. It simply sets an order on the sequence of samples, rather than representing a physical unit like seconds.
- **Operations:**
  - **Analysis:** Periodic measurement.
  - **Synthesis:** Stream of generated samples.

> [!info] The Bridge: [[Sampling-Theory|Sampling Theory]]
> - **Philosophical angle:** Modeling time as either continuous or discrete depends on the application.
> - **Zeno's paradox:** Modern calculus shows that infinite sums can converge to finite values, relevant for taking infinite samples to discrete numbers.
> - **Practicality:** Discrete-time models are computationally tractable (simple sums vs. complex integration).

### Types of Discrete-Time Signals

1. **Delta Signal (Unit Impulse / Kronecker Delta):** Equals 1 at $n=0$, and 0 everywhere else. The discrete-time equivalent of the Dirac delta.
   ![[Signal-Fundamentals_delta-signal.png]]
2. **Unit Step:** Equals 0 for $n<0$, and 1 for $n \ge 0$. Represents a signal that "turns on" at $n=0$.
   ![[Signal-Fundamentals_unit-step.png]]
3. **Exponential Decay:** Decays when $|a|<1$, grows when $|a|>1$. Real exponentials are common for **modeling system responses**.
   - *Example:* Newton's Law of Cooling (how fast coffee gets cold):
     $$ \frac{dT}{dt} = -c(T - T_{\text{env}}) \implies T(t) = T_{\text{env}} + (T_0 - T_{\text{env}})e^{-ct} $$
   ![[Signal-Fundamentals_exponential-decay.png]]
4. **Sinusoid:** Real-valued oscillating signal, fundamental for frequency representation.
   ![[Signal-Fundamentals_sinusoid.png]]

### Signal Classes

- **Finite-length:** Sequence $x[n]$ for $n = 0, \dots, N-1$. Vector notation: $\mathbf{x} = [x_0, x_1, \dots, x_{N-1}]^T$. Good for numerical packages.
- **Infinite-length:** Sequence $x[n]$ for $n \in \mathbb{Z}$. Abstraction good for theorems.
- **Periodic:** $N$-periodic sequence $\tilde{x}[n] = \tilde{x}[n + kN]$. Natural bridge between finite and infinite.
- **Finite-support:** $\bar{x}[n] = x[n]$ for $0 \le n < N$, else $0$. Another bridge.

### Elementary Operators (Finite-Length)

- **Scaling:** $y[n] = \alpha x[n]$
- **Sum:** $y[n] = x[n] + z[n]$
- **Product:** $y[n] = x[n] \cdot z[n]$
- **Shift (Delay):** $y[n] = x[n - k]$
  - *Finite-support:* ![[Signal-Fundamentals_shift-finite-support.png]]
  - *Periodic extension:* ![[Signal-Fundamentals_shift-length-periodic.png]]

---

## Discrete Amplitude (Quantization)

- **Definition:** The signal's value at each sampling instant is quantized to take on a finite number of values.
- **Process:** Converts continuous voltage levels to discrete digital values.
- **Meaning:** 
  - Converts a continuous range into a finite set of discrete levels.
  - **Countability:** The possible amplitude values become countable, mapping each level to an integer.
  - **Binary representation:** Integers are represented in binary (0s and 1s), which is the foundation of digital systems (storage, standard processing algorithms, and lossless transmission).

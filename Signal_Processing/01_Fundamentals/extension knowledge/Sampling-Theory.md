---
tags:
  - sampling
  - discrete-time
  - reconstruction
  - information-theory
---
# Sampling Theory

![[Sampling-Theory_overview.png]]

> [!abstract] Core Idea
> Under certain conditions, a continuous-time signal can be perfectly reconstructed from its discrete-time samples. This is a profound and non-intuitive result.

## The Reconstruction Function

> [!example] Mathematical Formula
> $\text{Continuous Signal} = \sum (\text{Samples} \times \text{sinc functions})$
> $$x(t) = \sum_{n=-\infty}^{\infty} x[n] \operatorname{sinc}\left(\frac{t - nT_s}{T_s}\right)$$

- **$x(t)$**: The reconstructed continuous-time signal.
- **$x[n]$**: The signal value at discrete time point $n$.
  - $n$ is dimensionless; it's simply an ordering index (1st sample, 2nd sample, etc.).
  - Square brackets `[n]` indicate discrete-time, while parentheses `(t)` indicate continuous-time.
- **$\operatorname{sinc}(\cdot)$**: The `sinc` function acts as the ideal interpolation filter. It shifts and scales by the value of the discrete time sequence.

**Intuition:** Each sample is "spread out" in time using the `sinc` function, and these spread-out versions are added together to reconstruct the original continuous signal.

![[sampling-Theory_Sampling-sinc-reconstruction.png|Sampling sinc reconstruction]]
*(Note: This image represents one time point $t$)*

### Example: Continuous to Discrete and Vice Versa

1. **Discretize:** We sample the original continuous signal into discrete points.
   ![[sampling-Theory_Sampling-continuous-to-discrete.png|Continuous to discrete sampling]]
2. **Calculate:** We calculate the `sinc` interpolation at each time point.
   ![[sampling-Theory_Sampling-per-point-calculation.png|Per-point calculation]]
3. **Reconstruct:** After calculating all time points, we sum them up to perfectly reconstruct the original result.
   ![[sampling-Theory_Sampling-final-reverse-reconstruction.png|Final reverse reconstruction]]

---

## Nyquist-Shannon Sampling Theorem

> [!def] The Theorem
> A **bandlimited signal** can be perfectly reconstructed if the sampling rate is greater than twice its bandwidth. This minimum required sampling rate is called the **Nyquist rate**.

### Key Concepts

- **Bandlimited:** A signal whose frequency content is limited (its Fourier Transform is zero above a certain frequency, called the bandwidth). This is a crucial assumption.
  ![[Sampling-Theory_bandlimited.png]]
  
- **Bandwidth ($f_{max}$):** The range or the width of the frequency (the highest minus the lowest frequency).
  ![[Sampling-Theory_bandwidth.png]]
  
- **Sampling Rate ($f_s$):** The number of samples taken per second, measured in Hertz (Hz).
  ![[Sampling-Theory_sampling-rate.png]]
  
- **Nyquist Rate:** The absolute minimum sampling rate required to avoid aliasing.
  $$f_s \ge 2 \cdot f_{max}$$

---

## Aliasing

> [!warning] What is Aliasing?
> If the sampling rate is **less** than the Nyquist rate, aliasing occurs. High-frequency components in the original signal are "folded" down to lower frequencies, permanently distorting the reconstructed signal.

**Real-world Examples:**
- **Audio:** A strange, low-frequency "whine" in poorly recorded digital audio.
- **Video:** The "wagon-wheel effect" in movies, where a fast-spinning car wheel or helicopter rotor appears to be spinning slowly backward. This happens because the camera's frame rate (its sampling rate) is too slow to correctly capture the rapid motion.

---

## Related Notes
- **Signal Types:** See [[Signal-Fundamentals#Types of Signals|Signal Fundamentals]] for analog vs. digital comparisons.
- **Hardware Conditioning:** See [[Operational-Amplifiers|Operational Amplifiers]] for hardware-side signal conditioning *before* sampling occurs.

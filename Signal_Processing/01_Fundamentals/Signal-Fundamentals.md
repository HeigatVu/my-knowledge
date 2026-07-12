---
tags:
  - signal
  - type-of-processing
  - type-of-signal
---
# Signal Fundamentals

## What is a Signal?

> [!def] Definition
> A signal is a description of the evolution of a physical phenomenon. Mathematically, it is a function that represents the variation of a physical quantity over time, space, or another independent variable.

- **Mathematical Function:** This emphasizes the mathematical nature of a signal. It's a precise mapping from an independent variable (like time) to a value (like temperature, pressure, voltage, etc.).
- **Physical Quantity:** The signal represents a measurable property of the physical world.
- **Variation:** Signals encode change. A constant value carries little information; the changes convey meaning.
- **Independent Variable:** Highlights that the variation is with respect to a specific dimension (e.g., time, space).
## Types of Processing
### Analysis
Extracting meaningful information from a signal. This often involves transforming the signal (e.g., to the frequency domain), filtering it, or detecting patterns.
- **Examples:**
  - **Speech Processing:** Understanding the information carried by a speech signal (identifying phonemes, recognizing words, determining the speaker's emotion).
  - **Neuroscience:** Analyzing an EEG signal to identify periods of sleep or detect epileptic seizures.
### Synthesis
Creating a signal to convey specific information.
- **Examples:**
  - **Telecommunications:** Transmitting information via a cell phone or radio, where voice or data is encoded into a signal for transmission over airwaves.
  - **Neuroscience:** Stimulating a specific region with an electrode to evoke a particular behavior or sensation (deep brain stimulation).
  - **Audio:** Creating music with a synthesizer.
## Types of Signals
### 1. Analog Signals
Signals that are **continuous** in both time and amplitude. They are described by functions of a real variable (e.g., $f(t)$ where $t$ can take on any real value).

> [!warning] Challenges with Analog Signals
> - They often require specialized hardware devices for recording and manipulation.
> - There isn't a universal way to handle all analog signals flexibly.
### 2. Digital Signals
Signals that are **discrete** in both time and amplitude. 
> [!info] Dive Deeper
> To see exactly how we represent and calculate digital signals, please check:
> - ➡️ [[Discrete-Time-Signals|Discrete Time Signal]] (Sampling, Quantization, and Math Operators)
> - ➡️ [[Sampling-Theory|Sampling Theory]] (How we bridge Analog and Digital)

---
## Signal Metrics
How do we measure the "size" or strength of a signal? We use Energy and Power metrics.
> [!info] Dive Deeper
> - ➡️ [[Energy-and-Power-Signals|Energy and Power Signals]] for the mathematical formulas.

---
## Basic Signal Processing
> [!info] Dive Deeper
> - ➡️ [[Basic-Signal-Processing|Basic Signal Processing]] for fundamental building blocks and system types.

---
## Complex Exponentials
Understanding the mathematics of oscillations and rotations is crucial in digital systems. We use complex exponentials to make math simpler and represent discrete-time periodic signals cleanly.

> [!info] Dive Deeper
> - ➡️ [[Complex-Exponentials|Complex Exponentials]] (Mathematical representations, periodicity in discrete time, Euler's connection)

---
## Aliasing
When converting analog signals to digital, we encounter the "Speed Limit of Discrete Time". If a signal oscillates too fast for the sampling rate, high frequencies will "alias" or masquerade as lower frequencies.

> [!info] Dive Deeper
> - ➡️ [[Aliasing|Aliasing]] (Nyquist frequency, aliased frequencies, and visual examples)

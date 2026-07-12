---
tags:
  - signal
  - basic-signal-processing
---
# Basic Signal Processing

### Definition about difference between [[Discrete-Time-Signals|Discrete time]] and Physical world:
#### Discrete time
- n: no physical dimension (just a counter)
- periodicity: how many samples before pattern repeats
#### Physical world
- periodicity: how many seconds before pattern repeats
- frequency meansured in Hz $(s^{-1})$
#### Example about How do you make a digital computer (works with numbers) talk to the analog world (continuous physical phenomena)?
How do you make a digital computer (works with numbers) talk to the analog world (continuous physical phenomena)?

- **Problem definition:**
	- **Computer (Discrete Number Requirement):** need discrete-time sequence $x[n] = \sin(\omega_0 n + \theta)$
		![[Signal-Fundamentals_sinusoid-1.png]]
	- **Human ear (Physical world):** Need continuous pressure waves in air
- **Solution:** Sound card to interpret discrete signal
		![[Signal-Fundamentals_how-speaker-work.png]]
	- **Digital-to-Analog Converter (DAC):**
		- **Input:** Discrete samples $x[n]$
		- **Output:** Continuous voltage signal
		- **System clock:** Takes new samples every $T_s$ seconds
			- **Function:** Determines time in seconds between samples
			- **Period:** $T_s$ seconds (physical time) 
				==> periodicity of M samples -> periodicity of $M*T_s$ seconds
				--> Real world frequency: $f = \frac{1}{MT_s}\text{ Hz}$
			- **Typical Value:** $T_s$ = 20.8 $\mu s$ (for 48 $kHz$ sampling)$$ \begin{array}{rcccc} \textbf{Digital Domain:} & x[0] & x[1] & x[2] & x[3] & \dots \\ & \downarrow & \downarrow & \downarrow & \downarrow & \\ \textbf{Physical Time:} & t=0 & t=T_s & t=2T_s & t=3T_s & \dots \\ & \downarrow & \downarrow & \downarrow & \downarrow & \\ \textbf{Analog Output:} & V(0) & V(T_s) & V(2T_s) & V(3T_s) & \dots \end{array} $$
				- We choose $F_s$ as the number of samples per seconds: $T_s= \frac{1}{F_s}$

#### Example Problem
A music song has a duration of 2 minutes and a sampling frequency of $f_s = 44100\text{ s}^{-1}$. How many samples does it contain?

| **Step / Parameter**      | **Value / Formula**                    | **Note**                                                                |
| ------------------------- | -------------------------------------- | ----------------------------------------------------------------------- |
| **Duration ($t$)**        | 2 minutes                              | Convert to seconds: $2 \times 60 = 120\text{ s}$                        |
| **Sampling Rate ($f_s$)** | $44100\text{ s}^{-1}$                  | 44,100 samples per second                                               |
| **Proportion**            | $1\text{ s} \to 44100 \text{ samples}$ | Baseline rate                                                           |
| **Total Samples**         | $120 \to ?$                            | $120\text{ s} \times 44100\text{ samples/s} = 5,292,000\text{ samples}$ |
#### Fundamental building blocks
- **Definition:** Complex systems are built from simple, and reusable components
- **Blocks:**
	- **Adder: $y[n] = x_1[n] + x_2[n]$**
		- **Function:** Combines two signals
		- **Symbol:** $\oplus$ or +
			![[Signal-Fundamentals_adder.png]]
	- **Multiplier: $y[n] = \alpha * x[n]$** 
		- **Function:** Scales signal amplitude
		- **Symbol:** Triangle with $\alpha$
			![[Signal-Fundamentals_multiplier.png]]
	- **Unit Delay $(z^{-1})$:** 
		- **Function:** $y[n] = x[n-1]$ (unit delay) to memory/storage element
		- **Symbol:** Rectangle with $z^{-1}$
			![[Signal-Fundamentals_unit-delay.png]]
			
	- **Abitrary Delay:**
		- **Function:** $y[n] = x[n-M]$ (M-sample delay) to memory/storage element
		- **Symbol:** Rectangle with $z^{-M}$
			![[Signal-Fundamentals_arbotrary-delay.png]]
#### Type of System
- **Moving average (feed-forward system):**
	- **simple average:** $m = \frac{a + b}{2}$
	- **moving average:** take a "local" average: $y[n] = \frac{x[n] + x[n - 1]}{2}$
	- **Application:** Smooths signals by averaging current and previous samples
		![[Signal-Fundamentals_moving-average-dsp.png]]
		![[Signal-Fundamentals_example-moving-average.png]]
		![[Signal-Fundamentals_example-moving-average-2.png]]
- **Recursion (feed-back system):**
	- **One time recursion:**
		- **Function:** $y[n] = x[n] + \alpha * y[n-1]$ -> Output $y[n]$ depends on previous output (not just previous input)
		- **Example:** Banking problem with building block
			![[Signal-Fundamentals_bank-problem-disscription.png]]
			![[Signal-Fundamentals_banking-problem-image.png]]
			![[Signal-Fundamentals_banking-problem-num-application.png]]
	- **More time recursion loop (the Karplus-Strong Algorithm):**
		- **Function:** $y[n] = \alpha * y[n - M] + x[n]$
		- **Example: With Unit Impulse**
			![[Signal-Fundamentals_more-loop-example.png]]
			![[Signal-Fundamentals_more-loop-example-1.png]]
		- **Application in music:**
			- build a recursion loop with a delay of $M$ -> To control frequency (pitch)
			- choose a signal $\bar{x}[n]$ that is nonzero only for $0 \le n < M$ 
			- choose a decay factor $\alpha$ -> To control envelope (decay)
			- input $\bar{x}[n]$ to the system  -> To control color (timbre)
			- play the output
			- **Example with sine wave:**
				![[Signal-Fundamentals_music-sine-wave.png]]
			- **Example with proto-violin:**
				![[Signal-Fundamentals_music-proto-violin.png]]
			- **Example with Karplus-Strong Algorithm:**
				![[Signal-Fundamentals_music-karplus-strong-algorithm.png]]
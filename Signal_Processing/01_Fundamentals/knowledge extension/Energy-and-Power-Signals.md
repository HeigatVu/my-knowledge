---
tags:
  - signal-energy
  - signal-power
---
# Energy and Power Signals

These formulas represent ways to quantify the "size" or strength of a signal over time. See [[Signal-Fundamentals]] for basic signal context.

## Energy Signal

The total energy of a discrete-time signal $x[n]$ is defined as:
$$E_x = \sum_{n=-\infty}^{\infty} |x[n]|^2$$

- For periodic signals, the total energy over all time is infinite: $E_{\tilde{x}} = \infty$.
## Power Signal

The average power of a discrete-time signal $x[n]$ is defined as:
$$P_x = \lim_{N\to\infty} \frac{1}{2N+1} \sum_{n=-N}^{N} |x[n]|^2$$

- For periodic signals, the average power can be calculated over a single period $N$:
  $$P_{\tilde{x}} \equiv \frac{1}{N} \sum_{n=0}^{N-1} |\tilde{x}[n]|^2$$
## Example:
Given

$$
x[n] =
\begin{cases}
(-1)^n n, & n = 1,2,3 \\
0, & \text{otherwise}
\end{cases}
$$

and

$$
y[n] = \sum_{k=-\infty}^{\infty} x[n+7k]
$$

So, \(y[n]\) is periodic with period \(7\):

$$
y[n] = \{0, -1, 2, -3, 0, 0, 0\}
$$ 
repeated every \(7\) samples.

---
### a) Compute the energy of \(x[n]\)
$$
E_x = \sum_{n=-\infty}^{\infty} |x[n]|^2
$$
Since \(x[n]\) only has non-zero values at \(n = 1,2,3\):
$$
x[1] = -1, \qquad x[2] = 2, \qquad x[3] = -3
$$
Therefore:
$$
E_x = |-1|^2 + |2|^2 + |-3|^2
$$
$$
E_x = 1 + 4 + 9 = 14
$$
So:
$$
\boxed{E_x = 14}
$$

---

### b) Compute the power of \(x[n]\)
$$
P_x =
\lim_{N \to \infty}
\frac{1}{2N+1}
\sum_{n=-N}^{N} |x[n]|^2
$$
Since \(x[n]\) has finite energy:
$$
P_x =
\lim_{N \to \infty}
\frac{14}{2N+1}
$$
$$
P_x = \frac{14}{\infty}
$$
So:
$$
\boxed{P_x = 0}
$$
---
### c) Compute the energy of \(y[n]\)
$$
E_y =
\sum_{n=-\infty}^{\infty} |y[n]|^2
$$
Because \(y[n]\) is periodic and non-zero, its energy is infinite:
$$
E_y = \infty
$$
So:
$$
\boxed{E_y = \infty}
$$
---
### d) Compute the power of \(y[n]\)

The power of \(y[n]\) is
$$
P_y =
\lim_{N \to \infty}
\frac{1}{2N+1}
\sum_{n=-N}^{N} |y[n]|^2
$$
Since \(y[n]\) is periodic with period \(7\), the signal repeats the same energy every period.
The energy in one period is
$$
E_x = 14
$$
Assume there are \(M\) complete periods inside the interval \([-N,N]\).  
Then the total energy inside the interval is approximately
$$
M \cdot E_x
$$
Therefore:
$$
P_y =
\lim_{N \to \infty}
\frac{M \cdot E_x}{2N+1}
$$
Because the period of \(y[n]\) is \(7\), the number of complete periods is approximately
$$
M =
\frac{2N+1}{7}
$$
Substitute this into the power formula:
$$
P_y =
\lim_{N \to \infty}
\frac{
\frac{2N+1}{7} \cdot E_x
}{
2N+1
}
$$
Cancel \(2N+1\):
$$
P_y =
\frac{E_x}{7}
$$
Since
$$
E_x = 14
$$
we get
$$
P_y =
\frac{14}{7}
$$
So
$$
\boxed{P_y = 2}
$$
---
tags:
  - signal
  - aliasing
---
# Aliasing

### Definition
- The Speed Limit of Discrete Time
- **One point with many names**
- Example: with name $2 \pi$ and $-2 \pi$ in the same points
	![[Signal-Fundamentals_2-pi-name.png]]
	![[Signal-Fundamentals_negative-2-pi.png]]
> [!tip] Key Takeaway
> The highest frequency = 2π
> => Following Nyquist frequency -> we only see half sampling rate (0,π)
> => if frequency between (π, 2π) -> we can see backward (aliased frequencies)
> True speed: 30°/frame → Appears: 30°/frame forward
> True speed: 90°/frame → Appears: 90°/frame forward
> True speed: 180°/frame → Appears: 180°/frame forward ← Maximum!
> True speed: 270°/frame → Appears: 90°/frame backward ← Aliasing starts!
> True speed: 360°/frame → Appears: 0°/frame forward → Wheel appears STATIONARY!
> True speed: 450°/frame → Appears: 90°/frame forward
> True speed: 540°/frame → Appears: 180°/frame forward
> True speed: 630°/frame → Appears: 90°/frame backward
> True speed: 720°/frame → Appears: 0°/frame forward

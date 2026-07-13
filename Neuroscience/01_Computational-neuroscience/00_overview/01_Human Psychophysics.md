---
tags:
---
## Definition:
- The analysis of perceptual processes by studying the effect on a subject's experience or behavior of systematically varying the properties of a stimulus along one or more physical dimensions.
	--> Research about relationship between stimulus and sensation
- This role of research is to precise measurement of perception 
## Example of research type:
-  **Contrast sensitivity and details:**
	- What colors a human being can perceive?
	- How far from the television I expect to be sitting (watching TV)?
	- Would get physically with an 8K TV or will it fact be imperceptible to human given them visual system?
		![[Human Psychophysics_constrast-sensitivity.png]]
		--> This can answer about pixel density (as in image above cannot perceive difference between two images until zooming out), viewing distance, television size, and so on for human or customers.
- **Trichromacy:** this research about synthesizing three primary colors to create color diversity and modern screen based on psychophysic to study about human color perception.
		![[Human Psychophysics_trichromacy.png]]
	- In fact, psychophysists had tried to work colour-matching experiment to predict the existence and approx sensitivities of these mechanisms before physiologists directly meansured the cone types in retina system.
		![[01_Human Psychophysics_phsyiology-trichrromacy.png]]
- **Weber-Fechner law:**
	- **Just Noticeable Difference (JND):** is a smallest weight that can add until participants are able to notice an increase in heaviness. *In other words,*  a person holds a 20g weight -> adding 1g -> if the person can detect the increase, the JND approx 1g under that condition
		- Example: JND for weight is 5%: 
			- 20g vs 21g -> just noticeable
			- 100g vs 101g -> not noticeable
			- 1000g vs 1050g -> just noticeable
	--> Weber found that Just Noticeable Difference was a constant fraction of baseline 
	$$\Delta S = kS$$
			Where:
				S: baseline stimulus intensity
				$\Delta S$: JND
				k: Weber fraction
			For example: $k = 0.05$:

				| Baseline $S$ | JND $\Delta S$ |
				| :----------: | :------------: |
				|     20 g     |      1 g       |
				|    100 g     |      5 g       |
				|   1,000 g    |      50 g      |
		
	![[01_Human Psychophysics_weber-fechner-law-baseline.png]]
		
	--> Weber also gave a assumption about constant perceived sensation:
		$$\Delta P = constant$$
		And internal signal is monotonically related to the underlying stimulus intensity (weber fraction)
		$$\Delta P \propto k => \Delta P \propto \frac{\Delta S}{S}$$
		In order to have an equation -> add constant value c indicate propotion of two quatities:
		$$\Delta P = c \frac{\Delta S}{S}$$
		Continuous form
		$$dP = c \frac{dS}{S}$$
		Prove logarithmic encoding:
		$$dP = c \int_{S_0}^S \frac{1}{S} dS$$
		With: $\int \frac{1}{S} dS = \ln(S)$
		$$dP = c (\ln(S) - \ln(S_0))  + C => dP = c \ln\frac{S}{S_0}  + C$$
		![[01_Human Psychophysics_weber-fechner-law-log.png]]
		==> We can see that a heavier weight, we need a larger external change to create the same internal change

## How to do Psychophysics:
### Step 1: Detecting task with question:
- Example: What is the minimum detectable amount of light? or how much light do we need to see?
	![[01_Human Psychophysics_example-detection-task.png]]
### Step 2: Design experiment
- "Yes/No" design
	- Example: 
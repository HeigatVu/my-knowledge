---
tags:
---
## Mind:
- Ideas and purposes
- Ability to find invariances and spot regularities
- Algorithms, and instruction sets

## Brain:
- Material thing and processes
- Physical, chemical, structure of the brain
- Physiology of the brain
- Dynamics
	![[Introduction_neuroscience.png]]
- Functional localization:
	![[Introduction_functional-localization.png]]
- Subcortical regions:
	![[Introduction_subcortical-regions.png]]
- Hardware of the brain:
	- **Neuron:**
		- **Structure of neuron**
			![[Introduction_neuron.png]]
		- **Type of neuron (neuron diversity)**
			![[Introduction_neuron-variance.png]]
	- **Synapses (connection):**
		- **Electrical synapses (connection)**
		- **Chemical synapses (connection)** -> Release of neurotransmitter by pre-synaptic neuron connecting with receptors on post-synaptic neuron
			![[Introduction_chemical-synapses.png]]
				- Positive deflection (excitatory reponse)
			- Negative deflection (inhibitory reponse)
				![[Introduction_excitatory-inhibitory.png]]
				-> **Dale's Dogma** means that each neuron will make either excitatory or inhibioty synapses 
- Brain's connectivity (how does the brain wire):
	- The main organization of brain matching with current GPU:
		Neocortex -> Cortical region -> Macrocolumn -> Miniolumn -> Neuron
		**Question: if we match each part of brain with GPU, should we choose neocortex equals GPU or neocrotex equals a system of GPUs**
		![[Introduction_neocortex-vertical-connectivity.png]]
	- Based on image from left to right, it will show
		- **Cortical sheet (cortex):** is a thin, folded outer layer of the brain
			- 1 cortical sheet has approx 2 million macrocolumns, 200 million microcolumns, and 20 billion neurons
				--> This shows that brain is not a consistent mass, it contains various repeated local network to process excitation from environment
		- **Macrocolumn:** is vertical block of cortical layer (repeating processing unit of the brain's cortex), including 6 layers. 1 macrocolumn has approx 100 microcolumns, and 10,000 neurons
		- **Minicolumn:** is a vertical group of neurons, 1 minicolumn has about 100 neurons
	- Overview about how the neocortex processes (the right diagram of image):
		- As in macrocolumn has 6 layers (vertical connectivity) and they are grouped into:
			- Layer 2/3
			- Layer 4
			- Layer 5/6
			- Layer 1???
			- With other type of neuron:
				- **EXC:** excitatory neurons
				- **IN:** inhibitory neurons
		- Basic flow on described image:
			External input -> layer 4 -> layer 2/3 -> layer 4/5 -> other brain regions
			- Feedforward connection: 
			- Feedback connection:
		- Each neuron also has horizontal connectivity as image:
			![[Introduction_neocortex-horizontal-connectivity.png]]
			--> We can see the rule that neuron will create more connection with nearby neuron and more patchy connectivity when it is far from soma **=> Distance-depent pattern**
		- Different areas of neocortex also connect with the others
			![[Introduction_neocortex-cross-cortical-area.png]]
- Network of networks bases on previous analyzed connection:
	![[Introduction_brain-network.png]]
	- a
- Brain function experiment design:
		![[Introduction_brain-function-study.png]]
	- Based on this image we have three types of brain research:
		- Researches about behavior with behavior -> Psychology
			- Some types of question that types of this research often ask:
				- Does reward change its decision?
				- Does previous experience affect its behavior?
			- This types of research do not directly recording neuron to link with brain function or neuron
		- Researches about brain activity with behavior -> Brain function
			- Some types of question that types of this research often ask:
				- Does prefrontal activity predict the animal’s decision?
				- Does activity occur before the animal starts licking?
				-> This types of research often called **neural correlates of behavior**
		- Researches about brain activity with brain activity -> Dynamics of the brain
			- This types of research try to explain one neuron, population or brain region related to activity. There are some example questions:
				- How does auditory cortex influence prefrontal cortex?
				- Do neuronal populations synchronize?
				- Does activity move through brain regions in a particular sequence?
			- This tries to answer question about “network of network” in brain
- Some tools in brain researches:
		![[Introduction_brain-research-tools.png]]
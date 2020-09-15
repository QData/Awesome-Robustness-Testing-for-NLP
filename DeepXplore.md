# Tags
Differential Testing, Neuron Coverage
# Motivation



We need automated testing, i.e. finding corner cases for DNNs with large number of parameters and neurons, as they are more and more being deployed in real world environmetns, with large number 
of unseen data points. 

## Differences between a traditional program and DNNs:
| Programs  |  DNNs |
|---|---|
| not differentiable  | differentiable  |
|  written by humans | not written by humans?  |
| not too large  |  millions of neurons and millions of parameters |
## Key Questions:
1. Find examples that trigger new systems of DL logic 
2. dont need to manually check for corner cases 

# Previous Work
1. Manually gather as much data as possible. 
2. Run simulations to collect data and see behaviour of model

Issue: Unaware of internal DL system, can only cover tiny fraction of all possible corner cases

3. Make adversaria examples such that look the same to us but : 
  1. imperceptible changes 
  2. manual checks ??
  3. Only cover a small aprt of the DL system's logic 
  
  
# Main Idea 
## Neuron Coverage 
1. This is analogous to code coverage for traditional software. Code coverage is not directly applicable. In fact, DL systems can achieve 100% code coverage but only 10% 
neuron coverage. 
Number of Neurons activated or value is above a threshold. 
2. Differential Testing: Multiple players/DNNs trained for the same task should produce the same output.
3. Joit Optimization of finding Test Inputs to maximize neuron coverage + examples that violate the differential testing procedure 

# Tags
Differential Testing, Neuron Coverage, White Box Testing, Gradient Based , efficient for large scale DNN systems 
# Motivation



We need automated testing, i.e. finding corner cases for DNNs with large number of parameters and neurons, as they are more and more being deployed in real world environmetns, with large number 
of unseen data points. 

### Goal is to find data points where the DNN is likely to perform bad, in NLP, find a weird sentence that it will perform bad 

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
X_test = argmin_X [X_{orig} - argmax_X(\lambda_c Coverage(X) + \lambda_d DiffPred(X)    )]

## Neuron Coverage 
1. This is analogous to code coverage for traditional software. Code coverage is not directly applicable. In fact, DL systems can achieve 100% code coverage but only 10% 
neuron coverage. 

Assumption of neuron coverage: as the value of a neuron goes down it influences the following neurons lesser. When the output value of a neuron
becomes zero, the neuron does not have any influence on the
downstream neurons.
Number of Neurons activated or value is above a threshold. 
2. Differential Testing: Multiple players/DNNs trained for the same task should produce the same output.
3. Joint Optimization of finding Test Inputs to maximize neuron coverage + examples that violate the differential testing procedure using gradients. 
4. efficient 

### Metrics used:
1. Neuron Coverage is higher than adversarial inputs and random inputs
2. Given a test set, can predict based on only input sample, that the DNN is likely to perform bad. 


## Limitations of Existing DNN Testing Techniques
1. large Scale labeling effort
2. Split into train and valid and see how it does on valid :
  a. nothing about internals : may not be a good test after all 
3. Adversarial Inputs:
  a. requires manual checking if it is truly imperceptble 
  b. nothing about coverage : internals of the DNN



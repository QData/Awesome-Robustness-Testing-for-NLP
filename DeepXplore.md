# Tags
Differential Testing (how to generate tests), Neuron Coverage (measures test effectiveness), White Box Testing, Gradient Based White Box Testing
# Motivation
### Goal is to find data points where the DNN is likely to perform bad, in NLP, find a weird sentence that it will perform bad 

We need automated testing, i.e. finding corner cases/decision boundary points for DNNs with large number of parameters and neurons, as they are more and more being deployed in real world environments, with large number of unseen data points. 
What can be the different corner cases?
1. out of distribution
2. noisy
3. adversarial

## Differences between a traditional program and DNNs:
| Programs  |  DNNs |
|---|---|
| not differentiable  | differentiable  |
|  written by humans | not written by humans?  |
| not too large  |  millions of neurons and millions of parameters |
## Key Questions:
1. Find examples that trigger new systems of DL logic -- how to know if a test is good?
2. dont need to manually check for corner cases -- finding tests automatically 

# Previous Work
1. Manually gather as much data as possible. 
2. Run unguided simulations to collect data and see behaviour of model

Issue: Unaware of internal DL system, can only cover tiny fraction of all possible corner cases
3. Split into train and valid and see how it does on valid :
  a. nothing about internals : may not be a good test after all
4. Make adversaria examples such that look the same to us but : 
  1. imperceptible changes 
  2. manual checks to see if it is actually adversarial
  3. Only cover a small aprt of the DL system's logic -- measured in terms of neuron coverage
  
  
# Main Ideas or Key Contributions
In terms of mathematical equation --(not the exact objective)

X_test = argmin_X [X_{orig} - argmax_X(\lambda_c Coverage(X) + \lambda_d DiffPred(X)    )]

*DeepXplore objective:*
but instead of outer argmin: constraints on the gradient 

 true_grad = (grad (\lambda_c Coverage(X) + \lambda_d DiffPred(X)    )))
 new_grad = constraints on true_grad
X_new = X_{orig} + lamdab_grad* new_grad
 1. __Definition: Neuron Coverage__ 
This is analogous to code coverage for traditional software. Code coverage is not directly applicable. In fact, DL systems can achieve 100% code coverage but only 10% neuron coverage.
Number of UNIQUE Neurons activated or value is above a threshold for all test inputs.__ 
__Assumption of neuron coverage__: as the value of a neuron goes down it influences the following neurons lesser. When the output value of a neuron
becomes zero, the neuron does not have any influence on the
downstream neurons.
NCov(T,x) = |n| out(neuron_n,x)>threshold|/|N|
Neuron coverage as output of neuron activation 
is differentiable


2. __Differential Testing__: Multiple players/DNNs trained for the same task should produce the same output.
3. __Joint Optimization__ of finding Test Inputs to maximize neuron coverage + examples that violate the differential testing procedure using gradients. 
4. __efficient__: tracks unactivated neurons and picks subset only at each step to add to the objective 


__Other points of note__ :
1. Neuron Coverage is higher than adversarial inputs and random inputs
2. Given a test set, can predict based on only input sample, that the DNN is likely to perform bad. 


  
 ## Method
 Input is k DNNs 
 Output : x' such that F_k(x')\neq y for atleast 1 k 
 
 Algorithm Details
 OBJ1: loss1(sum of confidence scores from a set of dnns except a random dnn) - lambda_1 (loss from random dnn)
 OBJ2: select a neuron not aactivated so far in all dnns and add its value 
 OBJ3: Apply constraints on the gradient 
 
 If succesfully prediction is different : add the example and and run another forward to update the cov tracker 
 Per sample, number of inference procedures: 1(initial class prediction) + k(dnns in obj 2) + 1(update cov tracker)
## Questions
are all wrong examples decision boundary examples? Can confidence score be used?

## Experiments 

1. Domain Specific Constraints
  a. patch of rectangle instead of entire image
  b. black squares as gradient =0 ??
  c. brightness 

### Result Figures :
1. Number of difference-inducing inputs found by DeepXplore for each tested DNN
2. Neuron Coverage vs Code Coverage
3. How different are the generated images from the true images-- diversity 
4. overlap vs numer of activated neurons for two classes
5. t vs nc (adv, random, )
6. Total time taken by DeepXplore to achieve 100% neuron coverage for different DNNs averaged over 10 runs. The last
column shows the number of seed inputs.
7. improvements after adding the samples


### Limitations
1. Requires multiple DNNs
2. If same outputs or make the same mistake: useless


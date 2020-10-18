# DeepXplore: Automated Whitebox Testing of Deep Learning Systems
## Summary:
find incorrect corner case behaviors by maximizing neuron coverage and checking differential behavior by cross referencing multiple models. Uses white box gradient based techniques.
## Motivation:
Goal is to find data points where the DNN is likely to perform bad-- looking for corner cases in a test set

We need automated testing, i.e. finding corner cases/decision boundary points for DNNs with large number of parameters and neurons, as they are more and more being deployed in real world environments, with large number of unseen data points. 
What can be such different corner cases?
1. out of distribution
2. noisy
3. adversarial

## Differences between a traditional program and DNNs:
| Programs  |  DNNs |
|---|---|
| not differentiable  | differentiable  |
|  written by humans | not written by humans?  |
| not too large  |  millions of neurons and millions of parameters |
## Key Questions answered by this paper:
1. how to know if a test is good?
2. How to find corner cases or examples that can serve as good tests -- finding tests automatically 

## Previous Work on testing DNNs

0. Random Testing: Split into train and valid and see how it does on valid :
  a. nothing about internals : may not be a good test after all
1. Manually gather as much data as possible. 
2. Run unguided simulations to collect data and see behaviour of model

Issue: Unaware of internal DL system, can only cover tiny fraction of all possible corner cases

3. Make adversaria examples such that look the same to us but : 
  1. imperceptible changes 
  2. manual checks to see if it is actually adversarial
  3. Only cover a small part of the DL system's logic -- measured in terms of neuron coverage
  
  
## Main Ideas or Key Contributions
In terms of mathematical equation --(Desired objective, Warning: this is not the actual objective of the paper )

X_test = argmin_X ImageDiff[X_{orig},  argmax_X(\lambda_c Coverage(X) + \lambda_d DiffPred(X)    )]

Actual *DeepXplore objective:*
but instead of outer argmin: constraints on the gradient 

true_grad = (grad (\lambda_c Coverage(X) + \lambda_d DiffPred(X)    )))
new_grad = constraints on true_grad
X_new = X_{orig} + lamdab_grad* new_grad
 1. __Definition: Neuron Coverage__ (This measures how good a test is)
This is analogous to code coverage for traditional software. Code coverage is not directly applicable. In fact, DL systems can achieve 100% code coverage but only 10% neuron coverage.
Number of UNIQUE Neurons activated or value is above a threshold for all test inputs.__ 
__Assumption of neuron coverage__: as the value of a neuron goes down it influences the following neurons lesser. When the output value of a neuron
becomes zero, the neuron does not have any influence on the
downstream neurons.
NCov(T,x) = |n| out(neuron_n,x)>threshold|/|N|
Neuron coverage as output of neuron activation 
is differentiable


2. __Differential Testing__: Multiple players/DNNs trained for the same task should produce the same output.(This provides a way to generate this test)
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

# Keywords
Differential Testing (how to generate tests), Neuron Coverage (measures test effectiveness), White Box Testing, Gradient Based White Box Testing


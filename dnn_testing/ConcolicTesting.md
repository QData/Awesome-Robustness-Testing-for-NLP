# Concolic Testing for Deep Neural Networks
Youcheng Sun, Min Wu, Wenjie Ruan, Xiaowei Huang, Marta Kwiatkowska, Daniel Kroening
ASE 2018
## Summary 
concolic testing (combining concrete execution (i.e. testing) with
symbolic execution) extended to DNNs. 
## Motivation
Testing software provides guidance to the user of success in deployment. 
Concolic Testing fits the DNN case:
1. high dimensional inputs : random testing can't possibly cover all cases. 
2. symbolic execution: relu neuron activation leads to too many exectuion paths

Hence, **Concolic testing can select certain execution paths based on DNN properties**. 




## Contributions
1. New Coverage criterion: QLAR
2. concrete execution: Say test set does not satisfy r in R, then find t such that [r(t) - r_0] is minimum , that is closest to finding the test example
3. symbolic analysis: revise t to t' such that r(t) is desirable. 
4. Evaluate Test Suite using oracle that measures robustness to adversarial examples, (If the test suite has adversarial examples).

### Briefly Concolic Testing
- A cycle of concrete execution and symbolic analysis till a coverage criterion is met. 



## Related Work

## Test Coverage for DNNs
## Activation patterns to represent execution path 
Each fixed sample x, results in a specific activation path and this can be encoded using a Linear Programming problem. 
## Formalizing Test Coverage Criteria
DR formulas are composed of 
1. r : coverage criteria
2. e : boolean formula
3. a : arithmetic formula 

## Definition of Satisfiability of a coverage criterion r by a test suite T
Complexity: Given a test suite T, coverage criterion r, network N, checking if a test suite T satisfies r, takes polynomial time in size of T. 

## Test Coverage Metrics
ratio of number of satisfied criterion in R over total number of coverage criteron in R. 

Definition:
__Set of Input Spaces__
1. These can be specified in terms of box constraints


### Lipschitz Continuity
1. If r_lip is true, then c can't be a lipschitz constant. as you can find samples that show a greater value as earlier you said c is the max value. 
Defined for input layer only. 
### Neuron Coverage
For a given neurn, there exists a sample in the test suite for which that neuron is activated. Should be true for all neurons after input layer.  
What about and combinations?
### Modified Condition/ Decision Making: Sign Sign Coverage 
Take two adjacent layers:
take all possible neuron layers:
there exists a pair of examples, for which the two neurons give opposite signs but the rest of the neurons shoudl remain the same. Find for all possible neurons and layers 
### Neuron Boundary Coverage
Two sets of bounds : upper and lower and find the ones that can violate this bound. 

## Algorithm 
The output is a test suite. 

## Ranking Coverage Requirements 
1. requirement_evaluation finds the best criterion that has not been satisfied, a heuristic to check if it is satisfied and the best example that are claosest to each other: R * N_seeds combinations 

heuristic for each requirement: such that r is \delta(r) -- the extent to which an input satisfies r
1. find argmax delta(r)--> returns a sample t, the value of the heuristic is val(delta(r), t). This delta r is max_x (maximizes an aritmentic a and also satisfies a boolean condition). So, say must be a close to real input and must maximize a loss? Like in DeepXplore, an X that maximizes coverage and difference but subject tp some constraints 


2. search ver all r's 
3. return that r and t 

In detail, solution of min_x a:e returns a such that t \in T, T satisfies e but r(x-->t)<= r(x-->t') t' \in T. All the seed inputs satisfy these conditions

### Heuristics 
1. Lipshitz
FInd the pair that maximizes 
||v_1[x_1]-v_1[x_2]|| - c*||x_1 - x_2||
2. Neuron Coverage for a specific neuron
-- Convert to maximum coverage additionally weighted by a layer specific constant 
\delta(NC) = max_x (c_l \sum_unit_l activation_layer_unit_before_relu): true 


3. SS Coverage for a specific neuron

4. neuron Boundary coverage -- (find one closest to boundary )
arg max _ x (u[x] -  h_upper_boundary): true 
arg max _ x (lower_boundary -  u[x]): true 



## Symbolic Generation of Concrete Inputs 
Input : t,r that have the most chances of success
Three optimizataion algorithms:
1. linear programming
2. global optimization for l_0 norm
3. new optmization algorithms 



### Linear programming
1. For Neuron Coverage we desire a neuron to be flipped. Before this, neuron all layers must preserve the activation patterns. 
ReLU at a point can be converted into linear model 




# Keywords
Concolic Testing


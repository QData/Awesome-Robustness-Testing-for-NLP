# Tags
Concolic Testing

# Motivation
Testing software provides guidance to the user of success in deployment. 
Concolic Testing fits the DNN case:
1. high dimensional inputs : random testing can't possibly cover all cases. 
2. symbolic execution: relu neuron activation leads to too many exectuion paths

Hence, **Concolic testing can select certain execution paths based on DNN properties**. 




# Contributions
1. New Coverage criterion: QLAR
2. concrete execution: Say test set does not satisfy r in R, then find t such that [r(t) - r_0] is minimum , that is closest to finding the test example
3. symbolic analysis: revise t to t' such that r(t) is desirable. 
4. Evaluate Test Suite using oracle that measures robustness to adversarial examples, (If the test suite has adversarial examples).

## Briefly Concolic Testing
- A cycle of concrete execution and symbolic analysis till a coverage criterion is met. 



# Related Work

# Test Coverage for DNNs
## Activation patterns to represent execution path 
Each fixed sample x, results in a specific activation path and this can be encoded using a Linear Programming problem. 
## Formalizing Test Coverage Criteria
DR formulas are composed of 
1. r : coverage criteria
2. e : boolean formula
3. a : arithmetic formula 

__Definition of Satisfiability of a coverage criterion r by a test suite T__


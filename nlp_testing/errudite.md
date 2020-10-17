# Errudite: Scalable, Reproducible, and Testable Error Analysis

## Summary
Errudite is an NLP focused Systematic Error Analysis tool. It provides functionalities of defining error hypotheses, 
extracting test examples following a hypothesis in a scalable way and perturbing inputs in a scalable way for counterfactual analysis. 

## Motivation
Error Analysis: When and why do models fail?
Two types of error analysis for NLP:
1. Data Grouping: Aggregate Metrics over groups of data : coarse and limited
2. Counterfactual Error Analysis: modify the input data to see if model still behaves the same way, such as adding irrelevant data to see if new errors are introduced. : not scalable

Limitations:
- gives small number of test ssamples, not representative of the true ERROR distribution, high variance

- small number of tests: can come to incorrect conclusion this is error, but actually well handled on average, low reproducibility

- wrong causes:
'Distractor' in Machine Comprehension is a common error hypothesis. For example, if the context paragraph also includes two entities, one corresponding to the answer entity and the other called the 'Distractor' entity. The model incorrectly predicts the distractor entity. 
Is 'Distractor' truly the cause? Check using counter factual



## Task : Machine Comprehension
## Dataset : SQuAD (Rajpurkar, Pranav, et al. "Squad: 100,000+ questions for machine comprehension of text." arXiv preprint arXiv:1606.05250 (2016)) 
## Model : BiDAF (Seo, Minjoon, et al. "Bidirectional attention flow for machine comprehension." arXiv preprint arXiv:1611.01603 (2016).)


## Error Analysis Principles of Errudite
### 1. P1: Precise and Reproducible Hypotheses : Errudite provides Domain Specific Language (DSL)
    What we do not want ? 
    "The model does bad on long sentences"
    What we want?
    "The model does bad on questions larger than length N"
    ## Solution : 
    DSL with three components : 
    1. Targets: inputs and outputs at different levels of granularity (example: q(question), passage context (c), ground truth (g)) etc
    2. Attribute Extractors: attributes about targets: example length(q), ENT(q)
    3. Operators: above attribute extractors can be composed using logical or numerical operators
### 2. P2: Error Prevalence should be assessed over the entire dataset: Errudite makes this scalable by grouping related queries to enable better error analysis, these are composable. 


### 3. P3:Error hypotheses should be explicitly tested. 
This means testing using counterfactual questions : "If the distractor wasnt there, will the model still predict wrong?"
Using the above query grouping strategy, Errudite is able to scale to large number of counterfactual examples, that can help
pinpoint the cause of a specific error. 




## Experiments

Focused on User studies evaluating:
1. Replication: If previous work on NLP error hypotheses can be replicated and if they were correct?
2. Exploration: General Utility of the toolbox











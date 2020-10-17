# Checklist 

## Summary
Checklist is a behavioral testing toolkit for NLP models.It provides guidelines in terms of domain specific linguistic capabilities, with corresponding test types/sanity checks. It also includes abstractions to generate large number of test cases directly. 

### It corresponds to a conceptual matrix with rows testing capabilities and columns representing the types of tests. Entries in
the matrix are by themselves the tests.

### It is Model Agnostic as well as Task Agnostic.


## Motivation
Goal of good NLP models: generalization
Most commonly used NLP model evaluation technique: performance on held out set using a 
single aggregate metric, but this does not tell us why model is failing

Behiavoural Testing: Is a technique used in software testing for complex systems that analyzes input
output behaviour without access to the software's internals.

NLP models are not built one component by component over time. So component testing doesnt work.

## Three Components of the CheckList matrix: capabilities, types of tests, and the test

### Capabilities

This depends on the model at hand. For NLP good ones are:
1. Vocabulary + Parts of Speech
2. Taxonomy
3. Robustness: invariance to typos, irrelevant changes, 
4. NER: approporiately understanding named entities
5. Fairness
6. Temporal: order of events
7. Negation
8. Coreference
9. Semantic Role Labeling
10. Logic: consistency, symmetric, etc.





### Test Types
#### Minimum Functionality Tests
#### Invariance Tests: label preserving perturbations to inputs and expect the model prediction to remain the same.(software metamorphic tests )
#### Directional Expectation Tests: The sentiment should not turn more positive if we add "negative" sentiment to the sentence.

The INV and DIR tests can be applied to unlabeled data, and do not need labels.



### Generating Tests

Can be generated from scratch as well as from an existing dataset. For generating from scratch, CheckList provides templates for each test type. Not scalable, as these require hand designed choices. CheckList provides an alternative by providing suggestions using a RoBERTa, a masked language model.

## Experiments
All experiments focus on failure rates for entries in the matrix, for popular state-of-the-art commerical models.






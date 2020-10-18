# DeepTest: Automated Testing of Deep-Neural-Network-driven Autonomous Cars
Yuchi Tian, Kexin Pei, Suman Jana, Baishakhi Ray
ICSE 2018
## Summary 
systematic technique to automatically synthesize
test cases that maximizes neuron coverage in safety-critical DNNbased systems like autonomous cars.

## Motivation
Existing mechanisms for detecting such erroneous behaviors depend heavily on manual collection of labeled
test data or ad hoc, unguided simulation and therefore miss
numerous corner cases. 
- Further, the space of possible inputs is extremely large. Thus, unguided simulations are highly unlikely to
find many erroneous behaviors.  This paper designs a systematic
testing methodology for automatically detecting erroneous behaviors of DNN-based software

## Neuron Coverage
Neuron Coverage = |Activated Neurons|/Total Neurons

DeepTest tries to generate inputs that maximize neuron
coverage of the test DNN using transformations that maximize neuron coverage. 
Transformations:

1. affine transformations:Translation, scaling, horizontal shearing, and rotation
2. brightness, contrast
3. rotation

They propose a neuron-coverage-guided greedy search technique for efficiently
finding combinations of image transformations that result in higher
coverage.


## Experiment Figures
1. Do different input-output pairs result in different neuron
coverage?
2. Do different realistic image transformations activate different neurons?
3. Can neuron coverage be further increased by combining
different image transformations?
4. Can we automatically detect erroneous behaviors using
metamorphic relations?
5. Can retraining DNNs with synthetic images improve accuracy?
## Keywords
Gray Box Testing, Neuron Coverage,  Metamorphic Testing

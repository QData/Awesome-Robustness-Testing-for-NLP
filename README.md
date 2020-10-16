# Automated-Robustness-Testing-for-NLP
## Why is testing DNNs important?
DNNs are modern software being deployed everywhere. Like other software these must be tested for corner cases(when the software is likely to be problematic). 
## Why is testing DNNs hard?
DNNs have too many parameters: too many neurons. Manually finding corner cases is too difficult. Need automated testing , i.e. generating automatically corner cases for large DNNs. 

## General Intro Position Papers/ Blogs
1. (Medium DeepMind Blog)[https://medium.com/@deepmindsafetyresearch/towards-robust-and-verified-ai-specification-testing-robust-training-and-formal-verification-69bd1bc48bdaΩ]
2. [General Survey of Testing in ML](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9000651)
### Neuron Coverage Based 
  1. [GrayBox Testing: DeepTest](https://arxiv.org/pdf/1708.08559.pdf) -- Augmentation, Neuron Coverage
  2. [White Box Gradient Based Testing](https://arxiv.org/abs/1705.06640)
  3. [DeepCT](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8668044)
  4. [Concolic Testing for Deep Neural Networks](http://qav.comlab.ox.ac.uk/papers/swr+18.pdf)
  5. [FuzzTesting](https://www.comp.nus.edu.sg/~abhik/pdf/ICSE20_Sensei.pdf) -- Augmentation,
  6. [Testing Deep Neural Networks- Symbolic Execution](https://arxiv.org/abs/1803.04792)
  7. [MCTS based](https://arxiv.org/abs/1710.07859)
  
##### Fuzzing Based 
1.  [FuzzTesting](https://www.comp.nus.edu.sg/~abhik/pdf/ICSE20_Sensei.pdf) -- Augmentation
2. [TensorFuzz](http://proceedings.mlr.press/v97/odena19a/odena19a.pdf)
3. [DLFuzz](https://arxiv.org/pdf/1808.09413.pdf)
4. [NeuFuzz](https://wcventure.github.io/FuzzingPaper/Paper/Access19_NeuFuzz%20.pdf)
## Robustness Testing for NLP Deep Models 
1. [Robustness Verification for Transformers](https://arxiv.org/pdf/2002.06622.pdf)
2. [Towards a Robust Deep Neural Network in
Texts: A Survey](https://arxiv.org/pdf/1902.07285.pdf)

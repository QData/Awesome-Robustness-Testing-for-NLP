# Blog Post: [Towards Robust and Verified AI: Specification Testing, Robust Training, and Formal Verification](https://medium.com/@deepmindsafetyresearch/towards-robust-and-verified-ai-specification-testing-robust-training-and-formal-verification-69bd1bc48bda)

1. Is the model consistent defined by behaviour controlled by the designer specificcations? finding corner cases during evaluation using worst case analysis

Robustness is a well studied problem, the question is to design models that how to evaluate against strong attacks. RL uses adversarial testing(paper example)[https://arxiv.org/abs/1812.01647]. 
2. Train the models to be specification consistent 

Specification is some relationhsip that must hold. If this bound is differentiable, propagte this bound through the model. 
3. How to show that the models are specification consistent: formal verification methods that do not scale well 
It is impossible to test for Computing bounds on the space of the output.




# Fuzzing Book 
## Fuzzing: Breaking Things with Random Inputs

__What is Fuzzing?__
give random inputs to a program to see if it fails. The goal is to test the robustness of as many NLP programs as possible.The idea is to generate random inputs and see 
if the DNN breaks or not. 

The **Fuzz Generator** : a program that will output a random character stream
These can be completely random characters or characters with specific constraints. Note that Fuzz may not be similar to adverasrial inputs as this need not be close
to the real-world input. 
**Attack** : get them to break 


What we need for this?
1. A DNN should be able to say this is not a valid input: valid errors
2. A DNN should be able to say this is unseen before : just crashes? What is a crash or a failure in DNN?




Bugs that a fuzzer can find:
1. Buffer overflows
2. Missing Error Checks: Corner Cases wrernt accounted for 
3. Uncommon Values or Rogue Inputs 



# Using fuzzing we know a bad input if the program crashes or hangs. But what if the program fails silently?
Checking silent errors with fuzzing
## Generic Checkers 
1. Memory Checker:  Send fuzzed commands but also give error if emeory check is bad. Illegal memory accesses can leak information. 
2. can happen in valid memory accesses too : heartbeat leak if the string is less thatn the requested length 
## Program Specific Checkers
1. assertiions
## Static Code Checkers
type checkers like MyPy


# Fuzzing Architecture 
## A Runner 
init: like model init which program
run: run on estep 
compile resukts: liek evaluation and loss calculation
## A Fuzzer 
Components: generator, trials
Input: Runner 

# Conclusion
Fuzzing is important when input processing is deficient 



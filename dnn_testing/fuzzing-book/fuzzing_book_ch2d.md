# Greybox Fuzzing
In the previous chaper, we saw that mutation fuzzing gives higher coverage than random fuzzing for teh same input size. Now we
want to be guided by this objective to generate inputs that increase coverage. 


## Ingredients:
### Mutator
### Seed
### Power Schedule 
1. Priortize more promising seeds
2. PowerSchedule: tells us the energy of each input, assigns energy to each input, choooses one based on energy randomly, also keeps a schedule of the number
of times the seed has been seen


## Types of Fuzzing
### 1. Blackbox Fuzzing
Just fuzz based on sceduler 
### 2. Greybox Fuzzing
fuzz, but only add to test set if it increases coverage, will take more time
### 3. Boosted Greybox Fuzzer
assign more energy to seeds that have more energy -- maybe using paths that havent been explored too much.
as a path is visited it updates frequency 
the seed is executed, its path value is checked, path frequency is updated and its path value is used to update its own energy for next time. 



Each Fuzzer takes as input:
1. seeds
2. Schedule -- choose a sample based on a schedule, each time this is called, the sampple energies are updated
3.  Mutator 

Blackbox only 
GreyBoxFuzzing modifies run function to select certain test inputs
Boosted Greybox modified assignEnergy by updated path energy

Ideally, Greybox visits most frequent less and less frequent more 


## Directed GreyBox Fuzzing 
We want the code to reach a dangerous area. 
Find the distance between the path and target, and add it as part of the scheduler, can improve it further by scaling based on distance. 


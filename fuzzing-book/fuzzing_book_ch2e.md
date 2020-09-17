# Search based Fuzzing 
We require inputs that reach a specific code. For this we __need a fitness function__ that tells us how good 
a sample test input is to the desired. 

## 1. Hill Climbing 
Pick a sample, pick some neighobrs, check fitness, find the first better one, then take this as the center seed. 
For steepest, find the best one for the neighbors. 
## 2. Evolutionary Search 
### a. Global Search 
Mutate the input slowly, and 
### b. Genetic Algorithm 

Requires :

Repeat for epochs:
P = []
  Repeat till desired length P:
    1. generate a sample from the population
    2. get fitness of each population
    3. find the winner in the small subsample 
    4. Repeat 1,2 to get set 2 offspring--> (x1,x2)
    5. cross over wih some prob: (x1',x2')
    6. mutate each offspring and position with certain probability --> (x1'', x2'')
    7. append to P
  make this new population 
  repeat


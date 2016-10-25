Notes for ["Discrete Optimization"](https://www.coursera.org/learn/discrete-optimization)

#The Knapsack Problem

The knapsack problem or rucksack problem is a problem in combinatorial optimization: Given a set of items, each with a weight and a value, determine the number of each item to include in a collection so that the total weight is less than or equal to a given limit and the total value is as large as possible. It derives its name from the problem faced by someone who is constrained by a fixed-size knapsack and must fill it with the most valuable items.

##Greedy Algorithms 

A greedy algorithm is an algorithm that follows the problem solving heuristic of making the locally optimal choice at each stage with the hope of finding a global optimum.

* __More items is best__ start with small ones and take as many as you can.  
* __Valuable items are best__ start with the most valuable items.  
* __Value density__ start with items with more dollars per kilogram.  

For one problem, there are many possible greedy algorithms  
some will do better than others  
depends on the input  

* __Advantages__  
quick to design and implement.  
can be very fast.  

* __Problems__  
no quality guarantees (in general).  
quality can vary widely on the input.  
problem feasibility needs to be “easy”.  


##Dynamic Programming

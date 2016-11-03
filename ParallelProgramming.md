Notes for ["Parallel programming"](https://www.coursera.org/learn/parprog1)

___What is Parallel Computing?___  
  *  Parallel computing is a type of computation in which many calculations are performed at the same time.  
  *  Basic principle: computation can be divided into smaller subproblems, each of which can be solved simultaneously.  

___Parallelism Granularity___  
Parallelism manifests itself at different granularity levels
  *  bit-level parallelism – processing multiple bits of data in parallel
  *  instruction-level parallelism – executing different instructions from the same instruction stream in parallel
  *  task-level parallelism – executing separate instruction streams in parallel

___Process___  
  *  an instance of a program that is executing in the OS.
  *  The same program can be started as a process more than once, or even simultaneously in the same OS. 
  *  The operating system multiplexes many different processes and a limited number of CPUs, so that they get time slices of execution. This mechanism is called multitasking.
  *  Two different processes cannot access each other’s memory directly – they are isolated.
  
___Threads___  
  *  Each process can contain multiple independent concurrency units called threads.
  *  Threads can be started from within the same program, and they share the same memory address space.
  *  Each thread has a program counter and a program stack.
  *  threads cannot modify each other’s stack memory. They can only modify the heap memory.

___Atomicity___  
  *  An operation is atomic if it appears as if it occurred instantaneously from the point of view of other threads.  
  *  An atomic process means a process which is not divisible or should not divide.  
  *  The sequence of statements in two separate threads should execute in a specific order, and not overlap.  
  
___Deadlocks___  
Deadlock is a scenario in which two or more threads compete for resources (such as monitor ownership), and wait for each to finish without releasing the already acquired resources.  


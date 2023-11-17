# Dynamic-System-Simulation
Testing the algorithmical aproach of a probability problem

## The Question

There is a one amoeba in a pond. After every minute the amoeba may die, stay the same, split into two or split into three with equal probability. All its offspring, if it has any, will behave the same (and independent of other amoebas).   

What is the probability the amoeba population will die out?

## The mathematical approach 

We define $p_i$ as the probability of extinction of the population of starting size $i$.
Going one step forward in time from initial state:
$$p_1 = \frac{1}{4} + \frac{1}{4} p_1 + \frac{1}{4} p_2 + \frac{1}{4} p_3$$
Using independence, we have $p_i = p_1^i$, we rename $p_1$ to $p$ and get:
$$p = \frac{1}{4} + \frac{1}{4} p + \frac{1}{4} p^2 + \frac{1}{4} p^3$$
We can solve this third-degree polynomial and we get 3 solutions, only one of these being between $0$ and $1$: $p=\sqrt{2}-1$ which is the answer.

## The algorithmic approach 

We simulate the life cycle of the amoeba and its potential offspring over a series of iterations, each representing a minute in the simulation. 
This method uses the Monte Carlo simulation technique, which repeated random sampling to obtain numerical results.

The simulation follows these steps:
- Start with a single amoeba.
- For each minute, determine the fate of each amoeba in the population based on equal probability for the following events:
    - Death: The amoeba dies and is removed from the simulation.
    - Stasis: The amoeba neither dies nor reproduces; its state remains the same.
    - Binary Fission: The amoeba splits into two separate amoebas, doubling its count.
    - Trinary Fission: The amoeba splits into three separate amoebas, tripling its count.
- Each offspring is then treated as a new individual amoeba and follows the same probabilistic rules in the next iteration.
- The simulation ends when the amoeba population dies out (i.e., reaches zero) or when the predetermined time limit is reached.

### Results

For a test of 1000 populations with a maximum of 10 minutes each, the execution time take only 0.2 seconds, and the resulting death ratio was approximately __0.406__.  

For a more extended simulation, where each of the 1000 populations had up to 30 minutes, the execution time was around 4 minutes and 5 seconds, leading to a slightly higher death ratio of __0.429__.

This demonstrates the simulation's capability to efficiently process complex probabilistic outcomes.

![The results](https://github.com/MatthieuHanania/Dynamic-System-Simulation/blob/main/results.png)

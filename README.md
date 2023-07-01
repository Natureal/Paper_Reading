# Paper_Reading
## MEC Related
1: ICWS '19 [A Mobility-Aware Cross-edge Computation Offloading Framework
for Partitionable Applications](https://www.researchgate.net/profile/Hailiang-Zhao-4/publication/335464610_A_Mobility-Aware_Cross-Edge_Computation_Offloading_Framework_for_Partitionable_Applications/links/5d7b8a024585155f1e3f2bca/A-Mobility-Aware-Cross-Edge-Computation-Offloading-Framework-for-Partitionable-Applications.pdf)
  - [Sides](http://hliangzhao.me/slides/cross_edge.pdf)
  - [Theorical Analysis](http://hliangzhao.me/papers/Theoretical_analysis.pdf)
  - [Lyapunov Optimization Introduction](http://hliangzhao.me/math/Lyapunov_optimization.pdf)
  - **Keywords**:
    - MEC, Computation Offloading, Cross-edge Collaboration, Application Partition, Lyapunov Optimization
  - **Problem**:
    - In the MEC scenario, how to design a computation offloading strategy with the minimum overall cost for partitionable applications.
  - **Formulation**: 
    - These 4 factors are taken into account: (1) transmission delay (2) execution delay (3) collaboration/coordination cost (4) battery energy level
    - **Constraints**:
      - (1) exec deadline >= maximum delay(trans + exec) + local exec delay + collaboration cost = TIME COST
      - (2) battery level >= local exec battery cost + sum of trans battery cost
    - **Purpose**(a non-convex optimization problem):
      - Find the minimum expectation of COST, where COST is TIME COST + DROPPING PENALTY.
  - **Method**: CCO(Cross-edge Computation Offloading) algorithm + Sampling-and-classification based edge site-selection algorithm (SES).
  - **Comments & Inspiration**:
    - The author decomposed the problem into two sub-problem: (1) edge site selection (2) evaluate optimized cost of the selection.
      - (1) SES. Sample-and-classification (SAC) based algo was proposed with the subroutine being restricted as *a binary classification algorithms*. [Common binary classification algorithms](https://towardsdatascience.com/top-10-binary-classification-algorithms-a-beginners-guide-feeacbd7a3e2)
      - (2) Lyapunov function was introduced to formulate the battery level of devices, which is appropriate for devices that are able to harvest energy. Consequently, asymptotic optimal result of a specific selection can be calculated, which makes selections sampled by SAC algorithm evaluable, enabling SES works properly.

## Optimization Related
1. CEC '14 [The Sampling-and-Learning Framework: A Statistical View of Evolutionary Algorithms](https://www.researchgate.net/publication/259893738_The_Sampling-and-Learning_Framework_A_Statistical_View_of_Evolutionary_Algorithms#fullTextFileContent)
  - 

2. AAAI '16 [Derivative-Free Optimization via Classification](https://www.researchgate.net/publication/303487232_Derivative-Free_Optimization_via_Classification)




# Summary



# Note

## derivative-free optimization methods list (updating)
  - genetic algorithms (Golberg 1989)
  - randomized local search (Neumann and Wegener 2007)
  - estimation of distribution algorithms (Larranaga and Lozano 2002)
  - cross-entropy methods (de Boer 2005)
  - bayesian optimization methods (Brochu, Cora and De Freitas 2010)
  - optimistic optimization methods (Munos 2014)

## Scholars studying MEC, edge-computing, distributed systems
  - Shuiguang Deng (zju)
  - Hailiang Zhao (zju)
  - Zhuzhong Qian (nju)

## Scholars studying derivative-free optimization
  - Yang Yu (nju)
  - Hong Qian (ecnu)


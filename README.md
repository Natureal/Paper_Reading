# Paper_Reading
1: ICWS '19 [A Mobility-Aware Cross-edge Computation Offloading Framework
for Partitionable Applications](https://www.researchgate.net/profile/Hailiang-Zhao-4/publication/335464610_A_Mobility-Aware_Cross-Edge_Computation_Offloading_Framework_for_Partitionable_Applications/links/5d7b8a024585155f1e3f2bca/A-Mobility-Aware-Cross-Edge-Computation-Offloading-Framework-for-Partitionable-Applications.pdf)
  - [Sides](http://hliangzhao.me/slides/cross_edge.pdf)
  - [Theorical Analysis](http://hliangzhao.me/papers/Theoretical_analysis.pdf)
  - [Lyapunov Optimization Introduction](http://hliangzhao.me/math/Lyapunov_optimization.pdf)
  - Keywords: MEC, Computation Offloading, Cross-edge Collaboration, Application Partition, Lyapunov Optimization
  - What Problem: In the MEC scenario, how to design a computation offloading strategy with the minimum overall cost for partitionable applications.
  - Problem Formulation: 
    - These 4 factors are taken into account: (1) transmission delay (2) execution delay (3) collaboration/coordination cost (4) battery energy level
    - Constraints:
      - (1) exec deadline >= maximum delay(trans + exec) + local exec delay + collaboration cost = TIME COST
      - (2) battery level >= local exec battery cost + sum of trans battery cost
    - Purpose(a non-convex optimization problem):
      - Find the minimum expectation of COST, where COST is TIME COST + DROPPING PENALTY.
  - What Method: CCO(Cross-edge Computation Offloading) algorithm.
  -

2. [Derivative-Free Optimization via Classification](https://www.researchgate.net/publication/303487232_Derivative-Free_Optimization_via_Classification)
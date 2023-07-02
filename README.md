# Paper_Reading
- While reading the paper I will try to answer the following questions:
  - **What** is the problem?
    - keywords
    - problem description
    - related work
  - **Why** solve this problem?
    - significance
  - **How** to solve this problem?
    - formulation and modeling
    - methods
  - **Why** use this method?
    - comments
    - thinking & inspiration

## I. MEC Related Papers
### 1: ICWS '19 [A Mobility-Aware Cross-edge Computation Offloading Framework
for Partitionable Applications](https://www.researchgate.net/profile/Hailiang-Zhao-4/publication/335464610_A_Mobility-Aware_Cross-Edge_Computation_Offloading_Framework_for_Partitionable_Applications/links/5d7b8a024585155f1e3f2bca/A-Mobility-Aware-Cross-Edge-Computation-Offloading-Framework-for-Partitionable-Applications.pdf)
  - **0. Materials**: [Sides](http://hliangzhao.me/slides/cross_edge.pdf), [Theorical Analysis](http://hliangzhao.me/papers/Theoretical_analysis.pdf), [Lyapunov Optimization Introduction](http://hliangzhao.me/math/Lyapunov_optimization.pdf)
  - **What** is the problem?:
    - **keywords**: MEC, Computation Offloading, Cross-edge Collaboration , Lyapunov Optimization
    - **problem description**: In the MEC scenario, how to design a computation offloading strategy with the minimum overall cost for partitionable applications.
    - **related work**:
      - (1) [Mobile edge computing(MEC) survey](https://www.researchgate.net/publication/319299183_A_Survey_on_Mobile_Edge_Computing_The_Communication_Perspective)
      - (2) Greedily select edge servers according to legitimated bandwidth and computing resources. [QoE Aware and Cell Capacity Enhanced Computation Offloading](https://ieeexplore.ieee.org/document/8560111)
      - (3) Introduce Lyapunov optimization to decompose a long-term problem into a series of real-time problem.[Follow me at the edge. JSAC '18](https://www.researchgate.net/publication/327688157_Follow_Me_at_the_Edge_Mobility-Aware_Dynamic_Service_Placement_for_Mobile_Edge_Computing)
  - **Why** solve this problem?
    - **significance**: Existing offloading strategies cannot handle the procedure for mobility-aware computation-intensive services.
  - **How** to solve this problem?
    - **formulation**: 
      - These 4 factors are taken into account:
        - (1) transmission delay
        - (2) execution delay
        - (3) collaboration/coo rdination cost
        - (4) battery energy level
      - **several constraints**:
        - (1) exec deadline >= maximum delay(trans + exec) + local exec delay + collaboration cost = TIME COST
        - (2) battery level >= local exec battery cost + sum of trans battery cost
      - **objective**(a non-convex optimization problem):
        - Find the minimum expectation of COST, where COST is TIME COST + DROPPING PENALTY.
    - **method**:
      - Cross-edge Computation Offloading algorithm(CCO)
      - Sampling-and-classification based edge site-selection algorithm(SES).
  - **Why** use this method?
    - **comments**:
      - The author decomposed the problem into two sub-problem: (1) edge site selection (2) evaluate optimized cost of the selection.
        - (1) SES. Sample-and-classification (SAC) based algo was proposed with the subroutine being restricted as *a binary classification algorithms*. [Common binary classification algorithms](https://towardsdatascience.com/top-10-binary-classification-algorithms-a-beginners-guide-feeacbd7a3e2)
        - (2) Lyapunov function was introduced to formulate the battery level of devices, which is appropriate for devices that are able to harvest energy. Consequently, asymptotic optimal result of a specific selection can be calculated, which makes selections sampled by SAC algorithm evaluable, enabling SES works properly.
    - **inspiring points**:
         - (1) Based on Lyapunov optimization, **priori knowledge on mobility** is not necessary to know.
         - (2) By introducing SAC, a high-dimensional non-differentiable problem is reduced to **a binary classification problem**.

### 2. IEEE Access '18 [Composition-Driven IoT Service Provisioning in Distributed Edges](https://www.researchgate.net/publication/327787725_Composition-Driven_IoT_Service_Provisioning_in_Distributed_Edges)
  - **What** is the problem?
    - **keywords**: MEC, IoT, Service Composition, Service Cache
    - **problem description**: How to establish efficient IoT service provision based on MEC under resource constraints.
    - **related work**:
      - (1) IoT MEC frameworks
      - (2) cache policy without utilizing the composition technologu of services
  - **Why** solve this problem?
    - **significance**: When using MEC technology, novel IoT services such like AR/VR/... are still restricted by a series of constraints, such as low computational capability, long respone time, etc. Optimizing the performance of MEC will facilitate the promotion of these novel services.
  - **How** to solve this problem?
    - **formulation**:
      - **Terms**:
        - (1) Two kinds of services: composite service and atomic service.
        - (2) The consumption of a composite service is equal to the sum of the consumption of its constituent sub-services.
        - (3) Services is available at the edge if it is cached, otherwise it has to be accessed from the cloud.
        - (4) ASRT(average service reponse time) is used evaluate the cache policy. 
      - **constraints**:
        - (1) Only memory resources are considered as constraints.
      - **Objective**: (similar to a backpack problem with complexity is 2^n)
        - Design a cache policy that optimizes ASRT by selecting a set of services which are cached at the edge.
    - **method**:
      - (1) A kind of random-greedy initialization algorithm
      - (2) ASRT is evaluated by greedy algorithm
      - (3) Genetic Algorithm
  - **Why** use this method?
    - **comments & inspiration**:
      - A proper random-greedy initialization is a key factor for high efficiency.
      - As a kind of evolutionary algorithm, genetic algorithm is efficient for this NP problem.

### 3. IEEE Trans. Wirel. Commun '17 [Energy-Efficient Resource Allocation for Mobile-Edge Computation Offloading](https://ieeexplore.ieee.org/document/7762913)



## II. Optimization Related Papers
1. CEC '14 [The Sampling-and-Learning Framework: A Statistical View of Evolutionary Algorithms](https://www.researchgate.net/publication/259893738_The_Sampling-and-Learning_Framework_A_Statistical_View_of_Evolutionary_Algorithms#fullTextFileContent)

2. CEC '16 [On Sampling-and-Classification Optimization in Discrete Domains](https://www.researchgate.net/publication/303487011_On_Sampling-and-Classification_Optimization_in_Discrete_Domains)

3. AAAI '16 [Derivative-Free Optimization via Classification](https://www.researchgate.net/publication/303487232_Derivative-Free_Optimization_via_Classification)


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


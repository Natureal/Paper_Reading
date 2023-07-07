# Paper_Reading
- While reading the paper I will try to answer the following questions:
  - **What** is the problem?
    - the **novelty** of this paper
    - keywords & problem description
    - related work
  - **Why** solve this problem?
    - significance
  - **How** to solve this problem?
    - formulation and modeling
    - methods
  - **Why** use this method?
    - comments
    - inspiration & new idea
    - problem?

---
- Current Reading Stats
  - Edge Computing
    - Mobile Edge Computing: 1
    - Service Provisioning: 1
    - Serverless Computing: 1  
  - Optimization Theory
    - EAs / Derivative-free optimization: 2
---

## I. MEC Related Papers
### 1: ICWS '19 [A Mobility-Aware Cross-edge Computation Offloading Framework for Partitionable Applications](https://www.researchgate.net/profile/Hailiang-Zhao-4/publication/335464610_A_Mobility-Aware_Cross-Edge_Computation_Offloading_Framework_for_Partitionable_Applications/links/5d7b8a024585155f1e3f2bca/A-Mobility-Aware-Cross-Edge-Computation-Offloading-Framework-for-Partitionable-Applications.pdf)
  - **0. Materials**: [Sides](http://hliangzhao.me/slides/cross_edge.pdf), [Theorical Analysis](http://hliangzhao.me/papers/Theoretical_analysis.pdf), [Lyapunov Optimization Introduction](http://hliangzhao.me/math/Lyapunov_optimization.pdf)
  - **What** is the problem?:
    - **novelty**: modeling method and the algo framework
    - **keywords**: MEC, Computation Offloading, Cross-edge Collaboration
    - **problem description**: In the MEC scenario, how to design a computation offloading strategy with the minimum overall cost for partitionable applications.
    - **related work**:
      - (1) [Mobile edge computing(MEC) survey](https://www.researchgate.net/publication/319299183_A_Survey_on_Mobile_Edge_Computing_The_Communication_Perspective)
      - (2) Greedily select edge servers according to legitimated bandwidth and computing resources. [QoE Aware and Cell Capacity Enhanced Computation Offloading](https://ieeexplore.ieee.org/document/8560111)
      - (3) Introduce Lyapunov optimization to decompose a long-term problem into a series of real-time problem. [Follow me at the edge. JSAC '18](https://www.researchgate.net/publication/327688157_Follow_Me_at_the_Edge_Mobility-Aware_Dynamic_Service_Placement_for_Mobile_Edge_Computing)
  - **Why** solve this problem?
    - **significance**: Existing offloading strategies cannot handle the procedure for mobility-aware computation-intensive services, and also do not take cross-edge collaboration into account.
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
    - **inspiration**:
         - (1) Based on Lyapunov optimization, **priori knowledge on mobility** is not necessary to know.
         - (2) By introducing SAC, a high-dimensional non-differentiable problem is reduced to **a binary classification problem**.
         - (3) H. Zhao gave a good introduction of Lyapunov optimization in Chinese which helps me a lot in understanding it. [Lyapunov Optimization Introduction](http://hliangzhao.me/math/Lyapunov_optimization.pdf)
     - **problem?**:
         - How other simple dynamic-programming based algorithms work on this problem?
         - Is there any other derivatie-dree optimization algorithm solves the selection problem better?

### 2. TPDS '22 [Dependent Function Embedding for Distributed Serverless Edge Computing](https://dsg.tuwien.ac.at/team/sd/papers/Zeitschriftenartikel_2022_SD_Dependent.pdf)
  - **What** is the problem?
    - **novelty**:
      - takes *proactive traffic routing* and *data splitting* into consideration.
      - A DP algorithm is proposed to this optimization problem.
    - **keywords**: Edge computing, Dependent Function Embedding, Task Scheduling
    - **problem description**: In the scenario of FaaS, how to design an algorithm framework to optimize makespan of serverless edge computing.
    - **related work**:
      - inter-task dependency & resource-constrained scheduling
        - Serverless architecture for edge computing - B. Javadi et al.
      - optimal function placement
        - Dependent task placement and scheduling with function configuration in edge computing - L. Liu et al.
      - other related algorithms
        - *FixDoc*: Dependent task placement and scheduling with function configuration in edge computing - L. Liu et al.
        - *HEFT*: Performance-effective and low-complexity task scheduling for heterogeneous computing - H. Topcuoglu et al.
  - **Why** solve this problem?
    - **significance**: Optimize the performance of edge computing, especially for FaaS.
  - **How** to solve this problem?
    - **formulation**
      - heterogeneous edge network -> UCG(undirected connected graph）
      - IoT dependent functions -> DAGs
      - function placement and stream mapping -> function embedding
      - **objective**:
        - minimize the finish time of the slowest exit function
    - **methods**
      - DP-based Embedding
        - optimal substructure: Based on connected edges, if our objectives is to find the optimal solution of node A, we can firstly find the optimal solution of node B that connected to A. That is to say, optimal substructure appears in topological order.
        - optimal data splitting: infinity norm minimization problem, which can be solved by simplex method or interior point method. But a better solution(OSM) is proposed to find the optimal objective value directly by introducing AM-GM inequality.
        - path finding: recursive searching.
  - **Why** use this method?
    - **comments**
      - Based on observation, a more efficient calculation is proposed to solve the data spliiting problem rather than use traditional optimization methods.
    - **inspiration**
      - By careful observation, some concise/novel optimal method could be found to solve some specific problems rather than using traditional methods.
      - Actually, optimal sub-problems are obvious to find in this scenario of topological edge network, but formulation and modeling methods are worth learning.
   
### 3. IEEE Access '18 [Composition-Driven IoT Service Provisioning in Distributed Edges](https://www.researchgate.net/publication/327787725_Composition-Driven_IoT_Service_Provisioning_in_Distributed_Edges)
  - **What** is the problem?
    - **novelty**: an algorithm framework better than simple EAs
    - **keywords**: IoT, Service Composition, Service Cache
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
      - **Objective**: (similar to a backpack problem with complexity being 2^n)
        - Design a cache policy that optimizes ASRT by selecting a set of services which are cached at the edge.
    - **method**:
      - (1) A kind of random-greedy initialization algorithm
      - (2) ASRT is evaluated by greedy algorithm
      - (3) Genetic Algorithm
  - **Why** use this method?
    - **comments & inspiration**:
      - A proper random-greedy initialization is a key factor for high efficiency.
      - As a kind of evolutionary algorithm, genetic algorithm is efficient for this NP problem.
    - **problem?**:
      - Only memory resources contraint does not seem to be enough.
      - If more limitations are taken into account, how to do greedy initialization? That is, how to generate initial best solution candidates? 

  

### 4. IEEE Trans. Wirel. Commun '17 [Energy-Efficient Resource Allocation for Mobile-Edge Computation Offloading](https://ieeexplore.ieee.org/document/7762913)




---

## II. Optimization Related Papers
### 1. AAAI '16 [Derivative-Free Optimization via Classification](https://www.researchgate.net/publication/303487232_Derivative-Free_Optimization_via_Classification)
  - **What** is the problem?
    - **novelty**: continuous domains research of SAC algo
    - **keywords**: Derivative-free, Error-target Dependence, Randomized Coordinate Shrinking
    - **problem description**: The author analysed a range of EAs from the perspective of statistics, and proposed a learning framework which is able to mimic some of EAs.
    - **related work**:
      - (1) theorical studies of EAs:
        - Analyzing Evolutionary Algorithms - T.Jansen et al.
        - Theory of Randomized Search Heuristics - Foundations and Recent Development - A. Auger et al.
      - (2) effects of cross-over operators, polulation size, etc:
        - The analysis of evolutionary algorithms - A proof that crossover really can help - T. Jansen et al.
        - On the choice of the offspring population size in evolutionary algorithms - T. Jansen et al.
      - (3) general framework of EAs
        - Model-based search for combinational optimization: A critical survey - M. Zlochin et al.
  - **Why** solve this problem?
    - **significance**:
      - This paper analyzed SAC algorithms in **continuous domains** while other studies mainly focus on discrete domains.
      - This paper gives lower and upper bound of QAA complexity of a range of EAs with **theorical proofs**.
  - **How** to solve this problem?
    - **formulation**:
      - **terms**:
        - (1) hamming distance: the number of differences of two vector or two strings.
        - (2) probable-absolute-approximate(PAA) query complexity: the number of calls to f(.) such that, with probability at leat 1-P to find a solution x with f(x) < a.
        - (3) sphere function class & spike function class(non-convex, non-differentiable)
    - **methods**:
      - (1) The sampling-and-learning(SAL) is an abstract summary of a range of EAs.
      - (2) In the SAL framework, learning a hypothesis h_(t) allows to take the current data set, the last data set and the last hypothesis h_(t-1) into account.
  - **Why** use this method?
    - **inspiration**:
      - (1）SAL looks an interesting algorithm in simulating PSO algorithm. Sampling from **positive region and global region** from the lastest hypothesis is similar to PSO in which velocity of each particle will be updated both **globally** and **personlally**.
      - (2) "An accurate learning algorithm may not be necessary for a good SAC algorithm." Let's learn more from [On the complexity of trial and error](https://www.researchgate.net/publication/224907207_On_the_Complexity_of_Trial_and_Error)

### 2. CEC '14 [The Sampling-and-Learning Framework: A Statistical View of Evolutionary Algorithms](https://www.researchgate.net/publication/259893738_The_Sampling-and-Learning_Framework_A_Statistical_View_of_Evolutionary_Algorithms#fullTextFileContent)

### 3. CEC '16 [On Sampling-and-Classification Optimization in Discrete Domains](https://www.researchgate.net/publication/303487011_On_Sampling-and-Classification_Optimization_in_Discrete_Domains)

---

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


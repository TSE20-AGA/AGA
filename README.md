# AGA: An Accelerated Greedy Additional Algorithm for Test Case Prioritization

This is the website of paper "AGA: An Accelerated Greedy Additional Algorithm for Test Case Prioritization", which has been submitted to TSE.

## Summary

In this paper, we target the Greedy Additional (GA) algorithm, which greedily schedules the execution order of test cases and we propose the Accelerated Greedy Additional (AGA) algorithm to improve the efficiency of GA while preserving its effectiveness. 

The contributions of this paper can be summarized as five-folds:

1. The first attempt to improve the efficiency of GA while preserving its effectiveness, since GA is believed to have high effectiveness.
2. An approach to accelerating the widely-known GA algorithm through two parts, including time complexity reduction and iteration number reduction.
3. A large scale experiment on 55 open-source projects demonstrating the effectiveness and efficiency of our AGA approach, compared with the GA algorithm.
4. An empirical comparison of our AGA approach with *FAST*, which improves time efficiency but decreases effectiveness.
5. An industrial case study on 22 subjects from Baidu, which indicates the practical usage of AGA in real-world scenarios.



## Basic information of our subjects

### Open-source

The basic information of our 55 open-source subjects is shown [here](Basic_Information/opensource.pdf). For each subject, the first column is the ID in the paper and the second column is the corresponding full name. The last four columns show the SLOC, TLOC, #Test Cases, and #Mutants of each subject. The last row calculates the sum of them.

### Industry

The basic information of our 22 industrial subjects is shown in the paper. Note that for the company's confidentiality, we hide the project names and report rough scale of SLOC.

## Input data

### Open-source

The input data of our 55 open-source subjects are shown [here](Input_Data/opensource/). For each subject, the corresponding directory contains four files. "testList" contains the names of all test cases, and their IDs start from 1. "stateMatrix.txt" contains the coverage table: each row represents one test case while each column represents one statement, and "1" means covered while "0" means uncovered. "state-map.txt" contains another form of the coverage table: each row represents one test case and it shows all statement IDs covered by this test case. "mutantKillMatrix" contains the kill information, where each row represents a test case and each column represents a mutant, and "1" means the corresponding test case kills the corresponding mutant while "0" means the opposite. P.S. Due to the 100M limit of file size on GitHub, we delete commons-math/mutantKillMatrix, commons-math/stateMatrix.txt, and camel-core/stateMatrix.txt.

The other form of input (adjacency list) can be obtained from "mutantKillMatrix" (adjacency matrix). We do not put them here because they are redundant.

### Industry

The input data of our 22 industrial subjects is hidden because of the company's confidentiality.



## Code

The code of AGA is present [here](Code/AGA.py) (based on both adjacency matrix and adjacency list).

The code of our implementation of GA (based on adjacency matrix) is present [here](Code/GA.py).

The code of *FAST* is present on this [website](https://github.com/icse18-FAST/FAST). (Note that we also reuse their implementation of GA (based on adjacency list).)



## Results

We report the results on adjacency list in the paper because we reuse the implementation of GA in [16] and the results are somewhat more reliable. Here, as we say in the paper, we present the results based on adjacency matrix, which means all of the implementations including AGA and GA assume adjacency matrix as the input format.

### RQ1 (the same as the paper)

The results for RQ1 are shown [here](Results/RQ1/). There are folders named by subject names. We report two files for each subject. In "apfd_results.csv", the first column represents the number of iterations to apply GA strategy and the second column represents the corresponding APFD value. In "TimeGAMethod", row i represents the time cost of the algorithm that repeats the GA strategy for i iterations.

### RQ2

The results for RQ2 are shown [here](Results/RQ2/). For each subject, the first column represents its ID, the last three columns represent the time costs of GA-first, GA, and AGA_C, respectively.

### RQ3

The results for RQ3 are shown [here](Results/RQ3/). We separate effectiveness and efficiency into two files. For effectiveness, for each subject, the first column represents its name, the last three columns represent the APFD values of GA-first, GA, and AGA, respectively. For efficiency, for each subject, the first column represents its name, the last three columns represent the time costs of GA-first, GA, and AGA, respectively.

### Empirical Comparison with *FAST*

The results for the empirical comparison with *FAST* are shown [here](Results/FAST/). For each subject, the first column represents its name, the second and the third columns represent the APFD values of AGA and *FAST*, and the forth and the last columns represent the time costs of AGA and *FAST*.

### Industrial Case Study

The results for the industrial case study are shown [here](Results/Industry). In file industry.csv, for each subject, the first column represents its ID, and remaining three columns represent the time cost of GA, AGA, and *FAST*, respectively.










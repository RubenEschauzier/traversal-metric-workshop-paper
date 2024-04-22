## Introduction
{:#introduction}

1. Talk about why we need LTQP
2. Introduce how link prioritiation can improve the effectiveness of LTQP in real-world applications
3. Explain the difficulty in discerning the marginal effect of link prioritization on query performance due to
    1. Differences in optimization strategies of different query engines  
    2. Usage of different languages (implementation in C might be faster than javascript, but fulfill different purposes so not a fair comparison)
    3. Variance in document request time
4. Draw parallel with join optimization and the number of intermediate results, as this also is a good way to get the marginal effect of join optimization
5. Research question: How can we design a metric to allow the comparison of the marginal algorithmic performance of link prioritization algorithms between different query engines?
6. Introduce the idea of the metric
    1. Represent the algorithmic performance of link prioritization algorithms independent of total query engine performance, thus allowing easy cross-engine comparisons
    2. Provide the optimal perfromance of link priortization algorithms to indicate how much performance is still available for link priorization algorithms

## Introduction
{:#introduction}

When using structured decentralized environments like Solid in applications, it's important to use querying approaches capable of handling numerous small, decentralized data stores. Additionally, as these vaults may contain sensitive data, querying must support fine-grained access control.

Link Traversal-based Query Processing (LTQP) is a promising approach that meets these requirements. LTQP is an integrated querying method where the query engine dynamically discovers sources by following hyperlinks found in previously dereferenced documents.

In LTQP, the arrival times of the first $$ k $$ results can be improved by prioritizing links likely to be relevant to the query. By initially dereferencing data sources relevant to the query, the query engine can quickly begin producing results. On the other hand, if irrelevant data is dereferenced first, the query engine spends time processing data that won't produce results, slowing down query execution.

Previous work has utilized result arrival times and total execution time to assess the performance of link prioritization algorithms. 
While this approach is sufficient when comparing link prioritization algorithms within the same engine and environment, it falls short when comparing different engine implementations and environments.
Specifically, several aspects complicate performance comparisons:

1. _Query Optimization Strategies:_ Different LTQP implementations may use different query optimization strategies unrelated to link prioritization, such as improvements in query planning. 
2. _Programming Languages:_ The languages used across different LTQP implementations can vary. 
These differences can substantially affect engine performance, making it challenging to compare algorithms based solely on execution time.
3. _Dereferencing Links:_ In real-world applications, the time required to dereference links can vary widely. This variability introduces significant noise into query execution times, complicating the comparison of link prioritization performance even within the same engine.

In short, measuring the marginal effect of link prioritization algorithms is challenging. 
In comparison, we can measure the marginal effectiveness of join planning relatively easily by counting the number of intermediate results produced by the engine. 
The goal of this paper is to introduce a metric that enables straightforward observation of the algorithmic performance of link prioritization approaches, independent of implementation details. 
This leads to our research question: _How can we design a metric to compare the marginal algorithmic performance of link prioritization algorithms independently of implementation details?_

<!-- 
1. Talk about why we need LTQP
2. Introduce how link prioritiation can improve the effectiveness of LTQP in real-world applications
3. Explain the difficulty in discerning the marginal effect of link prioritization on query performance due to
    1. Differences in optimization strategies of different query engines  
    2. Usage of different languages (implementation in C might be faster than javascript, but fulfill different purposes so not a fair comparison)
    3. Variance in document request time
4. Draw parallel with join optimization and the number of intermediate results, as this also is a good way to get the marginal effect of join optimization
5. Research question: How can we design a metric to allow the comparison of the marginal algorithmic performance of link prioritization algorithms independent from implementation details?
6. Introduce the idea of the metric
    1. Represent the algorithmic performance of link prioritization algorithms independent of total query engine performance, thus allowing easy cross-engine comparisons
    2. Provide the optimal perfromance of link priortization algorithms to indicate how much performance is still available for link priorization algorithms -->

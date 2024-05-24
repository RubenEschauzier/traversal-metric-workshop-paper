## Introduction
{:#introduction}
When using structured decentralized environments like Solid in applications, querying approaches that can handle the large number of small decentralized datastores in the environments are required.
Furthermore, as possibly sensitive data is stored in the vaults, querying should support fine-grained access control.
Link Traversal-based Query Processing (LTQP) is a possible candidate that satisfies these requirments.
LTQP is an integrated querying approach where the query engine dynamically discovers sources by following hyperlinks discovered in documents of previously dereferenced URIs.
In LTQP, we can optimize the arrival times of the first $$ k $$ results by prioritizing links that are likely relevant to the query [](cite:cites hartig2016walking, lynden2013hybrid).
If the query engine first dereferences data sources relevant to the query, we can quickly start producing query results, while if we first dereference irrelevant data, the query engine is stuck processing data that will not produce results.

Previous work has used the result arrival times and total execution time to measure the performance of link prioritization algorithms. 
While this approach is sufficient when comparing link prioritization algorithms within the same engine and environment, it falls short when comparing different engine implementations and environments.
Specifically the following possible diprecancies complicate link priortization performance comparisons.

1. Different LTQP implementations can employ varying query optimization strategies unrelated to link prioritization, like query planning improvements. 
2. Between LTQP implementations different languages may be used. These differences can significantly impact engine performance, which makes comparing algorithms by execution time difficult.
3. In real-world applications, the time required to dereference links is highly variable. This variance will be reflected in query execution times and is a source of irreducable noise when comparing link priorization performance, even when using the same engine.

In short, measuring the marginal effect of link prioritization algorithms is difficult.
In comparison, we can measure the marginal effectiveness of join planning relatively easily by counting the number of intermediate results produced by the engine.
The goal of this paper is to introduce a metric that would allow us to easily observe the algorithmic performance of link prioritization approaches regardless of implementation details.
Thus, leading to our research question: _How can we design a metric to allow the comparison of the marginal algorithmic performance of link prioritization algorithms independent from implementation details?_

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

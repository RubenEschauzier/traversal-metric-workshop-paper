## Introduction
{:#introduction}

Currently, web user data is stored in centralized data silos, which restricts innovation and poses privacy concerns [](cite:cites Verborgh_2020). 
Decentralization efforts like Solid propose a different approach, spreading user data across multiple personal small data stores at various locations. 
This data is highly personal and permissioned, requiring a querying approach capable of handling decentralized and permissioned data effectively.

Link Traversal-based Query Processing (LTQP) is an integrated querying approach designed to meet these [requirements](cite:cites Verborgh_2024).
Starting from _seed_ data sources, the LTQP query engine dynamically discovers new data sources by following hyperlinks found in previously discovered documents.

However, LTQP is currently slower compared to centralized alternatives. 
An optimization avenue is link prioritization, where the engine dynamically determines the order in which links should be dereferenced based on their expected relevance to the query [](cite:cites taelman2023link, hartig2016walking).
To optimize LTQP prioritization strategies, researchers need insights into the marginal performance of proposed algorithms and the theoretically optimal performance these strategies can achieve.

Existing literature on performance measures is insufficient.
Previous studies have utilized metrics like result arrival times, total execution time, and other [arrival time-based metrics](cite:cites acosta2017diefficiency) to assess the performance of different prioritization strategies [](cite:cites taelman2023link, hartig2016walking, hanskiobservations). 
However, these metrics fall short when comparing different engine implementations and environments as actual prioritization-related performance changes are obscured by these unrelated differences that may skew results: 

Programming Languages
: Different languages can substantially affect engine [performance](cite:cites fourment2008comparison), hindering purely time-based comparisons of algorithms.

Dereferencing Overhead
: Network communication times [vary widely](cite:cites christiansen2000tuning, kobayashi2002analysis), introducing significant noise into execution times, even for comparisons of the same engine.

Orthogonal Optimization Strategies
: Different [query optimization](cite:cites hartig2011zero) strategies might create differences in performance independent of prioritization strategies. 

Moreover, current measures do not provide insights into how far implemented prioritization approaches are from the theoretically optimal prioritization strategy.

This leads to our research question: _How can we compare the marginal algorithmic performance of prioritization algorithms in an implementation-agnostic manner_?
In this paper, we introduce the metric: Shortest Traversal Length Ratio (STLR). 
This metric allows for straightforward observation of the algorithmic performance of prioritization approaches, independent of implementations, and provides a benchmark against the theoretically optimal prioritization strategy.

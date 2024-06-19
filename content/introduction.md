## Introduction
{:#introduction}

Currently, web user data is stored in centralized data silos, restricting innovation [](cite:cites Verborgh_2020). 
Rather than storing all user data of a single application in a single location, decentralization efforts such as Solid adopt an approach that spreads data into smaller stores at different locations.
This data is highy personal and permissioned, and cannot be centralized, requiring a querying approach that can handle permissioned decentralized data.
Link Traversal-based Query Processing (LTQP) is an integrated querying approach that meets these [requirements](cite:cites Verborgh_2024). 
Starting from a _seed_ data source, the LTQP query engine dynamically discovers new data sources by following hyperlinks found in previously discovered documents.

Currently, LTQP is slow compared to centralized alternatives.
An avenue for optimization is link prioritization, in which an engine dynamically determines the [order](cite:cites taelman2023link, hartig2016walking) in which links should dereferenced in accordence to its expected relevance to the query.
To optimize LTQP prioritization strategies, researchers require insight into the marginal performance of proposed algorithms and the theoretically optimal performance prioritization strategies can achieve.
Currently, the literature on performance measures is insufficient. 
[Previous work](cite:cites taelman2023link, hartig2016walking, hanskiobservations) has utilized result arrival times, total execution time, and other [arrival time-based metrics](cite:cites acosta2017diefficiency) to assess the performance of different prioritization strategies. 
This falls short when comparing different engine implementations and environments, as actual prioritization-related performance changes are obscured by these unrelated differences that may skew results: 

Programming Languages
: Different languages can substantially affect engine [performance](cite:cites fourment2008comparison), hindering pure time-based comparisons of algorithms.

Dereferencing Overhead
: Network times [vary widely](cite:cites christiansen2000tuning, kobayashi2002analysis), introducing significant noise into execution times, even for comparisons of the same engine.

Orthogonal Optimization Strategies
: Different [query optimization](cite:cites hartig2011zero) strategies might create differences in performance independent of prioritization strategies. 

Furthermore, the used measures give no insight into how far implemented prioritization approaches are from the theoretical optimal _prioritization_ strategy.

In this paper, we introduce the metric: Shortest Traversal Length Ratio (STLR), that enables straightforward observation of the algorithmic performance of prioritization approaches, independent of implementations and provides a measure against the theoretically optimal priortization strategy. 
This leads to our research question: _How to compare the marginal algorithmic performance of prioritization algorithms in an implementation-agnostic manner?_

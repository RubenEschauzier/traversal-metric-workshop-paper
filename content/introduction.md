## Introduction
{:#introduction}

Currently, web user data is stored in centralized data silos, restricting innovation[](cite:cites Verborgh_2020). 
Rather than storing all user data of a single application in a single location, decentralization efforts, like Solid, adopt an approach that spreads data into smaller stores at different locations.
When applications intend to use decentralized data, querying approaches capable of handling numerous small, decentralized data stores are required. 
Additionally, as these vaults may contain sensitive data, querying must support fine-grained access control.
Link Traversal-based Query Processing (LTQP) is an integrated querying approach that meets these requirements. 
Starting from a 'seed' data source, the LTQP query engine dynamically discovers new data sources by following hyperlinks found in previously discovered documents.
In LTQP, the arrival times of the first $$ k $$ results can be [improved](cite:cites taelman2023link) by prioritizing links likely relevant to the query. 
By initially dereferencing data sources relevant to the query, the query engine can quickly begin producing results. 
On the other hand, if irrelevant data is dereferenced first, the query engine spends time processing data that won't produce results, slowing down query execution.
By streaming the first results quickly [](cite:cites koudas2005data), applications can already start presenting these results to clients. 
For example, an application can quickly present the first few query results, while hiding the yet-to-be-produced results behind a scrollbar.

[Previous work](cite:cites taelman2023link, hartig2016walking) has utilized result arrival times and total execution time to assess the performance of different traversal strategies. 
While this approach is sufficient when comparing traversal strategies within the same engine and environment, it falls short when comparing different engine implementations and environments.
This downside also holds for other execution time-based metrics, like [diefficiency](cite:cites acosta2017diefficiency).
Specifically, several aspects complicate performance comparisons:

1. _Query Optimization Strategies:_ Different LTQP implementations may use different [query optimization](cite:cites hartig2011zero) strategies unrelated to traversal strategies, such as improvements in query planning. 
2. _Programming Languages:_ The languages used across different LTQP implementations can vary. 
These differences can substantially affect engine [performance](cite:cites fourment2008comparison), making it challenging to compare algorithms based solely on execution time.
3. _Dereferencing Overhead:_ In real-world applications, the time required to dereference links can [vary widely](cite:cites christiansen2000tuning, kobayashi2002analysis). This variability introduces significant noise into query execution times, complicating the comparison of traversal strategies performance even within the same engine.

In short, measuring the marginal effects of different traversal strategies is difficult. 
Additionally, current metrics do not reveal how far current traversal methods are from the optimal solution. 
Consequently, the potential performance improvements from exploring new traversal strategies are unknown and uncertain.

To address this, we propose a new metric: the Shortest Traversal Length Ratio (STLR). 
STLR allows for the evaluation of traversal strategies by comparing their performance to the optimal traversal path.
This metric will guide future research by highlighting the potential gains from investigating new traversal strategies. 
Furthermore, it will allow the comparison of traversal strategies independent of implementation details.
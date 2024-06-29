## Existing Metrics
{:#existingmetrics}
Existing LTQP metrics are insufficient for measuring the marginal algorithmic performance of link prioritization algorithms:

Query execution time
: Prioritization algorithms are unlikely to improve total query execution time [](cite:cites hartig2016walking, taelman2023link). However, Link prioritization can [improve](cite:cites taelman2023link, hartig2016walking) arrival times of the first $$ k $$ results. However, the arrival times are influenced by both prioritization strategies and other unrelated engine optimizations obscuring the prioritization algorithm's effect.

Diefficiency Metrics
: Diefficiency metrics measure the continuous efficiency of query engines by reflecting the density of produced results over a given time interval [](cite:cites acosta2017diefficiency). This is in contrast to measuring the first $$ k $$ arrival times, which only measures engine performance at discrete points. However, as these metrics are based on result arrival times, the same limitations remain.

Number of HTTP Requests
: The number of HTTP requests directly represents the number of dereferenced documents, thus measuring the engine's ability to prune irrelevant links. However, HTTP request do not reveal the performance of _prioritization_ algorithms, which reorder rather than prune links.

The metric proposed in this paper complements existing metrics by specifically measuring the marginal performance of link prioritization algorithms rather than the overall performance of the LTQP system.

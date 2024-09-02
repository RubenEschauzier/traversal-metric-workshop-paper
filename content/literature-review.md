## Existing Metrics
{:#existingmetrics}
Existing LTQP and federated querying [metrics](cite:cites montoya2012benchmarking) are insufficient for measuring the marginal algorithmic performance of link prioritization algorithms:

Query execution time
: Prioritization algorithms are unlikely to improve total query execution time [](cite:cites hartig2016walking, taelman2023link). However, Link prioritization can [improve](cite:cites taelman2023link, hartig2016walking) arrival times of the first $$ k $$ results. However, the arrival times are influenced by both prioritization strategies and other unrelated engine optimizations obscuring the prioritization algorithm's effect.

Diefficiency Metrics
: Diefficiency metrics measure the continuous efficiency of query engines by reflecting the density of produced results over a given time interval [](cite:cites acosta2017diefficiency). This is in contrast to measuring the first $$ k $$ arrival times, which only measures engine performance at discrete points. However, the same limitations remain, as these metrics are based on result arrival times.

Number of HTTP Requests

: For federated query engines, the number of HTTP requests represents the efficiency of source selection and join planning during query execution [](cite:cites peng2019optimizing, schmidt2011fedbench). Federated engines often query SPARQL endpoints, allowing them to delegate parts of the query execution to the server [](cite:cites schwarte2011fedx). In contrast, in LTQP, the engine uses HTTP requests to download documents, so the number of requests corresponds to the number of dereferenced documents. Thus, the number of HTTP requests measures the engine's ability to prune irrelevant links. However, it does not indicate the effectiveness of _prioritization algorithms_, which reorder link dereference order, rather than pruning links.

The metric proposed in this paper complements existing metrics by measuring the marginal performance of link prioritization algorithms rather than the overall performance of the LTQP system.

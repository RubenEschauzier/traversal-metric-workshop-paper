## Existing Metrics
{:#existingmetrics}
Existing LTQP metrics are insufficent measures for marginal algorithmic performance of link prioritization algorithms:

Total query processing time
: Prioritization algorithms are unlikely to improve total query execution time, as completing a query requires dereferencing all documents, as prioritization algorithms do not prune links [](cite:cites hartig2016walking). Instead, it measures total LTQP engine performance, which includes overhead incurred from prioritization algorithms.

Arrival times of the first $$ k $$ results
: Link prioritization can [improve](cite:cites taelman2023link, hartig2016walking) arrival times of the first $$ k $$ results, by quickly dereferencing the data needed to answer a query. By streaming the first results quickly [](cite:cites koudas2005data), applications can start presenting these results to clients. However, the arrival times are influenced by both prioritization strategies and other unrelated engine optimizations obscuring the effect of the prioritization algorithm.

Diefficiency Metrics
: Diefficiency metrics measure the continuous efficiency of query engines by reflecting the density of produced results over a given time interval[](cite:cites acosta2017diefficiency). This is in contrast to measuring first $$ k $$ arrival times, which only measure engine performance at discrete points. However, as this is similarly based on result arrival times, the same limitations remain for our application.

Number of HTTP Requests
: The number of HTTP requests directly represents the number of dereferenced documents, thus measuring the ability of an engine to prune irrelevant links. However, HTTP request do not reveal the performance of _prioritization_ algorithms, as these do not prune links, but reorder the order in which links are dereferenced.

The metric this paper proposes is complementary to existing metrics, as it allows researchers to accurately measure the marginal performance of link prioritization algorithms. Furthermore, it allows researchers insight into how much benefit can be obtained from optimizing prioritization strategies. 
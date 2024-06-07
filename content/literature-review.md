## Existing Metrics
{:#existingmetrics}

Currently, LTQP performance is evaluated using several metrics:

{:.comment data-author="BET"} (1) It seems to me that you argue a bit of the contrary in the introduction "This downside also holds for other execution time-based metrics" maybe the language can be soften here or specify that it is good for evaluation with the same condition.

1. Total query execution time: While important, traversal strategies are unlikely to improve total query execution time significantly, as completing a query requires dereferencing all documents if the traversal strategy does not involve pruning links[](cite:cites hartig2016walking). However, it is an effective metric for total LTQP engine performance.

{:.comment data-author="BET"}  (2)  The comment seems to not fully in line with the purpose of presenting those metrics, I think it should be more of a why it is good or bad instead of if we can optimize it.

2. Arrival times of the first $$ k $$ results: As discussed in the introduction, link prioritization algorithms can potentially improve this metric.

{:.comment data-author="BET"}  (3) It seems like you should critique it a bit here. I know you do it in the intro, but it feels weird a bit
to me to have it here with no comments.

3. Diefficiency Metrics: These measure the continuous efficiency of query engines by reflecting the density of produced results over a given time interval[](cite:cites acosta2017diefficiency).
 
{:.comment data-author="BET"} Maybe it is not important but I feel like the completeness of results is missing particularly if we present
fewer HTTP requests as a direct good.

4. Number of HTTP Requests: This measures the efficiency of an engine at retrieving only relevant data. Fewer HTTP requests to achieve the same results indicate effective pruning.

These existing metrics are essential for evaluating the overall performance of the entire system. The metric this paper proposes is complementary to the existing metrics. The proposed metric will allow researchers to accurately measure the system's overall performance and the specific contribution of link prioritization algorithms.


<!-- 
Currently, LTQP performance is measured using several metrics. 
The first is the total execution time of a query. While this is an important metric, traversal strategies are unlikely to improve [it](cite:cites hartig2016walking), as completing a query likely requires dereferencing all documents. 
An alternative to total execution time is the arrival times of the first $$ k $$ results, which, as discussed in the introduction, can potentially be improved by link prioritization algorithms.
Similarly, [diefficiency metrics](cite:cites acosta2017diefficiency) can be used to measure the continuous efficiency of query engines during query execution. 
Diefficiency metrics reflect the density of produced results over given time interval. 
Finally, the number of HTTP requests measures the efficiency of an engine at retrieving only relevant data. Specifically, if an engine is able to retrieve the same results with less HTTP requests, it indicates effective pruning.

These existing metrics are essential for evaluating the overall performance of the entire system. 
By introducing the proposed metric in this paper, researchers can more accurately measure both the performance of the entire system and the specific contribution of link prioritization algorithms. -->


<!-- 1. Talk about existing metrics used for comparison (short)
    1. Total execution time
    2. Diefficiency
    3. First $$ k $$ result arrival times
2. Discuss that these metrics are complementary and combining the proposed metric with these metrics will give a clear idea of performance. -->
## Existing Metrics
{:#existingmetrics}

Currently, LTQP performance is primarily measured using three metrics. 
The first is the total execution time of a query. While this is an important metric, link prioritization algorithms are unlikely to improve [it](cite:cites hartig2016walking), as completing a query requires dereferencing all documents. 
The second metric is the arrival times of the first $$ k $$ results, which, as discussed in the introduction, can potentially be improved by link prioritization algorithms.
Finally, [diefficiency metrics](cite:cites acosta2017diefficiency) can be used to measure the continuous efficiency of query engines during query execution.<span class="comment" data-author="RT">This needs more details</span>

<span class="comment" data-author="RT">Number of HTTP reqs is also a relevant metric for LTQP perf.</span>

These existing metrics are essential for evaluating the overall performance of the system. 
By introducing the proposed metric in this paper, researchers can more accurately measure both the performance of the entire system and the specific contribution of link prioritization algorithms.
<!-- 1. Talk about existing metrics used for comparison (short)
    1. Total execution time
    2. Diefficiency
    3. First $$ k $$ result arrival times
2. Discuss that these metrics are complementary and combining the proposed metric with these metrics will give a clear idea of performance. -->
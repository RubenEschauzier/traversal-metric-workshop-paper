## Existing Metrics
{:#existingmetrics}

Currently, LTQP performance is primarily measured with three metrics. First, is the total execution time of a query. While this is an important metric to track, link prioritization algorithms are unlikely to improve it [](cite:cites hartig2016walking), as finishing a query requires all documents to be dereferenced. Second, the literature uses first $$ k $$ result arrival times [](cite:cites taelman2023link), which, as discussed in the introduction, can likely be improved by link prioritization algorithms. Finally, [diefficiency metrics](cite:cites acosta2017diefficiency) can be used to measure the continuous efficiency of query engines.

The previously mentioned metrics are important to measure the entire system performance.
By adding the proposed metric of this paper to the metric toolkit, researchers can accuractely measure the performance of the whole system, and  the link prioritization part of their system seperately.

<!-- 1. Talk about existing metrics used for comparison (short)
    1. Total execution time
    2. Diefficiency
    3. First $$ k $$ result arrival times
2. Discuss that these metrics are complementary and combining the proposed metric with these metrics will give a clear idea of performance. -->
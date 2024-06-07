## Conclusion & Future Work
{:#conclusion}


In this paper, we introduced a preliminary, implementation-independent metric to measure the algorithmic performance of link prioritization algorithms during LTQP. 
Early results show that while depth-first traversal outperforms breadth-first traversal algorithmically, this difference is not reflected in execution time. 
This supports the hypothesis that SolidBench Discover queries are unlikely to benefit from traversal strategy improvements [](cite:cites eschauzier2023does).

{:.comment data-author="BET"} I guess I am unsure of what traversal strategy is if it is only the prioritization I see it and the paper from Hartig also proves it but if it includes running at least in my experiment I was able to have better performance for some queries.

To improve the metric, we plan several extensions. 
First, we will include a metric for the first $$ k $$ results, defined as the ratio between the length of the path the engine takes to dereference the documents for $$ k $$ results and the optimal path to dereference $$ k $$ results. 
This is challenging because computing the optimal path for $$ k $$ results requires solving Steiner trees for all combinations of size $$ k $$ out of $$ n $$, where $$ n $$ is the total number of results.
Second, we will incorporate a penalty term for documents with long HTTP request times to account for real-world uncertainties in LTQP scenarios. 
Finally, we will conduct more extensive benchmarks and provide easy-to-use code repositories to reproduce and utilize the introduced metrics.

<div style="page-break-after: always; visibility: hidden"> 
\pagebreak 
</div>
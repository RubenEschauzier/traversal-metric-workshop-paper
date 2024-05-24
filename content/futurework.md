## Conclusion & Future Work
{:#conclusion}
In this paper, we introduced a preliminary version and vision for an implementation-independent metric to measure the algorithmic performance of link prioritization algorithms in LTQP. Early results show....

To improve the metric, we plan to extend it in several directions. 
First, we aim to include the metric for the first $$ k $$ results. 
Similar to the metric proposed in this paper, it will be defined as the ratio between the length of the path the engine takes to dereference the documents for $$ k $$ results and the optimal path to dereference $$ k $$ results. 
However, this is challenging because computing the optimal path to dereference $$ k $$ results currently requires computing Steiner trees for all combinations of size $$ k $$ out of $$ n $$, with $$ n $$ being the total number of results.
Second, we intend to include a penalty term for documents that require long HTTP request times, to account for the uncertainty in real-world LTQP scenarios.
Finally, we will conduct more extensive benchmarks and provide easy-to-use code repositories to reproduce and utilize the introduced metrics.

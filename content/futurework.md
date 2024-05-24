## Conclusion \& Future Work
{:#conclusion}
In this paper we introduced a preliminary version and vision for an implementation independent metric that measures the algorithmic performance of link prioritization algorithms in LTQP. Early results show ...
To improve the metric a few open questions remain. 
First, we would like to include the metric for the first $$ k $$ results. 
This metric would be defined as the division between the lenght of the path the engine takes to dereference the documents for $$ k $$ results, divided by the optimal path to dereference $$ k $$ results.
This, however, is challenging as computing the optimal path to dereference $$ k $$ results currently requires computing steiner trees for all combinations of size $$ k $$ out of $$ n $$, with $$ n $$ the total number of results.
Second, we would like to include a penalty term for documents that require long http requests times, to account for uncertainty in a real-world LTQP scenario.
Finally, when introducing the metric we will execute more extensive benchmarks and include easy to use code repositories to reproduce and use the introduced metrics.


## Method
{:#Method}
In this section we will formally introduce the metric, explain its components, and finally discuss what information query engines should track to compute it.

1. The metric is defined as the length of the path taken by the query engine untill all documents required for the full query answer are reached divided by the length of the optimal traversal path computed in hindsight.
2. Lower is better, as it means that the traversal path is closer to optimal
3. The first $$ k $$ version of the metric is defined as the length of the path untill all documents required for $$ k $$ out of $$ n $$ results are dereferenced divided by the optimal path to get all documents needed for $$ k $$ results.
4. This is computationally intensive, as the current implementation computes shortest paths for all combinations of size $$ k $$ out of $$ n $$ results.
5. To compute this metric, the engine should track the dereference order of links and the parent - child relations between documents.


## Relevant Retrieval Ratio
{:#Method}

The [subweb](cite:cites hartig2012foundations) traversed during LTQP can be represented as a directed graph, where an edge from document A to document B indicates that a URI pointing to document B was first discovered in the data obtained from document A. 
[](#example-metric) shows an example of such a directed graph.

During LTQP query execution, an optimal link dereference order that finds all documents needed to answer a query exists, as shown in the right-most directed graph in [](#example-metric).
This theoretical optimum can be considered an oracle link prioritization algorithm with perfect information on the location of query-relevant documents.
The optimal path can always be achieved, as the oracle only uses links between documents that an engine could also use.
An engine should strive to achieve a traversal path close to this optimal path.
As such, we use the ratio between the optimal traversal path length and the actual traversal path length during query execution to evaluate the performance of link prioritization algorithms.
The optimal traversal path is defined as the shortest path needed to dereference all documents required for the complete query result and is determined retrospectively.

Given the length of the optimal traversal path and the actual traversal path, we define the $$ R^3 $$ metric as

$$
\begin{aligned}
 R^{3} = \dfrac{|T_{O}|}{|T_{E}|}, \quad \quad |T_{O}|, \: |T_{E}| > 0
\end{aligned}
$$

where $$ |T_{E}| $$ is the length of the engine traversal path and $$ |T_{O}| $$ is the length of the optimal path. 
In this definition, a higher value is better, with $$ R^{3} = 1 $$ indicating optimal algorithmic link prioritization performance.
Note that when $$ |T_{O}| = 0 $$ or $$ |T_{E}| = 0 $$, our query has no results and the notion of optimal link prioritization does not exist.
When an engine performs poorly, resulting in smaller differences in the metric's values, taking the log2 can help visualize relative differences.

Using the $$ R^{3} $$ metric, we can compare the algorithmic efficiency of the two traversal algorithms in our example. 
Using breadth-first search, the path to dereference the query-relevant document contains six nodes, while the optimal traversal order contains two. 
Thus, the $$ R^3 $$ metric for breadth-first traversal equals $$ 0.33 $$. 
Depth-first visits only three nodes, yielding an $$ R^3 $$ value of $$ 0.67 $$.
From this analysis, we can conclude that depth-first traversal outperforms breadth-first traversal on this subweb.

To find the optimal traversal path to dereference all query-relevant documents, we notice that it is equivalent to solving the [directed Steiner tree problem](cite:cites 
zosin2002directed) on our directed graph, with the query-relevant documents serving as terminals.
As such, we can use existing Steiner tree solvers to efficiently find our optimal traversal path.



<figure id="example-metric">
<img src="figures/example_traversal_for_metric.svg">
<figcaption markdown="block">
An example [subweb](cite:cites hartig2012foundations) showing the differences in traversal paths between breadth-first and depth-first methods, as well as the optimal traversal path.
</figcaption>
</figure>
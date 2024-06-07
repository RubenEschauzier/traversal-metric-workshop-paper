## Optimal Traversal Metric
{:#Method}
In this section, we will introduce the metric, and its components, and discuss what information query engines should track to compute it.

### Definition
{:##definition}
To measure the algorithmic performance of link prioritization algorithms, we use the ratio of the length of the effective traversal path to the optimal traversal path during query execution. 
The optimal traversal path is defined as the shortest path needed to dereference all documents required for the complete query result and is determined retrospectively.

{:.comment data-author="BET"} Maybe the end "and is determined retrospectively" could be a second sentence.

The web traversed during LTQP can be represented as a directed graph, where an edge from document A to document B indicates that a URI pointing to document B was found in the data obtained from document A. 
Finding the shortest path to dereference all query-relevant documents in this graph is equivalent to solving a [directed Steiner tree problem](cite
zosin2002directed), with the query-relevant documents serving as terminals.

The traversal path taken by the engine is defined as the sequence of documents dereferenced by the engine to obtain all necessary documents for the complete query result. 
Given the lengths of these paths, the metric is defined as:


$$
\begin{aligned}
  \phi_{optimal} = \dfrac{|T_{E}|}{|T_{O}|},
\end{aligned}
$$



where $$ |T_{E}| $$ is the length of the engine traversal path and $$ |T_{O}| $$ is the length of the optimal path. 
In this definition, a lower value is better, with $$ \phi_{optimal} = 1 $$ indicating optimal algorithmic link prioritization performance.

To compute the metric, we first track the traversed topology of the queried web and convert it into a directed graph. Furthermore, for each query, we compute the minimal set of documents required to produce the query result. 
Finally, the engine's traversal path must be tracked, either within the engine or by recording the HTTP requests made by the engine.

{:.comment data-author="BET"} to do that do we need to parsed the knowledge graph dataset into a topology graph? Or we perform queries? What if the
method prune too much data sources?

### Experimental Set-up
{:##experiment}

For our experiments, we will use the [SolidBench benchmark](cite:cites taelman2023link) to test our link prioritization metric. 
We will use the Discover queries from SolidBench, as these often produce results without timing out, which is necessary for computing our metric.

To track the required information for computing the metric during query execution, we use the modular query engine [Comunica](cite:cites taelman2018comunica).
Our experiments will compare [depth-first traversal and breadth-first traversal](cite:cites hartig2016walking) using the optimal traversal metric and time until the final query result.

{:.comment data-author="BET"} Maybe a very small description of what depth-first traversal and breadth-first traversal are. But it might not be necessary.

To compute the optimal path, we will use a [heuristic Steiner tree solver](cite:cites watel2016practical) to speed up computations. Although an exact solver would be ideal, it would significantly increase the computational complexity.


{:.comment data-author="BET"} I think information about the theoretical complexity should be provided here and maybe mention notable optimization or information about the reliability of the results with the heuristic approach. The complexity may be in the definition.
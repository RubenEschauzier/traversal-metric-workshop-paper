## Optimal Traversal Metric
{:#Method}
In this section, we will introduce the metric, and its components, and discuss what information query engines should track to compute it.

### Definition
{:##definition}
To measure the algorithmic performance of link prioritization algorithms, we use the ratio of the length of the effective traversal path to the optimal traversal path during query execution. 
The optimal traversal path is defined as the shortest path needed to dereference all documents required for the complete query result and is determined retrospectively.

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

### Experimental Set-up
{:##experiment}

For our experiments, we will use the [SolidBench benchmark](citetaelman2023link) to test our link prioritization metric. 
We will use the Discover queries from SolidBench, as these often produce results without timing out, which is necessary for computing our metric.

To track the required information for computing the metric during query execution, we use the modular query engine [Comunica](citetaelman2018comunica).
Our experiments will compare [depth-first traversal and breadth-first traversal](cite:cites hartig2016walking) using the optimal traversal metric and time until the final query result.

To compute the optimal path, we will use a [heuristic Steiner tree solver](citewatel2016practical) to speed up computations. Although an exact solver would be ideal, it would significantly increase the computational complexity.
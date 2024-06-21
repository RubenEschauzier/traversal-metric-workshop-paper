## Shortest Traversal Length Ratio
{:#Method}
In this section, we will introduce the Shortest Traversal Length Ratio, and its components, and discuss what information query engines should track for its computation.

During LTQP query execution, there exists an optimal order in which links should be dereferenced to find all documents needed to answer a query. 
This theoretical optimum can be considered an oracle link prioritization algorithm with perfect information on the location of query-relevant documents.
In theory, this optimal path can always be achieved, as the oracle only uses links between documents that an engine could also use.
An engine should strive to achieve a traversal path close to this optimal path.
Thus, to measure the algorithmic performance of link prioritization algorithms, we use the ratio of the length of the optimal and effective traversal path during query execution. 
The optimal traversal path is defined as the shortest path needed to dereference all documents required for the complete query result and is determined retrospectively.

The [subweb](cite:cites hartig2012foundations) traversed during LTQP can be represented as a directed graph, where an edge from document A to document B indicates that a URI pointing to document B was first found in the data obtained from document A. 
Finding the shortest path to dereference all query-relevant documents in this graph is equivalent to solving a [directed Steiner tree problem](cite:cites 
zosin2002directed), with the query-relevant documents serving as terminals.
The traversal path taken by the engine is defined as the sequence of documents dereferenced by the engine to obtain all necessary documents for the complete query result. 
Given the lengths of these paths, the metric is defined as:

$$
\begin{aligned}
  \phi_{optimal} = \dfrac{|T_{O}|}{|T_{E}|}, \quad \quad |T_{O}|, \: |T_{E}| > 0
\end{aligned}
$$

where $$ |T_{E}| $$ is the length of the engine traversal path and $$ |T_{O}| $$ is the length of the optimal path. 
In this definition, a higher value is better, with $$ \phi_{optimal} = 1 $$ indicating optimal algorithmic link prioritization performance.
Note that when $$ |T_{O}| = 0 $$, our query has no results and the notion of optimal link prioritization does not exist.
Similarly, when $$ |T_{E}| = 0 $$, the engine has not dereferenced any links, indicating incomplete results or a query with an empty result set. 
As differences in the metric's values get smaller when an engine performs worse, taking, for example, the $$ log $$ can help visualize differences for small values of the metric. 

To compute the metric, we first track the traversed topology of the queried web as a directed graph. Furthermore, for each query, we compute the minimal set of documents required to produce the query result. 
Finally, the engine's traversal path must be tracked, either within the engine or by recording the HTTP requests made by the engine.



In this section, we introduce the Shortest Traversal Length Ratio (STLR), explain its components, and outline the information query engines need to track for its computation.

During LTQP query execution, there is an optimal order in which links should be dereferenced to find all documents needed to answer a query. This theoretical optimum can be viewed as an oracle link prioritization algorithm with perfect information about the location of query-relevant documents. In theory, this optimal path can always be achieved, as the oracle uses the same links between documents that any engine can use. An engine should strive to achieve a traversal path close to this optimal path.

To measure the algorithmic performance of link prioritization algorithms, we use the ratio of the length of the optimal traversal path to the length of the effective traversal path taken by the engine during query execution. The optimal traversal path is defined as the shortest path needed to dereference all documents required for the complete query result, determined retrospectively.

The [subweb](cite
hartig2012foundations) traversed during LTQP can be represented as a directed graph, where an edge from document A to document B indicates that a URI pointing to document B was first found in the data obtained from document A. Finding the shortest path to dereference all query-relevant documents in this graph is equivalent to solving a [directed Steiner tree problem](cite
zosin2002directed), with the query-relevant documents serving as terminals.

The traversal path taken by the engine is the sequence of documents dereferenced to obtain all necessary documents for the complete query result. Given the lengths of these paths, the metric is defined as:
  ϕoptimal=∣TO∣∣TE∣,∣TO∣, ∣TE∣>0
  ϕoptimal​=∣TE​∣∣TO​∣​,∣TO​∣,∣TE​∣>0​

where ∣TE∣∣TE​∣ is the length of the engine traversal path and ∣TO∣∣TO​∣ is the length of the optimal path. In this definition, a higher value is better, with ϕoptimal=1ϕoptimal​=1 indicating optimal algorithmic link prioritization performance.

If ∣TO∣=0∣TO​∣=0, the query has no results, and the notion of optimal link prioritization does not apply. Similarly, if ∣TE∣=0∣TE​∣=0, the engine has not dereferenced any links, indicating either incomplete results or a query with an empty result set. As differences in the metric's values become smaller when an engine performs worse, taking the log⁡log of the metric can help visualize differences for small values.

To compute the metric, we track the traversed topology of the queried web as a directed graph. For each query, we compute the minimal set of documents required to produce the query result. Finally, the engine's traversal path must be tracked, either within the engine or by recording the HTTP requests made by the engine.

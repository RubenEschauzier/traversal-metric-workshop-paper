## Optimal Traversal Metric
{:#Method}
In this section, we will introduce the metric, its components, and discuss what information query engines should track to compute it.

### Definition
{:##definition}
To measure the algorithmic performance of link prioritization algorithms, we compare the traversal order of the measured query engine to the optimal traversal path computed in hindsight. 
The optimal traversal path is defined as the shortest path required to dereference all documents necessary for the full query result. 
Since the traversed web during LTQP forms a directed acyclic graph, finding the shortest path equates to solving a [directed Steiner tree problem for graphs](cite:cites zosin2002directed), with the documents needed for the query answer functioning as terminals. 
The traversal path by the engine is similarly defined as the sequence of documents dereferenced by the engine to find all necessary documents for the complete query result. 
Given the lengths of these paths, the metric is defined as

$$
\begin{aligned}
  \phi_{optimal} = \dfrac{|T_{E}|}{|T_{O}|},
\end{aligned}
$$

with $$ |T_{E}| $$ the length of the engine traversal path and $$ |T_{O}| $$ the length of the optimal path. 
In this definition, a lower value is better, with $$ \phi_{optimal} = 1 $$ indicating optimal algorithmic link prioritization performance.

### Required Information
{:##requiredinfo}
Most LTQP engines do not by default track the data required to compute the proposed metric. 
To do so, the engine should track a graph structure representing the topology of the queried web and the order in which it dereferences documents. Additionally, engines should compute the document provenance of bindings, which indicates which documents contributed to the query result bindings. Fortunately, full [how-provenence](cite:cites herschel2017survey) is not required; only the set of documents involved in answering the query is needed.

### Experiment Set-up
{:##experiment}
For our experiments, we will use the [SolidBench benchmark](cite:cites taelman2023link) to test our link prioritization metric. 
We will use [Comunica](cite:cites taelman2018comunica) to track the required information for computing the metric. 
In our experiments, we compare depth-first traversal to breadth-first traversal using both the optimal traversal metric and total query execution time.

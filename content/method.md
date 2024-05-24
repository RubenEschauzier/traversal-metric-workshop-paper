## Optimal Traversal Metric
{:#Method}
In this section we will introduce the metric, explain its components, and finally discuss what information query engines should track to compute it.

### Definition
{:##definition}
To measure the algorithmic performance of link prioritization algorithms, we will compare the traversal order of the measured query engine to the optimal traversal path computed in hindsight. The optimal traversal path is defined as the shortest path taken to dereference all documents required for the full query result. As the traversed web during LTQP is a directed acyclic graph, finding the shortest path is a [directed steiner tree problem for graphs](cite:cites zosin2002directed), with the documents required for the full query answer as terminals. The traversal path by the engine is similary defined as the document sequence dereferenced to find all documents required for the full query result. Given the length of the two paths, the metric is defined as 

$$
\begin{aligned}
    \phi_{optimal} = \dfrac{|T_{E}|}{|T_{O}|},
\end{aligned}
$$

with $$ |T_{E}| $$ the length of the engine traversal path and $$ |T_{O}| $$ the length of the optimal path. 
In this definition, lower is better, with $$ \phi_{optimal} = 1 $$ meaning optimal algorithmic performance.

### Required Information
{:##requiredinfo}
By default, most LTQP engines do not track the data required to compute the metric. 
First, the engine should track topology of the queried web and the order in which it dereferences documents. 
This is best represented using a graph datastructure. 
In addition, engines should compute document provenence of bindings. 
Fortunately, we do not require full [how-provenence](cite:cites herschel2017survey), instead only the set of documents involved in answering the query is required.
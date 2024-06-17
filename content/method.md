## Optimal Traversal Metric
{:#Method}
In this section, we will introduce the metric and its components, and discuss what information query engines should track for its computation.

### Definition
{:#definition}
<span class="comment" data-author="RV">Remove this subsection heading.</span>

<span class="comment" data-author="RV">Why. Start saying why. Say there's a theoretical optimal path, which engines should always strive to achieve. So hence, we're measuring that deviation.</span>
To measure the algorithmic performance of link prioritization algorithms, we use the ratio of the length of the effective traversal path to the optimal traversal path during query execution. 
The optimal traversal path is defined as the shortest path needed to dereference all documents required for the complete query result and is determined retrospectively.

<span class="comment" data-author="RV">Do we (need to) introduce the concept of an oracle? As in: there's a theoretical optimum. Can it be achieved in all cases? If yes, say so, and why. If no, say so, and why, and how close we can get.</span>

The subweb traversed during LTQP can be represented as a directed graph, where an edge from document A to document B indicates that a URI pointing to document B was <ins class="comment" data-author="RV">first</ins> found in the data obtained from document A. 
Finding the shortest path to dereference all query-relevant documents in this graph is equivalent to solving a [directed Steiner tree problem](cite
The web traversed during LTQP can be represented as a directed graph, where an edge from document A to document B indicates that a URI pointing to document B was found in the data obtained from document A. 
Finding the shortest path to dereference all query-relevant documents in this graph is equivalent to solving a [directed Steiner tree problem](cite:cites 
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
<span class="comment" data-author="RV">So why don't we invert the fraction then, such that higher is better, and 1 is the optimum?</span>
<span class="comment" data-author="RV">And do account for zeros. (Maybe add +1 to both factors to account for seed?)</span>

To compute the metric, we first track the traversed topology of the queried web and convert it into a directed graph. Furthermore, for each query, we compute the minimal set of documents required to produce the query result. 
Finally, the engine's traversal path must be tracked, either within the engine or by recording the HTTP requests made by the engine.

<span class="comment" data-author="RV">Should be clear at this point whether the optimum is always reachable or not. (And whether this theoretical optimum is always the best way. For example, theoretically, it's faster for me to drive by car to the office. In practice, this optimum is rare at the times when I have meetings, so the train turns out to be faster, despite general suboptimality.)</span>

### Experimental Set-up
{:#experiment}
<span class="comment" data-author="RV">Move this subsection to the next section. It's part of the experiments of one validation of the metric; not a part of its definition.</span>

<<<<<<< HEAD
<span class="comment" data-author="RV">See comments inclusion for what comes next. We are testing the metric here, not an old hypothesis.</span>

Our experiments use the [SolidBench benchmark](citetaelman2023link) to test our link prioritization metric. 
<span class="comment" data-author="RV">Give the metric a name in the previous section, so 1) we don't have to keep calling it <q>our link prioritization metric</q>, 2) so others can use that name later.</span>
We focus on the Discover queries from SolidBench, as these often produce results without timing out, a necessary precondition for our metric.
<span class="comment" data-author="RV">This property should be mentioned as a limitation at the end of the paper.</span>
We extended the modular query engine [Comunica](citetaelman2018comunica)
to track the required information for computing the metric during query execution.
Our experiments compare [depth-first traversal and breadth-first traversal](cite:cites hartig2016walking) using the optimal traversal metric and time until the final query result.
<span class="comment" data-author="RV">Yes, really give the metric a name. It gets awkward at this point.</span>
We use a [heuristic Steiner tree solver](citewatel2016practical) to speed up optimal path computation; although an exact solver would be ideal, it significantly increases computational complexity.
<span class="comment" data-author="RV">How much? Did we try? Is this a limitation of our proposal that we must mention at the end?</span>

<span class="comment" data-author="RV">Yes, baptize it the RRR metric after it's authors 😂</span>
=======
For our experiments, we will use the [SolidBench benchmark](cite:cites taelman2023link) to test our link prioritization metric. 
We will use the Discover queries from SolidBench, as these often produce results without timing out, which is necessary for computing our metric.

To track the required information for computing the metric during query execution, we use the modular query engine [Comunica](cite:cites taelman2018comunica).
Our experiments will compare [depth-first traversal and breadth-first traversal](cite:cites hartig2016walking) using the optimal traversal metric and time until the final query result.

To compute the optimal path, we will use a [heuristic Steiner tree solver](cite:cites watel2016practical) to speed up computations. Although an exact solver would be ideal, it would significantly increase the computational complexity.
>>>>>>> master

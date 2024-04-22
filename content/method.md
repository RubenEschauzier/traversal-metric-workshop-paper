## Method
{:#Method}
In this section we will formally introduce the metric, explain its componenets, and finally discuss what information query engines should track to compute it.

### Traversed Sub-web
{:##traversedsubweb}

During query execution, the engine traverses the sub-web of documents available from $$ W $$ and query $$ \mathcal{Q}_{c}^{B, S} $$. This produces a Directed Acyclic Graph (DAG) with sources $S$ from the seed documents.

### Relevant Traversal Path
{:##relevanttraversalpath}

<!-- In LTQP, queries are defined by their basic graph pattern (BGP) $$ B $$, seed URI's $$ S $$, reachability criterion $$ c $$, and data web $$ W $$. During query execution over $$ W $$ the seed URIs $$ S $$ are dereferenced first. From this data, new URIs to follow are extracted in accordence to the BGP $$ B $$ and chosen reachability criterion $$ c $$.  -->
During LTQP, the engine must dereference all documents that contribute to the query result set to complete the query. However, during the traversal the engine will likely dereference irrelevant documents that do not produce triples required to answer the query. By tracking the source document for each solution mapping and propegating this during joins, we obtain the set $$ D_{\mathcal{Q}_{c}^{B, S}(W)} \subseteq D_{\mathcal{R}}$$ of nodes in the reachable sub-web that are required to answer the query $$ \mathcal{Q}_{c}^{B, S} $$ on data-web $$ W $$. In this [formulation](cite:cites hartig2012foundations) $$ \mathcal{Q}_{c}^{B, S}(W) $$ denotes the query result set of BGP $$ B $$ with seed documents $$ S $$ and reachability criterion $$ c $$, when executed over data-web $$ W $$. Furthermore, $$ D_{\mathcal{R}} $$ denotes the reachable sub-web of for our query, which again depends on $$ B $$, $$ S $$, $$ c $$, and $$ W $$. The formal definitions are given in [](cite:cites hartig2012foundations). We define $$ D_{\mathcal{Q}_{c}^{B, S}(W)} $$

$$
\begin{aligned}
    D_{\mathcal{Q}_{c}^{B, S}(W)} = \{ \{ d | d \in D_{\mu_{n}} \} | \mu_{n} \in \mathcal{Q}_{c}^{B, S}(W) \}.
\end{aligned}
$$

Where $$ D_{\mu_{n}} $$ denotes the set of documents required to produce solution $$ \mu_{n} \in \mathcal{Q}_{c}^{B, S}(W) $$. During query execution, documents are sequentially dereferenced and added to the queried data. This produces a traversal order of documents $$ (D_{\mathcal{R}}, \preceq) $$, a totally ordered set with order

$$
    \preceq \text{}= d_{a} < d_{b} \text{        if    } t_{d_{a}} < t_{d_{b}} \text{,    } \forall d_{a}, d_{b} \in O_{\mathcal{Q}_{c}^{B, S}(W)} .
$$

With $$ t_{d_{a}} $$ the timestamp when document $$ d_{a} $$ is dereferenced by the engine.
Using this ordering, we define the totally ordered set $$ R_{\mathcal{Q}_{c}^{B, S}(W)} = (\bigcup\limits_{j=1}^{n} D_{(\mathcal{Q}_{c}^{B, S}(W), j)}, \preceq )$$, the set of query relevant documents ordered by their dereference time. We use this to define the minimal set of dereferenced documents required to dereference all documents as follows:
 <!-- We note that $$ O_{\mathcal{Q}_{c}^{B, S}(W)} $$ is simply the set resulting from applying the preceding order on $$ D_{\mathcal{R}} $$. 
 From $$ O_{\mathcal{Q}_{c}^{B, S}(W)} $$ we define the relevant traversal order $$ O^{r}_{\mathcal{Q}_{c}^{B, S}(W)} $$ as minimal set of traversed documents required to dereference all query-relevant documents -->


$$
   O^{r}_{\mathcal{Q}_{c}^{B, S}(W)} = \{ d_{i} \in D_{\mathcal{R}} | t_{d_{i}} < \text{max}_{t_{j} \in  R_{\mathcal{Q}_{c}^{B, S}(W)} }(t_{j})  \}
$$

TODO: Define optimal traversal path using steiner tree and DAG formulation  of sub-web.

NAME HERE is defined as the length of the traversal path to get all relevant documents divided by the optimal traversal path computed in hindsight.
To determine the impact link prioritizatio nalgorithms have on performance the engine must first track its traversal order
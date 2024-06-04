## Abstract
<!-- Context      -->
The scale of decentralization envisioned for the current centralized web necessitates querying approaches capable of querying multiple small data sources rather than a few large ones.
Link Traversal-based Query Processing (LTQP) is a promising approach for querying highly decentralized environments. It executes queries without prior knowledge of the data, discovering data sources dynamically.
<!-- Need         -->
During LTQP, engines can prioritize links likely to be relevant to the query, improving query execution speed. 
However, assessing and comparing the algorithmic performance of these systems is challenging due to various compounding factors during query execution. 
<!-- Task         -->
Therefore, researchers need an implementation-agnostic and deterministic metric that accurately measures the marginal effectiveness of link prioritization algorithms in LTQP engines.
<!-- Object       -->
In this paper, we motivate the need for accurately measuring traversal performance, introduce initial steps toward defining such a metric, and outline the challenges and potential extensions of the proposed metric.
<!-- Findings     -->
Our findings show that the proposed metric highlights differences in link prioritization performance depending on data fragmentation strategy and correlates with overall query engine performance.
<!-- Conclusion   -->
The proposed metric allows us to evaluate link prioritization performance and paves the way for easily assessing the effectiveness of future link prioritization algorithms.
<!-- Perspectives -->
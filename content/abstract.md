## Abstract
<!-- Context      -->
The decentralization envisioned for the current centralized web requires querying approaches capable of accessing multiple small data sources while complying with legal constraints related to personal data, such as licenses and the GDPR.
Link Traversal-based Query Processing (LTQP) is a querying approach designed for highly decentralized environments that satisfies these legal requirements.
An important optimization avenue in LTQP is the order in which links are dereferenced, which involves prioritizing links to query-relevant documents. 
<!-- Need         -->
However, assessing and comparing the algorithmic performance of these systems is challenging due to various compounding factors during query execution. 
Therefore, researchers need an implementation-agnostic and deterministic metric that accurately measures the marginal effectiveness of link prioritization algorithms in LTQP engines.
<!-- Task         -->
<!-- Object       -->
In this paper, we motivate the need for accurately measuring link prioritization performance, define and test such a metric, and outline the challenges and potential extensions of the proposed metric.
<!-- Findings     -->
Our findings show that the proposed metric highlights differences in link prioritization performance depending on the queried data fragmentation strategy.
<!-- Conclusion   -->
The proposed metric allows evaluating link prioritization performance
<!-- Perspectives -->
and enables easily assessing the effectiveness of future link prioritization algorithms.

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
The proposed metric allows for evaluating link prioritization performance
<!-- Perspectives -->
and enables easily assessing the effectiveness of future link prioritization algorithms.


<span class="printonly firstpagefooter">
<span class="firstpagefootertop">&nbsp;</span>
<span class="footnotecopyright">
<span style="font-style:italic">AMW 2024: 16th Alberto Mendelzon International Workshop on Foundations of Data Management, September 30th--October 4th, 2024, Mexico City, Mexico</span><br />
<img src="img/mail.png" width="12px" /> ruben.eschauzier@ugent.be (R. Eschauzier); <img src="img/mail.png" width="12px" /> ruben.taelman@ugent.be (R. Taelman); <img src="img/mail.png" width="12px" /> ruben.verborgh@ugent.be (R. Verborgh)<br />
<img src="img/cc-by.png" width="50px" /><span style="font-size: 0.75em">© 2024 Copyright for this paper by its authors. Use permitted under Creative Commons License Attribution 4.0 International (CC BY 4.0).</span><br />
<img src="img/ceur-ws-logo.png" width="50px" />CEUR Workshop Proceedings (<a href="https://CEUR-WS.org">CEUR-WS.org</a>)<br />
</span>
</span>
<span class="comment" data-author="RV">No <q>towards</q> titles. They kill things. Try removing the word. If not happy with the resulting title, refine until you are.</span>

## Abstract
<!-- Context      -->
The scale of decentralization envisioned for the current centralized web necessitates querying approaches capable of querying multiple small data sources rather than a few large ones.
<span class="comment" data-author="RV">No, I disagree. It's not the scale. It's the fact that legal constraints (licenses, GDPR…) forbid us from bringing them together. We're not decentralizing just for the heck of it. It's technologically extremely subobtimal. Rather, we are deliberately making the structure of tech match the structure of sociolegal reality. And _then_ there's the scale argument, which makes it even more complex. </span>
Link Traversal-based Query Processing (LTQP) is a promising approach for querying highly decentralized environments.
<span class="comment" data-author="RV">I don't think it's <q>promising</q>; in fact, it's almost the opposite 😅 But what we're saying is: everything else is un-promising. It's a no-go, because it violates a constraint we can't cross (see https://ruben.verborgh.org/blog/2024/05/30/the-webs-data-triad/). At least LTQP matches the needs; now the question is: how do we make it match our wants?</span>
It executes queries without prior knowledge of the data, discovering data sources dynamically.
During LTQP, engines can prioritize links likely to be relevant to the query, improving query execution speed. 
<!-- Need         -->
However, assessing and comparing the algorithmic performance of these systems is challenging due to various compounding factors during query execution. 
<span class="comment" data-author="RV">Be more specific. It's not just challenging. We don't know how good they are, because query semantics are different. Apples and oranges. We have an apples and oranges problem, and you'll propose a strategy for breaking through it.</span>
<!-- Task         -->
Therefore, researchers need an implementation-agnostic and deterministic metric that accurately measures the marginal effectiveness of link prioritization algorithms in LTQP engines.
<span class="comment" data-author="RV">Nope, this sentence is the NEED 😃 As you can see from the beginning. Put that in the NEED. The task is what you've done to address this need.</span>
<!-- Object       -->
In this paper, we motivate the need for accurately measuring traversal performance, introduce initial steps toward defining such a metric, and outline the challenges and potential extensions of the proposed metric.
<!-- Findings     -->
Our findings show that the proposed metric highlights differences in link prioritization performance depending on data fragmentation strategy and correlates with overall query engine performance.
<!-- Conclusion   -->
The proposed metric allows evaluating link prioritization performance
<!-- Perspectives -->
and paves the way for easily assessing the effectiveness of future link prioritization algorithms.

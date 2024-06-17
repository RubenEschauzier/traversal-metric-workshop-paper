## Introduction
{:#introduction}

Currently, web user data is stored in centralized data silos, restricting innovation [](cite:cites Verborgh_2020). 
Rather than storing all user data of a single application in a single location, decentralization efforts such as Solid adopt an approach that spreads data into smaller stores at different locations.
When applications intend to use decentralized data, querying approaches capable of handling numerous small, decentralized data stores are required. 
<span class="comment" data-author="RV">Say why: because we can't centralize. It might be useful to swap the position of the next and previous sentences to make that point.</span>
Additionally, as these vaults may contain sensitive data, querying must support fine-grained access control.
Link Traversal-based Query Processing (LTQP) is an integrated querying approach that meets these requirements. 
Starting from a _seed_ data source, the LTQP query engine dynamically discovers new data sources by following hyperlinks found in previously discovered documents.

In LTQP, the arrival times of the first $$ k $$ results can be [improved](cite:cites taelman2023link) by prioritizing links likely relevant to the query. 
By initially dereferencing data sources relevant to the query, the query engine can quickly begin producing results. 
On the other hand, if irrelevant data is dereferenced first, the query engine spends time processing data that won't produce results, slowing down query execution.
By streaming the first results quickly [](cite:cites koudas2005data), applications can already start presenting these results to clients. 
For example, an application can quickly present the first few query results, while hiding the yet-to-be-produced results behind a scrollbar.

<span class="comment" data-author="RV">Flows well, but remember that this is a short paper. We're 2 paragraphs in and it's all context. Can we get to the need faster?
1) Shoot, some data can never be centralized.
2) We'll need to be able to query it where it is.
3) Existing techniques are damn slow.
4) We want to know how slow/fast.
5) Here's how those techniques work.
</span>

<span class="todo" data-author="RV">Describe very clearly what a <q>traversal strategy</q> is, and how it differ from other factors. Should be clear: what's in, what's out.</span>

<span class="comment" data-author="RV">Swap the order of sentences in the next para. Start with the conclusion: we can't measure things. Then elaborate why (shortcomings of existing approaches).</span>
[Previous work](cite:cites taelman2023link, hartig2016walking) has utilized result arrival times and total execution time to assess the performance of different traversal strategies. 
While this approach is sufficient when comparing traversal strategies within the same engine and environment, it falls short when comparing different engine implementations and environments.
This downside also holds for other execution time-based metrics, like [diefficiency](cite:cites acosta2017diefficiency).
<del class="comment" data-author="RV">Specifically, several aspects complicate performance comparisons:</del>
<span class="comment" data-author="RV">Can we rephrase the previous sentence to be much more specific?</span>
<ins class="comment" data-author="RV">Actual traversal-related performance changes are obscured by these unrelated differences that may skew results:</ins>


Programming Languages
: Different languages can substantially affect engine [performance](cite:cites fourment2008comparison), hindering pure time-based comparisons of algorithms.

Dereferencing Overhead
: Network times [vary widely](cite:cites christiansen2000tuning, kobayashi2002analysis), introducing significant noise into execution times, even for comparisons of the same engine.

Orthogonal Optimization Strategies
: Different [query optimization](cite:cites hartig2011zero) strategies might create differences independent of traversal factors. 

<del class="comment" data-author="RV">In short, measuring the marginal effect of traversal strategies is challenging. </del>
<span class="comment" data-author="RV">We just made that point.</span>
In contrast,
the number of intermediate results produced by the engine
might allow a better measurement of
the marginal effectiveness of join planning. 
<span class="comment" data-author="RV">Does it though? Wouldn't that be also affected by other optimization strategies? Some of them affect this number.</span>
In this paper, we introduce a metric that enables straightforward observation of the algorithmic performance of traversal approaches, independent of implementations. 
This leads to our research question: _How to compare the marginal algorithmic performance of traversal strategies in an implementation-agnostic manner?_
<span class="comment" data-author="RV">Really good to end on this question. Makes for a suggested title:
<q>Implementation-agnostic performance comparison of traversal strategies</q>
</span>
In short, measuring the marginal effects of different traversal strategies is difficult. 
Additionally, current metrics do not reveal how far current traversal methods are from the optimal solution. 
Consequently, the potential performance improvements from exploring new traversal strategies are unknown and uncertain.

To address this, we propose a new metric: the Shortest Traversal Length Ratio (STLR). 
STLR allows for the evaluation of traversal strategies by comparing their performance to the optimal traversal path.
This metric will guide future research by highlighting the potential gains from investigating new traversal strategies. 
Furthermore, it will allow the comparison of traversal strategies independent of implementation details.

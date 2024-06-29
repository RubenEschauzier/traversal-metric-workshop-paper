## Conclusion
{:#conclusion}
<!-- Maybe cut this part -->
The current definition and implementation of the Relevant Retrieval Ratio ($$ R^{3} $$) has several limitations.
First, due to the computational complexity of the Steiner tree problem for graphs and the lack of readily available exact solvers that work on directed graphs, our implementations use heuristics, thus leading to potentially suboptimal traversal path lengths.
Second, the metric can not be computed when a query produces no results, either due to timeout or no results existing for the query.
Finally, our metric uses theoretically optimal paths. 
In practice, document dereference times can vary, making the theoretically optimal path potentially suboptimal.
In future work, more extensive benchmarking of the metric is required to validate its effectiveness in measuring prioritization performance. Furthermore, a new metric that includes a penalty term for HTTP request time would account for real-world uncertainties in LTQP scenarios. Finally, an $$ R^3 $$ metric for the first $$ k $$ results can be defined.


### Acknowledgements
This research was supported by SolidLab Vlaanderen (Flemish Government, EWI and RRF project VV023/10).
Ruben Taelman is a postdoctoral researcher at the Research Foundation – Flanders (FWO).

<!-- <span class="comment" data-author="RE"> Mention limitations: heuristic solver, needs results to compute the metric, in practise with differing HTTP request times, the path might actually not be optimal. Maybe more links but faster to dereference is faster</span>
<del class="comment" data-author="RV">
In this paper, we introduced a preliminary, implementation-independent metric to measure the algorithmic performance of link prioritization algorithms during LTQP. 
Early results show that while depth-first prioritization outperforms breadth-first prioritization algorithmically, this difference is not reflected in execution time. 
</del>
<span class="comment" data-author="RV">We don't need a summary in a short paper.</span>

<del class="comment" data-author="RV">
This supports the hypothesis that SolidBench Discover queries are unlikely to benefit from link prioritization improvements [](cite:cites eschauzier2023does).
</del>
<div class="comment" data-author="RV" markdown=1>
Nooooo this is a capital sin. We cannot do this. This is a fatal scientific flaw that would justify rejecting the paper. We have our argumentation structure wrong!

We are **not** gathering evidence for the hypothesis. That's not what we are doing—at all.

Our real strategy is as follows:

- We consider the hypothesis proven, through other means, in [](cite:cites eschauzier2023does).
- We now want to test our metric—**_not_ the hypothesis**.
- Our metric can only be successful if:
    - it obtains the same result
    - it was easier to obtain that result
- Note that this is not a _proof_ that our metric works.
    - But it at least shows that
      it does not **not** work for this particular case.
    - So there's some hopeful circumstantial evidence.
- And it **definitely _cannot_ be additional proof
  of the hypothesis' correctness because**:
    - Its correctness was an assumption when we started this.
    - We don't even know if our metric works.

Basically, by leaving in the previous sentence,
we would be making the flawed argument:

- Let's assume the sky is green.
- My new color tester thinks the sky is green.
- Okay, so the sky is definitely green
  and my color tester is great.

Note how the above argument both:

- fails to prove the sky is green
- fails to prove the tester works

And our claim that it would,
casts insurmountable doubts on our argumentation capabilities
in a way that would kill the entire paper,
because we've just confidently proven that the sky is green.
</div>

<span class="comment" data-author="RV">First, lessons learned. What can readers do now as a result of their work? When should they be using the new metric?</span>

<span class="comment" data-author="RV">Second, limitations. When should they not be using our metric?</span>

To improve the metric, we plan several extensions. 
<span class="comment" data-author="RV">
Don't.
1) Let's leave the metric as-is. It's finished. It has a name and everything. We're done here.
2) We can call for additional metrics. Different ones. They will have different names.
</span>

<span class="comment" data-author="RV">First step of future work: more evidence for our metric. More understanding of what it does and doesn't.</span>

<span class="comment" data-author="RV">Second step: introducing additional metrics and checking if they help.</span>

<span class="comment" data-author="RV">And we're not promising anything here. Future work is not about us promising things. It's about how other people can build on top of our work. If those other people happen to be us; great. If not, even better.</span>

<del class="comment" data-author="RV">First, we will include a</del> <ins class="comment" data-author="RV">Someone else can make a new</ins> metric for the first $$ k $$ results, defined as the ratio between the length of the path the engine takes to dereference the documents for $$ k $$ results and the optimal path to dereference $$ k $$ results. 
This is challenging because computing the optimal path for $$ k $$ results requires solving Steiner trees for all combinations of size $$ k $$ out of $$ n $$, where $$ n $$ is the total number of results.
Second, <del class="comment" data-author="RV">we will</del> <ins class="comment" data-author="RV">somebody else can create a new metric to</ins> incorporate a penalty term for documents with long HTTP request times to account for real-world uncertainties in LTQP scenarios. 
Finally, <del class="comment" data-author="RV">we will</del> <ins class="comment" data-author="RV">as a result of our work, anybody can now</ins> conduct more extensive benchmarks and provide easy-to-use code repositories to reproduce and utilize the introduced metrics.
<span class="comment" data-author="RT">Explain why that is (they are selective). I'd also make explicit here that in future work you will look into less selective queries, and say what you expect to see there.</span>

To improve the metric, we plan several extensions. 
First, we will include a metric <span class="comment" data-author="RT">But this would not be an extension to the metric, but a new metric, right?</span> for the first $$ k $$ results, defined as the ratio between the length of the path the engine takes to dereference the documents for $$ k $$ results and the optimal path to dereference $$ k $$ results. 
This is challenging because computing the optimal path for $$ k $$ results requires solving Steiner trees for all combinations of size $$ k $$ out of $$ n $$, where $$ n $$ is the total number of results.
Second, we will incorporate a penalty term for documents with long HTTP request times to account for real-world uncertainties in LTQP scenarios. 
Finally, we will conduct more extensive benchmarks and provide reusable tools to reproduce and utilize the introduced metrics. -->

<!-- <div style="page-break-after: always; visibility: hidden"> 
\pagebreak 
</div> -->

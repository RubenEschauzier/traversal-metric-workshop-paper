## Results
{:#Results}
[](#figure-main) shows that depth-first traversal outperforms breadth-first traversal in algorithmic performance using the computed traversal performance metrics (TPMs).
<span class="comment" data-author="RV">But actually, it does not! It doesn't show anything about the algorithms. It should show something about our metric.</span>

<ins class="comment" data-author="RV">[](#figure-main) shows that our metric-with-a-new-fancy-name confirms the findings observed by existing-but-more-cumbersome-metric.</ins>

However, this trend is not observed when comparing the time until the last query result. 
<span class="comment" data-author="RV">Are we observing the opposite trend? Or no such trend at all?</span>
<ins class="comment" data-author="RV">However, no such trend</ins>
<ins class="comment" data-author="RV">However, he opposite trend</ins>
Additionally, examining the Pearson Correlation Coefficient between the TPM value and the time until the last query result for each traversal strategy reveals a weak negative correlation: -0.156 for breadth-first and -0.175 for depth-first.
This weak correlation, along with the minimal impact of better TPM on execution time, supports the hypothesis that SolidBench Discover queries do not benefit from traversal strategy optimization due to execution being limited by suboptimal query plans [](cite
eschauzier2023does).

<div class="comment" data-author="RV" markdown=1>
Much more explicit here!

1. We are going to preliminary investigate whether out metric works.
1. Let's see if we can confirm _this_ existing hypothesis, which we've already proven using other means, more easily.
1. Bam, yes, we can!! And it was so easy.
1. Okay, that's an interesting indication that our metric at least works here.
   Did we mention it was easy?

That structure is absolutely crucial to make your point.
</div>

<figure id="figure-main">
<img src="figures/metric_difference.svg">
<figcaption markdown="block">
The difference in the proposed traversal performance metric between depth-first traversal and breadth-first traversal.
<span class="comment" data-author="RV">Mmm not the figure I expected. This is a paper that defined a metric, and we're not even showing the metric? What are the outcomes of the metric? I'd want to see the scores for each strategy for each query. We MUST use the metric and show its results. It's not a relative metric.</span>
</figcaption>
</figure>

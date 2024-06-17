## Existing Metrics
{:#existingmetrics}

<del class="comment" data-author="RV">Currently, LTQP performance is evaluated using several metrics:</del>
<span class="comment" data-author="RV">More opinion/information. Be stronger.</span>
<ins class="comment" data-author="RV">Existing LTQP metrics for implementations are unreliable predictors of when one traversal strategy outperforms another:</ins>

Total query processing time
: While important, traversal strategies are unlikely to improve total query execution time significantly, as completing a query requires dereferencing all documents if the traversal strategy does not involve pruning links [](cite:cites hartig2016walking). However, it is an effective metric for total LTQP engine performance.
<span class="comment" data-author="RV">I don't understand this point; and I now realize this happens because strategy wasn't defined in intro.</span>

Arrival times of the first $$ k $$ results
: As discussed in the introduction, link prioritization algorithms can potentially improve this metric.
<span class="comment" data-author="RV">Add something new here. Perhaps move content from the intro to here then. Otherwise, this falls flat.</span>

Diefficiency Metrics
: These measure the continuous efficiency of query engines by reflecting the density of produced results over a given time interval[](cite:cites acosta2017diefficiency). 
<span class="comment" data-author="RV">As opposed to what? Be clear and specific. Not necessarily with more words.</span>
<ins class="comment" data-author="RV">Continuous efficiency improves over … by …</ins>

Number of HTTP Requests
: <span class="rephrase" data-author="RV">This measures the efficiency of an engine at retrieving only relevant data.</span> <del class="comment" data-author="RV">Fewer HTTP requests to achieve the same results indicate effective pruning.</del>
<span class="comment" data-author="RV">Say this thing in one sentence, but much more clearly.</span>

<del class="comment" data-author="RV">These existing metrics are essential for evaluating the overall performance of the entire system.</del> The metric this paper proposes is complementary to existing metrics, as it allows researchers to accurately measure <del class="comment" data-author="RV">the system's overall performance and</del> the specific contribution of link prioritization algorithms.
<span class="comment" data-author="RV">Link this back to <q>strategy</q>. Or keep using <q>prioritization algorithm</q>. But use one term for the thing you aim to measure.</span>

## Results
{:#Results}
The differences in computed traversal performance metrics (TPMs) for both depth-first and breadth-first traversal are shown in [](#figure-main).
The figure shows that depth-first traversal outperforms breadth-first traversal in algorithmic performance.

However, this trend is not observed when comparing the time until the last query result. 
Additionally, examining the Pearson Correlation Coefficient between the TPM value and the time until the last query result for each traversal strategy reveals a weak negative correlation: -0.156 for breadth-first and -0.175 for depth-first.

This weak correlation, along with the minimal impact of better TPM on execution time, supports the hypothesis <span class="comment" data-author="RT">Make sure to cite this hypothesis</span> that SolidBench Discover queries do not benefit from traversal strategy optimization due to execution being limited by suboptimal query plans [](cite
eschauzier2023does).

<span class="comment" data-author="RT">Reminder for table with actual metric results.</span>

<!-- <figure id="figure-main">
<img src="figures/metric_difference.svg">
<figcaption markdown="block">
The difference in the proposed traversal performance metric between depth-first traversal and breadth-first traversal.
</figcaption>
</figure> -->

<!-- 

<figure id="figure-main">

<figure id="figure-main-1" class="subfigure">
<img src="figures/depth-first-metric.svg">
<figcaption markdown="block">
Subfigure 1
</figcaption>
</figure>

<figure id="figure-main-2" class="subfigure">
<img src="figures/breadth-first-metric.png" width="200">
<figcaption markdown="block">
Subfigure 2
</figcaption>
</figure>

<figcaption markdown="block">
Two figures
</figcaption>
</figure> -->

<!-- 
<span class="comment" data-author="RT">Figures need a legend for explaining the colors, and descriptions</span>

|      |      D1 |       D2 |       D3 |      D4 |      D5 |      D6 |      D7 |      D8 |
|:-----|--------:|---------:|---------:|--------:|--------:|--------:|--------:|--------:|
| mean | 3.05714 | 1.88286  | 1.48188  | 11.4157 | 8.56275 | 3.16885 | 9.8     | 1.43302 |
| std  | 1.64473 | 0.401009 | 0.352253 | 11.1215 | 8.28228 | 2.25602 | 7.60731 | 1.19184 |

|      |      D1 |       D2 |       D3 |      D4 |       D5 |      D6 |      D7 |       D8 |
|:-----|--------:|---------:|---------:|--------:|---------:|--------:|--------:|---------:|
| mean | 4.82857 | 1.57624  | 1.49423  | 12.4213 |  9.22745 | 3.33612 | 12.8667 | 0.980952 |
| std  | 4.42827 | 0.295887 | 0.393644 | 11.2035 | 10.291   | 2.14421 | 11.643  | 0.905814 |

<span class="comment" data-author="RT">What are the two tables about?</span>

<span class="comment" data-author="RT">Are the following enumeration todo's?</span>

1. Computed metric for depth first vs FIFO link prioritisation (possibly with time to compute the metric?)
2. Timing of the two methods to compare correlation between metric and execution time
D1   -1.771429
D2    0.306624
D3   -0.012357
D4   -1.005556
D5   -0.664706
D6   -0.167273
D7   -3.066667
D8    0.452063
 -->
<style>
@media print {
    @page {
      margin: 2.5cm;   
    }
    div.row > div {
      display: inline-block;  
      border: solid 1px #ccc;
      margin: 0.2cm;
    }
    div.row {
      display: block;
    }
}


.table {
    display: table;
    border-spacing: 2px;
}
.row {
    display: table-row;
}
.row > div {
    display: table-cell;
    border: solid 1px #ccc;
    padding: 2px;
}
caption {
    caption-side: bottom;
}
</style>

<figure id="initresults" class="table" markdown="1">

<table>
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>depth-first</th>
      <th>breadth-first</th>
      <th>Average Difference</th>
    <th></th>
      <th>depth-first</th>
      <th>breadth-first</th>
      <th>Average Difference</th>
    </tr>
    <tr>
      <th>Query</th>
      <th></th>
      <th></th>
      <th></th>
    <th>Query</th>
          <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>D1.0</th>
      <td>4.29</td>
      <td>13.14</td>
      <td>-8.86</td>
      <th>D5.0</th>
      <td>7.50</td>
      <td>6.83</td>
      <td>0.67</td>
    </tr>
    <tr>
      <th>D1.1</th>
      <td>2.00</td>
      <td>2.00</td>
      <td>0.00</td>
      <th>D5.1</th>
      <td>2.00</td>
      <td>2.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D1.2</th>
      <td>2.00</td>
      <td>2.00</td>
      <td>0.00</td>
      <th>D5.2</th>
      <td>3.00</td>
      <td>1.50</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>D1.3</th>
      <td>1.33</td>
      <td>1.33</td>
      <td>0.00</td>
      <th>D5.3</th>
      <td>24.67</td>
      <td>29.33</td>
      <td>-4.67</td>
    </tr>
    <tr>
      <th>D1.4</th>
      <td>5.67</td>
      <td>5.67</td>
      <td>0.00</td>
      <th>D5.4</th>
      <td>5.65</td>
      <td>6.47</td>
      <td>-0.82</td>
    </tr>
    <tr>
      <th>D2.0</th>
      <td>2.02</td>
      <td>1.98</td>
      <td>0.04</td>
      <th>D6.0</th>
      <td>1.88</td>
      <td>1.88</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D2.1</th>
      <td>2.00</td>
      <td>1.50</td>
      <td>0.50</td>
      <th>D6.1</th>
      <td>2.50</td>
      <td>2.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D2.2</th>
      <td>2.00</td>
      <td>1.50</td>
      <td>0.50</td>
      <th>D6.2</th>
      <td>2.50</td>
      <td>2.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D2.3</th>
      <td>1.11</td>
      <td>1.11</td>
      <td>0.00</td>
      <th>D6.3</th>
      <td>7.60</td>
      <td>7.60</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D2.4</th>
      <td>2.28</td>
      <td>1.79</td>
      <td>0.49</td>
      <th>D6.4</th>
      <td>1.36</td>
      <td>2.20</td>
      <td>-0.84</td>
    </tr>
        <tr>
    </tr>
    <tr>
      <th>D3.0</th>
      <td>2.00</td>
      <td>2.11</td>
      <td>-0.11</td>
      <th>D7.0</th>
      <td>21.17</td>
      <td>21.17</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D3.1</th>
      <td>1.10</td>
      <td>1.06</td>
      <td>0.04</td>
      <th>D7.1</th>
      <td>2.50</td>
      <td>2.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D3.2</th>
      <td>1.07</td>
      <td>1.07</td>
      <td>0.00</td>
      <th>D7.2</th>
      <td>2.50</td>
      <td>2.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D3.3</th>
      <td>1.61</td>
      <td>1.61</td>
      <td>0.00</td>
      <th>D7.3</th>
      <td>6.50</td>
      <td>6.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D3.4</th>
      <td>1.63</td>
      <td>1.63</td>
      <td>0.00</td>
      <th>D7.4</th>
      <td>16.33</td>
      <td>31.67</td>
      <td>-15.33</td>
    </tr>
    <tr>
      <th>D4.0</th>
      <td>11.00</td>
      <td>15.78</td>
      <td>-4.78</td>
      <th>D8.0</th>
      <td>2.22</td>
      <td>1.57</td>
      <td>0.65</td>
    </tr>
    <tr>
      <th>D4.1</th>
      <td>2.25</td>
      <td>2.25</td>
      <td>0.00</td>
      <th>D8.1</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D4.2</th>
      <td>2.00</td>
      <td>2.25</td>
      <td>-0.25</td>
      <th>D8.2</th>
      <td>2.14</td>
      <td>1.00</td>
      <td>1.14</td>
    </tr>
    <tr>
      <th>D4.3</th>
      <td>32.43</td>
      <td>32.43</td>
      <td>0.00</td>
      <th>D8.3</th>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>D4.4</th>
      <td>9.40</td>
      <td>9.40</td>
      <td>0.00</td>
      <th>D8.4</th>
      <td>2.80</td>
      <td>2.33</td>
      <td>0.47</td>
    </tr>
  </tbody>
</table>

<figcaption markdown="block">
Calculated Shortest Traversal Length Ratio's for depth-first and breadth-first prioritization seperated by query template and instantiation.
</figcaption>

</figure>



<figure id="initresults" class="table" markdown="1">

| Query Template           | C1     | C2     | C3     | F1    | F2    | F3    | F4     | F5    | L1    |
| ------------------------ |--------|--------|--------|-------|-------|-------|--------|-------|-------|
| Planning (RL)            | 0.5028 | 1.000  | 0.277  | 0.214 | 0.347 | 0.160 | 0.800  | 0.278 | 0.027 |
| Execution (RL)           | 3.116  | 2.577  | 0.583  | 0.100 | 0.090 | 0.062 | 1.906  | __0.059__ |__0.006__ |
| ------------------------ |--------|--------|--------|-------|-------|-------|--------|-------|-------|
| Planning (Comunica)      | 0.007  | 0.008  | 0.017  | 0.002 | 0.003 | 0.005 | 0.005  | 0.005 | 0.002 |
| Execution (Comunica)     | __0.076__  | __0.001__  | __0.490__  | __0.001__ |__0.005__ |__0.008__ | __0.012__  | 0.194 | 0.032 |

| Query Template           | L2     | L5     | S1     | S2    | S3    | S4    | S5     | S6    | S7    |
| ------------------------ |--------|--------|--------|-------|-------|-------|--------|-------|-------|
| Planning (RL)            | 0.025  | 0.024  | 0.689  | 0.060 | 0.059 | 0.066 | 0.059  | 0.021 | 0.028 |
| Execution (RL)           | __0.001__  | __0.002__  | 2.242  | 0.011 | __0.005__ | __0.000__ | __0.002__  | 0.008 | 0.002 |
| ------------------------ |--------|--------|--------|-------|-------|-------|--------|-------|-------|
| Planning (Comunica)      | 0.001  | 0.001  | 0.006  | 0.002 | 0.002 | 0.002 | 0.002  | 0.002 | 0.002 |
| Execution (Comunica)     | 0.006  | 0.007  | __0.139__  | __0.009__ | 0.008  | 0.005 | 0.009 | __0.001__ | __0.000__ |

<figcaption markdown="block">
Comparison of the query optimization and plan execution time, in seconds, of a previous version of our optimizer and the standard [Comunica](cite:cites taelman2018comunica) optimizer, with the faster plan execution in bold.
</figcaption>
</figure>

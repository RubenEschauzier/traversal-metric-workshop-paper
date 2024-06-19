## Results
{:#Results}

For our experiments, we will use the Discover queries from the [SolidBench benchmark](cite:cites taelman2023link) to test our STLR metric.
To track the required information for computing the metric during query execution, we use the modular query engine [Comunica](cite:cites taelman2018comunica).
To compute the optimal path, we will use a [heuristic Steiner tree solver](cite:cites watel2016practical) to speed up computations. Although an exact solver would be ideal, it could significantly increase the computational complexity for large subwebs [](cite:cites hwang1992steiner, lucas2014ising).

Our experiments will compare [depth and breadth-first prioritization](cite:cites hartig2016walking) using STLR and time until the final query result.
We will attempt to validate the substantiated assumption that Discover queries do not benefit from improved link prioritization [](cite:cites eschauzier2023does).

[](#metric-results) shows the computed metrics per template instantiation and the average difference in metric value. We observe that our metric favors depth-first prioritization compared to breadth-first on some query template instantiations. 
This is likely due to the different fragmentation strategies used in [SolidBench](cite:cites taelman2023link), as some pods store all query-relevant data in a single file, while others fragment these into multiple directories, complicating optimal traversal.
This difference in prioritization performance is not observed in query execution time. In fact, when we examine the <span class="comment" data-author="RE"> RECOMPUTE PEARSON METRIC</span> Pearson Correlation Coefficient between the average STLR and query-execution time of each template we find ....
Using the STLR, we confirm our previous [paper](cite:cites eschauzier2023does) by computing a metric value, instead of an engine-specific indepth analysis of the query execution progress.

<style>
table thead {
  border-bottom: 1px solid;
}

th,
td {
text-align:center;
}
tbody, th {
text-align:center; 
}

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
    tbody, th {
        text-align:center; 
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

<figure id="metric-results" class="table" markdown="1">

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
      <th style="border-bottom: 0">D1.0</th>
      <td>4.29</td>
      <td>13.14</td>
      <td>-8.86</td>
      <th style="border-bottom: 0">D5.0</th>
      <td>7.50</td>
      <td>6.83</td>
      <td>0.67</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D1.1</th>
      <td>2.00</td>
      <td>2.00</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D5.1</th>
      <td>2.00</td>
      <td>2.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D1.2</th>
      <td>2.00</td>
      <td>2.00</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D5.2</th>
      <td>3.00</td>
      <td>1.50</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D1.3</th>
      <td>1.33</td>
      <td>1.33</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D5.3</th>
      <td>24.67</td>
      <td>29.33</td>
      <td>-4.67</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D1.4</th>
      <td>5.67</td>
      <td>5.67</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D5.4</th>
      <td>5.65</td>
      <td>6.47</td>
      <td>-0.82</td>
    </tr>
    <tr style="border-top: 1px solid !important">
      <th style="border-bottom: 0">D2.0</th>
      <td>2.02</td>
      <td>1.98</td>
      <td>0.04</td>
      <th style="border-bottom: 0">D6.0</th>
      <td>1.88</td>
      <td>1.88</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D2.1</th>
      <td>2.00</td>
      <td>1.50</td>
      <td>0.50</td>
      <th style="border-bottom: 0">D6.1</th>
      <td>2.50</td>
      <td>2.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D2.2</th>
      <td>2.00</td>
      <td>1.50</td>
      <td>0.50</td>
      <th style="border-bottom: 0">D6.2</th>
      <td>2.50</td>
      <td>2.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D2.3</th>
      <td>1.11</td>
      <td>1.11</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D6.3</th>
      <td>7.60</td>
      <td>7.60</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D2.4</th>
      <td>2.28</td>
      <td>1.79</td>
      <td>0.49</td>
      <th style="border-bottom: 0">D6.4</th>
      <td>1.36</td>
      <td>2.20</td>
      <td>-0.84</td>
    </tr>
        <tr>
    </tr>
    <tr style="border-top: 1px solid">
      <th style="border-bottom: 0">D3.0</th>
      <td>2.00</td>
      <td>2.11</td>
      <td>-0.11</td>
      <th style="border-bottom: 0">D7.0</th>
      <td>21.17</td>
      <td>21.17</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D3.1</th>
      <td>1.10</td>
      <td>1.06</td>
      <td>0.04</td>
      <th style="border-bottom: 0">D7.1</th>
      <td>2.50</td>
      <td>2.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D3.2</th>
      <td>1.07</td>
      <td>1.07</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D7.2</th>
      <td>2.50</td>
      <td>2.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D3.3</th>
      <td>1.61</td>
      <td>1.61</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D7.3</th>
      <td>6.50</td>
      <td>6.50</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D3.4</th>
      <td>1.63</td>
      <td>1.63</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D7.4</th>
      <td>16.33</td>
      <td>31.67</td>
      <td>-15.33</td>
    </tr>
    <tr style="border-top: 1px solid">
      <th style="border-bottom: 0">D4.0</th>
      <td>11.00</td>
      <td>15.78</td>
      <td>-4.78</td>
      <th style="border-bottom: 0">D8.0</th>
      <td>2.22</td>
      <td>1.57</td>
      <td>0.65</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D4.1</th>
      <td>2.25</td>
      <td>2.25</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D8.1</th>
      <td>-</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D4.2</th>
      <td>2.00</td>
      <td>2.25</td>
      <td>-0.25</td>
      <th style="border-bottom: 0">D8.2</th>
      <td>2.14</td>
      <td>1.00</td>
      <td>1.14</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D4.3</th>
      <td>32.43</td>
      <td>32.43</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D8.3</th>
      <td>-</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D4.4</th>
      <td>9.40</td>
      <td>9.40</td>
      <td>0.00</td>
      <th style="border-bottom: 0">D8.4</th>
      <td>2.80</td>
      <td>2.33</td>
      <td>0.47</td>
    </tr>
  </tbody>
</table>

<figcaption markdown="block">
Calculated Shortest Traversal Length Ratio's for depth and breadth-first prioritization seperated by query template and instantiation. In this table, e.g. **D1.2** denotes the second instantiation of Discover query template 1 and <q>-</q> indicates a query timeout.
</figcaption>

</figure>

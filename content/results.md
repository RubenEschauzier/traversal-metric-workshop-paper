## Results
{:#Results}

For our experiments, we will use the Discover queries from the [SolidBench benchmark](cite:cites taelman2023link) to test our STLR metric.
To track the required information for computing the metric during query execution, we use the modular query engine [Comunica](cite:cites taelman2018comunica).
To compute the optimal path, we will use a [heuristic Steiner tree solver](cite:cites watel2016practical) to speed up computations. 
Although an exact solver would be ideal, it could significantly increase the computational complexity for large subwebs [](cite:cites hwang1992steiner, lucas2014ising). 
We provide an implementation of STLR on [github](https://github.com/RubenEschauzier/metric-link-prioritisation-performance/tree/master).

Our experiments will compare [depth and breadth-first prioritization](cite:cites hartig2016walking) using STLR and time until the final query result.
We will attempt to validate the substantiated assumption that Discover queries do not benefit from improved link prioritization [](cite:cites eschauzier2023does).

[](#metric-results) shows the computed metrics per template instantiation and the average difference in metric value. 
We find our metric significantly favors depth-first prioritization compared to breadth-first on some query template instantiations. 
This is likely due to the different fragmentation strategies used in [SolidBench](cite:cites taelman2023link), as some pods store all query-relevant data in a single file, while others fragment these into multiple directories, complicating optimal traversal.
This difference in prioritization performance is not observed in the time until the last result; the Pearson correlation coefficients between STLR and time until the last result are -0.042 and 0.201 for depth and breadth-first respectively. 
These low correlations indicate a weak link between STLR, however, this observed link could simply signify the noisiness of measuring query execution time characteristics.
Using the STLR, we confirm our previous [paper](cite:cites eschauzier2023does) by computing a metric value, instead of an engine-specific in-depth analysis of the query execution progress.

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
      <td>0.23</td>
      <td>0.08</td>
      <td></td>
      <th style="border-bottom: 0">D5.0</th>
      <td>0.13</td>
      <td>0.15</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D1.1</th>
      <td>0.50</td>
      <td>0.50</td>
      <td></td>
      <th style="border-bottom: 0">D5.1</th>
      <td>0.50</td>
      <td>0.50</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D1.2</th>
      <td>0.50</td>
      <td>0.50</td>
      <td>0.031</td>
      <th style="border-bottom: 0">D5.2</th>
      <td>0.33</td>
      <td>0.67</td>
      <td>-0.064</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D1.3</th>
      <td>0.75</td>
      <td>0.75</td>
      <td></td>
      <th style="border-bottom: 0">D5.3</th>
      <td>0.04</td>
      <td>0.03</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D1.4</th>
      <td>0.18</td>
      <td>0.18</td>
      <td></td>
      <th style="border-bottom: 0">D5.4</th>
      <td>0.18</td>
      <td>0.16</td>
      <td></td>
    </tr>
    <tr style="border-top: 1px solid !important">
      <th style="border-bottom: 0">D2.0</th>
      <td>0.50</td>
      <td>0.51</td>
      <td></td>
      <th style="border-bottom: 0">D6.0</th>
      <td>0.53</td>
      <td>0.53</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D2.1</th>
      <td>0.50</td>
      <td>0.67</td>
      <td></td>
      <th style="border-bottom: 0">D6.1</th>
      <td>0.40</td>
      <td>0.40</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D2.2</th>
      <td>0.50</td>
      <td>0.67</td>
      <td>-0.083</td>
      <th style="border-bottom: 0">D6.2</th>
      <td>0.40</td>
      <td>0.40</td>
      <td>0.056</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D2.3</th>
      <td>0.90</td>
      <td>0.90</td>
      <td></td>
      <th style="border-bottom: 0">D6.3</th>
      <td>0.13</td>
      <td>0.13</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D2.4</th>
      <td>0.44</td>
      <td>0.56</td>
      <td></td>
      <th style="border-bottom: 0">D6.4</th>
      <td>0.73</td>
      <td>0.46</td>
      <td></td>
    </tr>
        <tr>
    </tr>
    <tr style="border-top: 1px solid">
      <th style="border-bottom: 0">D3.0</th>
      <td>0.50</td>
      <td>0.48</td>
      <td></td>
      <th style="border-bottom: 0">D7.0</th>
      <td>0.05</td>
      <td>0.05</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D3.1</th>
      <td>0.91</td>
      <td>0.95</td>
      <td></td>
      <th style="border-bottom: 0">D7.1</th>
      <td>0.40</td>
      <td>0.40</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D3.2</th>
      <td>0.93</td>
      <td>0.93</td>
      <td>-0.002</td>
      <th style="border-bottom: 0">D7.2</th>
      <td>0.40</td>
      <td>0.40</td>
      <td>0.006</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D3.3</th>
      <td>0.62</td>
      <td>0.62</td>
      <td></td>
      <th style="border-bottom: 0">D7.3</th>
      <td>0.15</td>
      <td>0.15</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D3.4</th>
      <td>0.61</td>
      <td>0.61</td>
      <td></td>
      <th style="border-bottom: 0">D7.4</th>
      <td>0.06</td>
      <td>0.03</td>
      <td></td>
    </tr>
    <tr style="border-top: 1px solid">
      <th style="border-bottom: 0">D4.0</th>
      <td>0.09</td>
      <td>0.06</td>
      <td></td>
      <th style="border-bottom: 0">D8.0</th>
      <td>0.45</td>
      <td>0.64</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D4.1</th>
      <td>0.44</td>
      <td>0.44</td>
      <td></td>
      <th style="border-bottom: 0">D8.1</th>
      <td>-</td>
      <td>-</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D4.2</th>
      <td>0.50</td>
      <td>0.44</td>
      <td>0.042</td>
      <th style="border-bottom: 0">D8.2</th>
      <td>0.47</td>
      <td>1.00</td>
      <td>-0.263</td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D4.3</th>
      <td>0.03</td>
      <td>0.03</td>
      <td></td>
      <th style="border-bottom: 0">D8.3</th>
      <td>-</td>
      <td>-</td>
      <td></td>
    </tr>
    <tr>
      <th style="border-bottom: 0">D4.4</th>
      <td>0.11</td>
      <td>0.11</td>
      <td></td>
      <th style="border-bottom: 0">D8.4</th>
      <td>0.36</td>
      <td>0.43</td>
      <td></td>
    </tr>
  </tbody>
</table>

<figcaption markdown="block">
The calculated Shortest Traversal Length Ratio's for depth and breadth-first prioritization seperated by query template and instantiation. In this table, e.g. **D1.2** denotes the second instantiation of Discover query template 1 and <q>-</q> indicates a query timeout.
<span class="comment" data-author="RE"> Should this be a average difference for the log of metric? Because right now the average differences tell a different story than the relative performance, as in the previous (larger is worse) definition of the metric depth-first was clearly better.</span>
</figcaption>

</figure>

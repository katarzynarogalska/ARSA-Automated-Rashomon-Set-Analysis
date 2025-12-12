[back](index.md)

# IntersectionVisualizer

<div style="background-color: #c2deb1; padding: 10px; border-radius: 4px;">
class rashomon_analysis.visualizers.<strong>IntersectionVisualizer</strong>(rashomon_intersection, y_true)
</div>
<br>
This class is responsible for creating visualizations and descriptions of the key properties and metrics related to the Rashomon Intersection. Is a<strong> subclass of the Visualizer</strong> class.


The main library used for the visualizations is [Plotly](https://plotly.com/python/). 

<br>

<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Parameters</strong>
</div>
</br>
    <strong>rashomon_intersection</strong> : RashomonIntersection</br>
     &emsp;   created RashomonIntersection object for analysis.
    </br>
    <strong>y_true</strong> : pd.DataFrame </br>
    &emsp;   true class labels for every observation in the test dataset. (Returned by converters)
    <br>

</br>
</br> 
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Attributes</strong>
</div>
</br>
 <strong>rashomon_set</strong> : RashomonIntersection </br>
     &emsp; The rashomon_intersection value. Overwrites the rashomon_set attribute of the Visualizer class.
    </br>
 <strong>y_true</strong> : pd.DataFrame </br>
     &emsp;  y_true parameter value
    </br>
    <strong>binary_methods</strong> : list[str] </br>
    &emsp;  list of methods names, which create plots for binary task type analysis. 
    <br>
    <strong>binary_methods</strong> : list[str] </br>
    &emsp;  list of methods names, which create plots for multiclass task type analysis/
    <br>
</br>
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
</br>
<strong>Note:</strong> 
As this is a subclass of the Visualizer class, all methods, which are not specified in this section remain the same as in :

[Visualizer documentation](visualizer.md)
<br>
<div style="color: #60824f; font-size: 18px;">
    <strong>base_metric_return()</strong>
</div>
&emsp; Overrides the base_metric_return() method from Visualizer class. Returns the list of metrics specified in the RashomonIntersection object to be analyzed. Returns the metrics and an empty plot.  
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>empty_plot</code> : go.Figure
</br>
&emsp; <code>base_metrics</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>weighted_method_return()</strong>
</div>
&emsp; Additional method used only for the Rashomon Intersection analysis. Returns the name of the <code>weighted_sum_method</code> specified in the RashomonIntersection object to be analyzed. Returns the method name and an empty plot.  
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>empty_plot</code> : go.Figure
</br>
&emsp; <code>weighted_sum_method</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>set_size_indicator()</strong>
</div>
&emsp; Overrides the set_size_indicator() from the Visualizer class. Creates the gauge plot representing the fracton of models from the leaderboard that are included in the Rashomon Intersection. Returns the plot with its description. 
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>gauge_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>



<div style="color: #60824f; font-size: 18px;">
    <strong>ambiguity_vs_epsilon()</strong>
</div>
&emsp; Overrides the ambigutiy_vs_epsilon() method from the Visualizer class. Creates the Line chart of the possible <code>ambiguity</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding ambiguities. The actual ambiguity value for the given Rashomon Intersection is highlighted with the different color. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>proba_ambiguity_vs_epsilon()</strong>
</div>
&emsp; Overrides the proba_ambigutiy_vs_epsilon() method from the Visualizer class. Creates the Line chart of the possible <code>probabilistic_ambiguity</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding ambiguities. The actual probabilistic_ambiguity value for the given Rashomon Intersection is highlighted with the different color. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>discrepancy_vs_epsilon()</strong>
</div>
&emsp;  Overrides the discrepancy_vs_epsilon() method from the Visualizer class. Creates the Line chart of the possible <code>discrepancy</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding discrepancies. The actual discrepancy value for the given Rashomon Intersection is highlighted with the different color. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>prba_discrepancy_vs_epsilon()</strong>
</div>
&emsp;  Overrides the proba_discrepancy_vs_epsilon() method from the Visualizer class. Creates the Line chart of the possible <code>probabilistic_discrepancy</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding discrepancies. The actual probabilistic_discrepancy value for the given Rashomon Intersection is highlighted with the different color. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>rashomon_ratio_vs_epsilon()</strong>
</div>
&emsp;  Overrides the rashomon_ratio_vs_epsilon() method from the Visualizer class. Creates a Line chart of the possible <code>rashomon_ratio</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding rashomon_ratios. The actual rashomon_ratio value for the given Rashomon Intersection is highlighted with a different color. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>pattern_rashomon_ratio_vs_epsilon()</strong>
</div>
&emsp;  Overwrites the pattern_rashomon_ratio_vs_epsilon() method from the Visualizer class. Creates a Line chart of the possible <code>pattern_rashomon_ratio</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding pattern_rashomon_ratios. The actual pattern_rashomon_ratio value for the given Rashomon Intersection is highlighted with a different color. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>generate_rashomon_set_table()</strong>
</div>
&emsp; Overrides the generate_rashomon_set_table() method from the Visualizer class. Creates a table with the names of models included in the intersection alongside with their scores for both specified evaluation metrics. Returns the table and the description containing information about the <code>base_model</code> and selected <code>metrics</code>.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>table</code> : go.Figure
</br>
&emsp; <code>table_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>generate_gauge_for_metrics()</strong>
</div>
&emsp; Creates gauge plots illustrating how many models from the separate Rashomon Sets for each metric are included in the Rashomon Intersection. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>gauge_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>plot_venn_diagram()</strong>
</div>
&emsp; Creates the Venn diagram illustrating models, which are included in the separate Rashomon Sets for each metric, as well as the intersection of those two sets. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>venn_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>pareto_front_plot()</strong>
</div>
&emsp; Creates the scatterplot with the x and y axes representing two evaluation metrics, and points representing models from the entire leaderboard. Models included in the Pareto Front are highlighted in a different color. To read more about the Parto Front in multiobjective optimization visit: 

[Multi-Objective Hyperparameter Optimization in ML](https://arxiv.org/pdf/2206.07438#page=39.46).
    </br>
    </br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>scatter_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>


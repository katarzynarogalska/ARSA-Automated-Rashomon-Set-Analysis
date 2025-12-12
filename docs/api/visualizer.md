[back](index.md)

# Visualizer

<div style="background-color: #c2deb1; padding: 10px; border-radius: 4px;">
class rashomon_analysis.visualizers.<strong>Visualizer</strong>(rashomon_set, y_true)
</div>
<br>
This class is responsible for creating visualizations and descriptions of the key properties and metrics related to the Rashomon Set.


The main library used for the visualizations is [Plotly](https://plotly.com/python/). 

<br>

<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Parameters</strong>
</div>
</br>
    <strong>rashomon_set</strong> : RashomonSet </br>
     &emsp;   created RashomonSet object for analysis.
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
 <strong>rashomon_set</strong> : RashomonSet </br>
     &emsp;  rashomon_set parameter value
    </br>
 <strong>y_true</strong> : pd.DataFrame </br>
     &emsp;  y_true parameter value
    </br>
    <strong>binary_methods</strong> : list[str] </br>
    &emsp;  list of methods names, which create plots for binary task type analysis. 
    <br>
    <strong>binary_methods</strong> : list[str] </br>
    &emsp;  list of methods names, which create plots for multiclass task type analysis. 
    <br>
</br>
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>base_model_return()</strong>
</div>
&emsp; Returns the <code>base_model</code> name of the given RashomonSet object and an empty plot. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>empty_plot</code> : go.Figure
</br>
&emsp; <code>base_model</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>base_model_score_return()</strong>
</div>
&emsp; Returns the value of <code>base_metric</code> achieved by the <code>base_model</code> from the given RashomonSet object and an empty plot. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>empty_plot</code> : go.Figure
</br>
&emsp; <code>base_score</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>base_metric_return()</strong>
</div>
&emsp; Returns the <code>base_metric</code> name used in the given RashomonSet object and an empty plot. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>empty_plot</code> : go.Figure
</br>
&emsp; <code>base_metric</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>number_of_classes_return()</strong>
</div>
&emsp; Returns the number of classes obtained in the given RashomonSet object and an empty plot. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>empty_plot</code> : go.Figure
</br>
&emsp; <code>number_of_classes</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>set_size_indicator()</strong>
</div>
&emsp; Creates the gauge plot representing the number of models from the whole leaderboard that are included in the analyzed RashomonSet. Returns the plot and its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>gauge_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>rashomon_ratio_indicator()</strong>
</div>
&emsp; Creates the Indicator plot for the <code>rashomon_ratio</code> metric obtained from the Rashomon Set. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>indicator_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>pattern_ratio_indicator()</strong>
</div>
&emsp; Creates the Indicator plot for the <code>pattern_rashomon_ratio</code> metric obtained from the Rashomon Set. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>indicator_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>lolipop_ambiguity_discrepancy()</strong>
</div>
&emsp; Creates the Lolipop chart for the <code>ambiguity</code> and <code>discrepancy</code> metrics obtained from the Rashomon Set. The x-axis represents the metric (e.g ambiguity or discrepancy) and the y-axis presents it's value. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>lolipop_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>lolipop_ambiguity_discrepancy_proba_version(<code>delta</code>)</strong>
</div>
&emsp; Creates the Lolipop chart for the <code>probabilistic_ambiguity</code> and <code>probabilistic_discrepancy</code> metrics obtained from the Rashomon Set. The x-axis represents the metric (e.g ambiguity or discrepancy) and the y-axis presents it's value for the given delta. Returns the plot with its description.
</br>
</br>
Note : Method available only for binary classification task type.
</br>
</br>
&emsp; <strong>Parameters :</strong> </br>
&emsp;<code>delta</code> : float
</br>
&emsp;&emsp;<em>delta parameter indicates the minimum difference between two risk probabilities for the predictions to be considered conflicting.</em>
</br>
<br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>lolipop_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>ambiguity_vs_epsilon()</strong>
</div>
&emsp; Creates the Line chart of the possible <code>ambiguity</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding ambiguities. The actual ambiguity value for the given Rashomon Set is highlighted with a different color. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>proba_ambiguity_vs_epsilon(<code>delta</code>)</strong>
</div>
&emsp; Creates the Line chart of the possible <code>probabilistic_ambiguity</code> values for the given delta with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding ambiguities. The actual ambiguity value for the given Rashomon Set is highlighted with the different color. Returns the plot with its description.
</br>
</br>
Note : Method available only for binary classification task type.
</br>
</br>
&emsp; <strong>Parameters :</strong> </br>
&emsp;<code>delta</code> : float
</br>
&emsp;&emsp;<em>delta parameter indicates the minimum difference between two risk probabilities for the predictions to be considered conflicting.</em>
</br>
<br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>discrepancy_vs_epsilon()</strong>
</div>
&emsp; Creates the Line chart of the possible <code>discrepancy</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding discrepancies. The actual discrepancy value for the given Rashomon Set is highlighted with the different color. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>proba_discrepancy_vs_epsilon(<code>delta</code>)</strong>
</div>
&emsp; Creates the Line chart of the possible <code>probabilistic_discrepancy</code> values for the given delta with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding discrepancies. The actual discrepancy value for the given Rashomon Set is highlighted with a different color. Returns the plot with its description.
</br>
</br>
Note : Method available only for binary classification task type.
</br>
</br>
&emsp; <strong>Parameters :</strong> </br>
&emsp;<code>delta</code> : float
</br>
&emsp;&emsp;<em>delta parameter indicates the minimum difference between two risk probabilities for the predictions to be considered conflicting.</em>
</br>
<br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>rashomon_ratio_vs_epsilon()</strong>
</div>
&emsp; Creates the Line chart of the possible <code>rashomon_ratio</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding rashomon_ratios. The actual rashomon_ratio value for the given Rashomon Set is highlighted with a different color. Returns the plot with its description.
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
&emsp; Creates the Line chart of the possible <code>pattern_rashomon_ratio</code> values with respect to different <code>epsilons</code>. The x-axis represents the epsilon values, while the y-axis shows the corresponding pattern_rashomon_ratios. The actual pattern_rashomon_ratio value for the given Rashomon Set is highlighted with the different color. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>line_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>proba_probabilities_for_sample(<code>sample_index</code>)</strong>
</div>
&emsp; Visualizes the predicted probabilities for the chosen sample across all models present in the Rashomon Set. The sizes of the segments indicate how confident each model is in predicting each class. If the number of possible classes is greater than 10, the barplot is switched to a heatmap for better clarity. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Parameters :</strong> </br>
&emsp; <code>sample_index</code> : int <br>
&emsp; &emsp; <em>index of the sample for which predictions are to be plotted</em>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>probabilities_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>rashomon_capacity_for_sample(<code>sample_index</code>)</strong>
</div>
&emsp; Method to visualize <code>rashomon_capacity</code> metric for given sample index. It creates a 1D plot, where the x-axis represents the range of possible Rashomon Capacity values from 1 to number of classes in the classification task (marked as black dots). The highlighted dot represents Rashomon Capacity value for the selected sample. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Parameters :</strong> </br>
&emsp; <code>sample_index</code> : int <br>
&emsp; &emsp; <em>index of the sample for which predictions are to be plotted</em>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>scatter_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>rashomon_capacity_distribution()</strong>
</div>
&emsp; Visualizes the distribution of <code>rashomon_capacity</code> values across all samples in the dataset. The histogram visualizes the frequency of different capacity values. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>histogram_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>rashomon_capacity_distribution_by_class()</strong>
</div>
&emsp; Creates a visualization of the distribution of the <code>rashomon capacity</code> metric across all samples, grouped by their true class labels. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>box_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>percent_agreement_barplot()</strong>
</div>
&emsp; Visualizes the distribution of <code>percent_agreements</code> for all models in the Rashomon Set. The x-axis represents the different models, while the y-axis shows the corresponding percent_agreements with the base model. The horizontal line indicates the mean value of the percent_agreement across all models (besides the base_model) from the Rashomon Set. Returns the plot with its description. 
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>bar_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>cohens_kappa_diverging_barplot()</strong>
</div>
&emsp; Visualizes the distribution of <code>cohens_kappa</code> for all models in the Rashomon Set with respect to the base model. The y-axis represents the different models, while the x-axis shows the corresponding Cohen's Kappa metric value with the base model. Returns the plot with its description. 
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>fig</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>cohens_kappa_heatmap()</strong>
</div>
&emsp; Generates a heatmap of Cohen’s Kappa values for every pair of models in the Rashomon Set, illustrating the level of agreement between their predictions. Returns the plot with its description. 
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>fig</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>


<div style="color: #60824f; font-size: 18px;">
    <strong>generate_rashomon_set_table()</strong>
</div>
&emsp; Creates the table containing all models from the Rashomon Set with their values of the <code>base_metric</code> sorted in a descending order with the highlighted name of the base model. Additionally, a brief text description of the Rashomon Set main properties is returned. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>table</code> : pd.DataFrame
</br>
&emsp; <code>set_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>vprs_widths_plot()</strong>
</div>
&emsp; Visualizes the distribution of <code>VPRs</code> widths for all observations in the test dataset grouped by their true class label in a form of Box plots with visible points. The x-axis represents the class label (0 or 1), while the y-axis shows the corresponding VPRs widths. Returns the plot with its description.
</br>
</br>
Note : Method available only for binary classification task type.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>box_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>vpr_width_histogram()</strong>
</div>
&emsp; Creates the histogram of <code>VPRs</code> widths for all observations in the test dataset. The number of bins is determined using the Freedman–Diaconis method. The x-axis represents the ranges of VPR widths, while the y-axis indicates the number of observations falling within each range. Returns the plot with its description.
</br>
</br>
Note : Method available only for binary classification task type.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>histogram_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>feature_importance_table()</strong>
</div>
&emsp; Generates a table summarizing feature importance information. It provides information about the ranking and occurrence of the most important features across the base model and all models in the Rashomon set. If feature importances are not available for a certain model, the table column is empty. 
<br><br>
&emsp; Table columns:<br>
&emsp; <code>Rank</code> – the position of the feature (1 being the most important).<br>
&emsp; <code>Base Model Top 3</code> – the three most important features for the base model, if feature importance is available.<br>
&emsp; <code>Most Frequent in Rashomon Set</code> – the features that most frequently appear as the 1st, 2nd, or 3rd most important across all models in the Rashomon set.<br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>table</code> : go.Figure
</br>
&emsp; <code>table_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>feature_importance_heatmap()</strong>
</div>
&emsp; Generates a heatmap visualizing the top three most important features 
for each model in the Rashomon set. The x-axis shows feature names and the y-axis lists models from the Rashomon set.<br>
<br>
Feature ranks are defined as follows:<br>
Rank = 0 – feature is not present in the top 3 most important features.<br>
Rank = 1 – feature is the most important feature selected by the model.<br>
Rank = 2 – feature is the second most important feature selected by the model.<br>
Rank = 3 – feature is the third most important feature selected by the model.<br>
</br>
Cell colors represent the feature’s rank within each model. No color represents a feature not present in the top 3 for the model. The most important feature for model (Rank 1) is represented by red color, second most important (Rank 2) by orange and third most important (Rank 3) by yellow.
</br>
<br>
<em>Note: If any model present in the Rashomon Set does not have feature importance available, then its corresponding row of the heatmap is empty. In other words, an empty row does not indicate that the model does not consider any of the features important. </em>
</br>
<br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>heatmap_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>agreement_rates_density()</strong>
</div>
&emsp; Creates the Violin plot of the <code>agreement_rate</code> values for all observations in the test dataset. Returns the plot with its description.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>violin_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>vprs_vs_base_model_plot()</strong>
</div>
&emsp; Creates the violin plot showing how the base model's risk predictions compare to the range of predictions produced by all models in the Rashomon set. For each observation, the Viable Prediction Range (VPR) is defined as  [min risk prediction, max risk prediction] across all models from the Rashomon Set. This plot allows the user to see where the base model's prediction falls within this range for each observation. For the positive class the difference is calculated as the max risk prediction - base model's risk prediction, while for the negative class it's the base model's risk prediction - min risk prediction.
</br>
</br>
Note : Method available only for binary classification task type.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>violin_plot</code> : go.Figure
</br>
&emsp; <code>plot_descr</code> : str
</br>
</br>
[back](index.md)

# BuildRashomonFromConverted

<div style="background-color: #c2deb1; padding: 10px; border-radius: 4px;">
class rashomon_analysis.pipelines.pipelines_from_converters.<strong>BuildRashomonFromConverted</strong>(converter_results_path, base_metric, delta)
</div>
</br>
This is a subclass of <code>Builder</code> abstract class, which provides pipeline for creating and exploring the Rashomon Set created from parameters in a format propsed by the convert() method of converter classes.
</br>
</br>
Example usage of this pipeline can be found at <code>demo_notebooks/converters_pipeline.ipynb</code>.
</br>
</br>
</br>

<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Parameters</strong>
</div>
</br>
    <strong>converter_results_path</strong> : Path </br>
     &emsp;  Path to a folder where all necessary files are stored. Obligatory files to be included in this folder are:
    </br>
    &emsp; 1. leaderboard.csv : file containing all trained models and their evaluation metrics scores.<br>
    &emsp; 2. y_true.csv: target column from test dataset.<br>
    &emsp; 3. predictions_dict.pkl : dictionary with model names as keys and their class prediction vectors as values.<br>
    &emsp; 4. proba_predictions.pkl : dictionary with model names as keys and their probabilities predictions as values.<br>
    &emsp; 5. (optional) feature_importance_dict.pkl : dictionary with model names as keys and their features sorted descending by their feature importance as values. <br>
    </br>
    If you do not have the necessary files, please visit documentation of the pipelines accepting raw models as input:

[H2O pipeline](pipeline_user_input_rashomon_H2O.md) <br>
[AutoGluon pipeline](pipeline_user_input_rashomon_autogluon.md) <br>
<br>
    <strong>base_metric</strong> : str </br>
    &emsp; Evaluation metric to be used as the <code>base_metric</code> while creating the Rashomon Set.
    </br>
    <strong>delta</strong> : float </br>
     &emsp; Delta parameter for probabilistic ambiguity and discrepancy (used only for binary task type). <br>
     &emsp; If not specified the default value of 0.1 will be used.
</br>
</br> 

<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
    <strong>BuildRashomonFromConverted Pipeline – Key Steps</strong>
</div>
<br>
<ol>
    <li><strong>Initialization (<code>__init__</code>)</strong> – Evaluation of the given arguments. If the provided folder contains all necessary files the Pipeline is initialized.</li>
    <li><strong>Preview Rashomon (<code>preview_rashomon()</code>)</strong> – Visualize leaderboard and Rashomon Set sizes to guide epsilon selection.</li>
    <li><strong>Set Epsilon (<code>set_epsilon()</code>)</strong> – Set epsilon parameter value to be used when creating the Rashomon Set.</li>
    <li><strong>Build Pipeline (<code>build()</code>)</strong> – Create RashomonSet and Visualizer objects and launch the Streamlit dashboard in the background.</li>
    <li><strong>Interactive Analysis</strong> – Explore plots via returned Visualizer object or the dashboard.</li>
    <li><strong>Close Dashboard (<code>dashboard_close()</code>)</strong> – Stop Streamlit processes.</li>
</ol>


<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>preview_rashomon()</strong>
</div>
&emsp; Method presenting the leaderboard and the plot with all possible epsilon values and the corresponding Rashomon Set sizes. <br>
&emsp; Should be called to guide the selection of an appropriate epsilon threshold.
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>visualize_rashomon_set_volume()</strong>
</div>
&emsp; Method for visualising Rashomon Set size depending on different epsilon values.
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>set_epsilon(<code>epsilon</code>)</strong>
</div>
&emsp; Sets the epsilon parameter value to be used when constructing the Rashomon Set object.<br>
&emsp; <strong> Epsilon value must be set before calling build() method. </strong>
</br>
</br>
&emsp; <strong>Parameters :</strong> </br>
&emsp; <code>epsilon</code> : float <br>
<br>

<div style="color: #60824f; font-size: 18px;">
    <strong>build()</strong>
</div>
&emsp;Builds the Rashomon Set pipeline from converted files found in the given directory and other provided parameters. <br>
&emsp; Creates the Rashomon Set object and Visualizer object from user's input and launches a Streamlit dashboard in a subprocess for interactive visualization.
</br>
</br>
&emsp; This method performs the following steps:
<ul>
<li>Validates that the epsilon threshold has been set using <code>set_epsilon()</code> method.</li><br>
<li>Creates the <code>RashomonSet</code> object based on the leaderboard, predictions, probability predictions, feature importances, metrics, methods to select base model, and epsilon threshold. <br>
<li>Initializes the <code>Visualizer</code> object for interactive analysis of the Rashomon Set. <br>
Individual plots can later be generated directly from the <code>Visualizer</code> object.</li><br>
<li>Generates plots for analysis depending on the task type (binary or multiclass), and stores them temporarily with their descriptions for the Streamlit dashboard.</li><br>
<li>Closes any previous Streamlit processes to avoid conflicts.</li><br>
<li>Launches the Streamlit dashboard in a subprocess on the local machine (localhost), allowing interactive exploration of the Rashomon Set properties without blocking the main workflow.</li>

</ul>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>rashomon_set</code> : RashomonSet
</br>
&emsp; <code>visualizer</code> : Visualizer
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>dashboard_close()</strong>
</div>
&emsp; Method for stopping all Streamlit processes and closing the dashboard.<br>
&emsp; Note: <em>Always call this method after finishing the analysis to ensure the dashboard is properly closed.</em>

<br>




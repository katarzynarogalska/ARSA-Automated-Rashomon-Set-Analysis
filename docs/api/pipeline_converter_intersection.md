[back](index.md)

# BuildIntersectionFromConverted

<div style="background-color: #c2deb1; padding: 10px; border-radius: 4px;">
class rashomon_analysis.pipelines.pipelines_from_converters.<strong>BuildIntersectionFromConverted</strong>(converter_results_path, metrics, custom_weights, weighted_sum_method, delta)
</div>
</br>
This is a subclass of the <code>Builder</code> abctract class, which provides pipeline for creating and exploring the Rashomon Intersection created from parameters in a format propsed by the convert() method of converter classes.
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
    <strong>metrics</strong> : list </br>
    &emsp; Evaluation metrics to be used as the <code>metrics</code> list while creating the Rashomon Intersection.
    </br>
    <strong>custom_weights</strong> : list </br>
    &emsp; List containing two values of custom weights assigned by the user to every evaluation metric present in the <code>metrics</code> list. Can be set only while using the <code>'custom_weights'</code> weighted sum method. Default is None.
    </br>
    <strong>weighted_sum_method</strong> : str </br>
    &emsp; Name of the <code>weighted_sum_method</code> to be used while selecting the <code>base_model</code> in the Rashomon Intersection. Possible options are 'entropy','critic', 'custom_weights'. Default is 'entropy'.
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
    <li><strong>Preview Rashomon (<code>preview_rashomon()</code>)</strong> – Visualize leaderboard and Rashomon Intersection sizes to guide epsilon selection.</li>
    <li><strong>Set Epsilon (<code>set_epsilon()</code>)</strong> – Set epsilon parameter value to be used when creating the Rashomon Intersection.</li>
    <li><strong>Build Pipeline (<code>build()</code>)</strong> – Create RashomonIntersection and IntersectionVisualizer objects and launch the Streamlit dashboard in the background.</li>
    <li><strong>Interactive Analysis</strong> – Explore plots via returned IntersectionVisualizer object or the dashboard.</li>
    <li><strong>Close Dashboard (<code>dashboard_close()</code>)</strong> – Stop Streamlit processes.</li>
</ol>


<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>preview_rashomon()</strong>
</div>
&emsp; Method illustrating the leaderboard and the plot with all possible epsilon values and the Rashomon Intersection sizes for different epsilon values. <br>
&emsp; Should be called to guide the selection of an appropriate epsilon threshold.
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>visualize_rashomon_set_volume()</strong>
</div>
&emsp; Method for visualising Rashomon Intersection size depending on different epsilon values.
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>set_epsilon(<code>epsilon</code>)</strong>
</div>
&emsp; Sets the epsilon parameter value to be used when constructing the Rashomon Intersection object.<br>
&emsp; <strong> Epsilon value must be set before calling build() method. </strong>
</br>
</br>
&emsp; <strong>Parameters :</strong> </br>
&emsp; <code>epsilon</code> : float <br>
<br>

<div style="color: #60824f; font-size: 18px;">
    <strong>build()</strong>
</div>
&emsp;Builds the Rashomon Intersection pipeline from converted files found in the given directory and other provided parameters. <br>
&emsp; Creates Rashomon Intersection object and IntersectionVisualizer object from user's input and launches a Streamlit dashboard in a subprocess for interactive visualization.
</br>
</br>
&emsp; This method performs the following steps:
<ul>
<li>Validates that the epsilon threshold has been set using <code>set_epsilon()</code> method.</li><br>
<li>Creates the <code>RashomonIntersection</code> object based on the leaderboard, predictions, probability predictions, feature importances, metrics, methods to select base model, and epsilon threshold. <br>
<li>Initializes the <code>IntersectionVisualizer</code> object for interactive analysis of the Rashomon Intersection. <br>
Individual plots can later be generated directly from the <code>IntersectionVisualizer</code> object.</li><br>
<li>Generates plots for analysis depending on the task type (binary or multiclass), and stores them temporarily with their descriptions for the Streamlit dashboard.</li><br>
<li>Closes any previous Streamlit processes to avoid conflicts.</li><br>
<li>Launches the Streamlit dashboard in a subprocess on the local machine (localhost), allowing interactive exploration of the Rashomon Intersection properties without blocking the main workflow.</li>

</ul>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>rashomon_intersection</code> : RashomonIntersection
</br>
&emsp; <code>visualizer</code> : IntersectionVisualizer
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>dashboard_close()</strong>
</div>
&emsp; Method for stopping all Streamlit processes and closing the dashboard.<br>
&emsp; Note: <em>Always call this method after finishing the analysis to ensure the dashboard is properly closed.</em>

<br>
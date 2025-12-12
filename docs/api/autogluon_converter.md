[back](index.md)

# PredictorConverter 

<div style="background-color: #c2deb1; padding: 10px; border-radius: 4px;">
class rashomon_analysis.converters.<strong>PredictorConverter</strong>(predictor, test_data, df_name, feature_imp_needed = True)
</div>
</br>
This subclass of the Converter abstract class, which is used to transform Autogluon trained TabularPredictor object into leaderboard and dictionaries that can be used to build the Rashomon Set.
</br>
</br>

<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Parameters</strong>
</div>
</br>
<strong>predictor</strong> : TabularPredictor </br>
    &emsp;   Trained TabularPredictor AutoGluon object.
</br>
<strong>test_data</strong> : TabularDataset </br>
&emsp;   Test data for analysis in a TabularDataset format.
</br>
<strong>df_name</strong> : str </br>
&emsp; The name of the dataset to be used while saving converted results.
</br>
<strong>feature_imp_needed</strong> : bool, default = True </br>
&emsp; Whether to obtain feature importances from trained models or not. Can  
result in a longer runtime of .convert() method.
</br>
</br> 
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Attributes</strong>
</div>
</br>
<strong>predictor</strong> : TabularPredictor </br>
predictor parameter
</br>
<strong>test_data</strong> : TabularDataset </br>
&emsp;   test_data parameter
</br>
<strong>df_name</strong> : str </br>
&emsp; df_name parameter
</br>
<strong>feature_imp_needed</strong> : bool </br>
&emsp; feature_imp_needed parameter
</br>
<strong>metrics</strong> : list </br>
&emsp; list of all evaluation metrics extracted from AutoGluon -  multiclass or binary based on the predictor's problem_type attribute.
</br>
<strong>leaderboard</strong> : pd.DataFrame </br>
&emsp; leaderboard created with the create_leaderboard() method consisting only of the selected evaluation metrics.
</br>
</br>
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
</br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>create_leaderboard()</strong>
</div>
&emsp; Creates a dataframe with all trained models and their evaluation metrics values obtained from predictor.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>leaderboard</code> : pd.DataFrame
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>create_predictions_dict()</strong>
</div>
&emsp; Creates a dictionary with model names as keys and their class prediction vectors as values.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>predictions_dict</code> : dict[str, pd.Series]</br>
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>create_proba_predictions_dict()</strong>
</div>
&emsp; Creates a dictionary with model names as keys and their class probabilities predictions as values.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>proba_predictions_dict</code> : dict[str, pd.Dataframe(n_observations, n_classes)]</br>
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>create_feature_importance_dict()</strong>
</div>
&emsp; Creates a dictionary where the keys are model names and the values are lists of features sorted in descending order of importance, so that the most important feature appears first in each list. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>feature_importance_dict</code> : dict[str, list]</br>
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>extract_target_column()</strong>
</div>
&emsp; Extracts the target column from the test dataset using the .label attribute of the TabularPredictor object.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>y_true</code> : pd.DataFrame</br>
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>save_results(<code>leaderboard, predictions_dict, proba_predictions_dict, feature_importance_dict, y_true, saving_path</code>)</strong>
</div>
&emsp;Method for saving results from creating a leaderboard and all dictionaries on disk in .csv and .pickle formats.
</br>
</br>
&emsp;<strong> Parameters :</strong> </br>
&emsp; <code>leaderboard</code> : pd.DataFrame </br>
&emsp; &emsp; <em>created_ leaderboard to be saved as csv</em> </br>
</br>
&emsp; <code>predictions_dict</code> : dict </br>
&emsp; &emsp; <em>created predictions dict to be saved as pickle</em></br>
</br>
&emsp; <code>proba_predictions_dict</code> : dict </br>
&emsp; &emsp;<em> created proba predictions dict to be saved as pickle</em> </br>
</br>
&emsp; <code>feature_importance_dict</code> : dict </br>
&emsp; &emsp;<em> created feature importance dict to be saved as pickle</em></br>
</br>
&emsp; <code>y_true</code> : pd.DataFrame </br>
&emsp; &emsp;<em> extracted target column to be saved as a csv</em></br>
</br>
&emsp; <code>saving_path</code> : Path </br>
&emsp; &emsp;<em> path to a directory where results should be saved, if not specified the default of timestamp + df_name is used to create a new directory</em></br>
</br>
    </br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>convert(<code>saving_path</code>)</strong>
</div>
&emsp; Final method used to create leaderboard, predictions_dict, proba_predictions dict and feature_importance_dict and save the results using save_results() method. If feature_imp_needed parameter is False, feature_importance_dict is not created and the method returns NaN as its value.
</br>
</br>
&emsp;<strong> Parameters :</strong> </br>
&emsp; <code>saving_path</code> : Path </br>
&emsp; &emsp; <em>path to a directory where results should be saved, if not specified the default of timestamp + df_name is used to create a new directory</em> </br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>leaderboard</code> : pd.DataFrame </br>
&emsp; &emsp; <em>created_ leaderboard using create_leaderboard() method</em> </br>
</br>
&emsp; <code>predictions_dict</code> : dict[str, pd.Series] </br>
&emsp; &emsp; <em>created predictions dict created using create_predictions_dict() method</em></br>
</br>
&emsp; <code>proba_predictions_dict</code> : dict[str, pd.DataFrame] </br>
&emsp; &emsp;<em> created proba predictions dict created using create_proba_predictions_dict() method</em> </br>
</br>
&emsp; <code>feature_importance_dict</code> : dict[str, list] </br>
&emsp; &emsp;<em> created feature importance dict created using create_feature_importance_dict() method</em></br>
</br>
&emsp; <code>y_true</code> : pd.DataFrame </br>
&emsp; &emsp;<em> extracted target column using extract_target_column() method</em></br>
</br>
</br>    




     

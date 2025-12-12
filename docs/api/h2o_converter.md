[back](index.md)

# H2OConverter 

<div style="background-color: #c2deb1; padding: 10px; border-radius: 4px;">
class rashomon_analysis.converters.<strong>H2OConverter</strong>(models_directory, test_data, target_column, df_name, feature_imp_needed=True)
</div>
</br>
This is a subclass of the Converter abstract class, wich is used to transform H2O trained models into leaderboard and dictionaries that can be used to build the Rashomon Set. Uses H2O framework that expects Java to be installed.
</br>
</br>

<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Parameters</strong>
</div>
</br>
<strong>models_directory</strong> : Path </br>
    &emsp;   Path object navigating to the directory with saved models from H2O framework.
</br>
<strong>test_data</strong> : H2OFrame </br>
&emsp;   Test data for analysis in a H2OFrame format.
</br>
<strong>target_column</strong> : str </br>
&emsp;   Name of the target column. Used to determine the task type - binary or multiclass classification.
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
<strong>task_type</strong> : str </br>
&emsp; Name of the task type - 'binary' or 'multiclass' indicating whether models were trained for binary or multiclass classification purposes. Obtained from determine_task_type() method.
</br>
<strong>loaded_models</strong> : list </br>
&emsp; List containing all models that were loaded from the given models_directory. Obtained from load_all_models() method.
</br>
<strong>prediction_frames_dict</strong> : dict </br>
&emsp; A dictionary containing loaded models as keys and pd.DataFrames containing predcitions returned by H2O models as values. Obtained from get_prediction_frames_dict() method.
</br>
<strong>class_prediction_dict</strong> : dict </br>
&emsp; A dictionary containing loaded models as keys and pd.Series containing class predcitions obtained from H2O models as values in pd.Series format. Calculated by get_class_predictions_dict() method.
</br>
<strong>proba_prediction_dict</strong> : dict </br>
&emsp; A dictionary containing loaded models as keys and pd.Series containing class probabilities predcitions obtained from H2O models as values in pd.DataFrame format. Calculated by get_proba_predictions_dict() method.
</br>
<strong>classes</strong> : list </br>
&emsp; List of all classes found for a given task. Obtained from the test_data. 
</br>
<strong>MULTICLASS_METRICS_DICT</strong> : dict </br>
&emsp; A dictionary containing typical multiclasss classification evaluation metrics name and their implementation functions from sklearn.
</br>
<strong>BINARY_METRICS_DICT</strong> : dict </br>
&emsp; A dictionary containing typical binary classification evaluation metrics name and their implementation functions from sklearn.
</br>
<strong>models_directory</strong> : Path </br>
    &emsp;   models_directory parameter value
</br>
<strong>test_data</strong> : H2OFrame </br>
&emsp;   test_data parameter value
</br>
<strong>target_column</strong> : str </br>
&emsp;  target_column parameter value
</br>
<strong>df_name</strong> : str </br>
&emsp; df_name parameter value
</br>
<strong>feature_imp_needed</strong> : bool, default = True </br>
&emsp; feture_imp_needed parameter value
</br>
</br>
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
</br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>determine_task_type()</strong>
</div>
&emsp; Returns whether the task type for a given dataset is binary or multiclass classification based on target_column and test_data parameters. If another task type is determined, the method throws ValueError. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>task_type</code> : str
</br>
</br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>load_all_models()</strong>
</div>
&emsp; Loads all H2O models objects from a given model_directory and saves them in a list format. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>loaded_models</code> : list
</br>
</br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>get_prediction_frames()</strong>
</div>
&emsp; Used to obtain predictions returned by all H2O models and save them in a dictionary format with model names as keys and predictions dataframes as values. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>predictions</code> : dict[str, pd.DataFrame]
</br>
</br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>get_class_predictions_dict()</strong>
</div>
&emsp; Used to obtain class predictions returned by all H2O models and save them in a dictionary format with model names as keys and predictions in a pd.Series format as values. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>class_predictions_dict</code> : dict[str, pd.Series]
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>get_proba_predictions_dict()</strong>
</div>
&emsp; Used to obtain class probabilities predictions returned by all H2O models and save them in a dictionary format with model names as keys and probability predictions in a pd.DataFrame format as values. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>proba_predictions_dict</code> : dict[str, pd.DataFrame]
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>get_feature_importance_dict()</strong>
</div>
&emsp; Used to obtain feature importances from all H2O models and save them in a dictionary format with model names as keys and features sorted in a descending order based on their importance as values.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>feature_importance_dict</code> : dict[str, list]
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>extract_target_column()</strong>
</div>
&emsp; Used to extract the target column from the test dataset. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>y_true</code> : pd.DataFrame
</br>
</br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>calculate_multiclass_metrics()</strong>
</div>
&emsp; Calculates multiclass classification evaluation metrics from MULTICLASS_METRICS_DICT for all loaded models based on their prediction vectors and target column. Calculated results are stored in a pd.DataFrame object containing all evaluation metric scores for each model.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>metrics_df</code> : pd.DataFrame
</br>
</br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>calculate_binary_metrics()</strong>
</div>
&emsp; Calculates binary classification evaluation metrics from BINARY_METRICS_DICT for all loaded models based on their prediction vectors and target column. Calculated results are stored in a pd.DataFrame object containing all evaluation metric scores for each model.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>metrics_df</code> : pd.DataFrame
</br>
</br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>save_results(<code>leaderboard, predictions_dict, proba_predictions_dict, feature_importance_dict, y_true, saving_path</code>)</strong>
</div>
&emsp;Method for saving results from creating a leaderboard and all dictionaries on disk in .csv and .pickle formats.
</br>
</br>
    &emsp;<strong> Parameters :</strong> </br>
    &emsp; <code>leaderboard</code>: pd.DataFrame </br>
    &emsp; &emsp; <em>created leaderboard to be saved as csv</em> </br>
    </br>
    &emsp; <code>predictions_dict</code> : dict </br>
    &emsp; &emsp; <em>created class predictions dict to be saved as pickle</em></br>
    </br>
    &emsp; <code>proba_predictions_dict </code>: dict </br>
    &emsp; &emsp;<em> created proba predictions dict to be saved as pickle</em> </br>
    </br>
    &emsp; <code>feature_importance_dict</code> : dict </br>
    &emsp; &emsp;<em> created feature importance dict to be saved as pickle</em></br>
</br>
    &emsp; <code>y_true</code> : pd.DataFrame </br>
    &emsp; &emsp;<em> extracted target column to be saved as a csv</em></br>
</br>
    &emsp; <code>saving_path</code> : Path </br>
    &emsp; &emsp;<em> path to a directory where the results should be saved, if not specified the default of timestamp + df_name is used to create a new directory</em></br>
    <br>
<div style="color: #60824f; font-size: 0.9rem;">
    <strong>convert(<code>saving_path</code>)</strong>
</div>
&emsp; Final method used to create and save leaderboard created in calculate_binary_metrics() or calculate_multiclass_metrics() based on the task type, class_predictions_dict, proba_predictions_dict and feature_importance_dict created in the corresponding methods. If feature_imp_needed parameter is False, feature_importance_dict is not created and the method returns NaN as its value.
</br>
</br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp; <code>saving_path</code> : Path </br>
    &emsp; &emsp;<em> path to a directory where the results should be saved, if not specified the default of timestamp + df_name is used to create a new directory</em></br>
    <br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>leaderboard</code> : pd.DataFrame
</br>
</br>
&emsp; <code>class_predictions_dict</code> : dict[str, pd.Series]
</br>
</br>
&emsp; <code>proba_predictions_dict</code> : dict[str, pd.DataFrame]
</br>
</br>
&emsp; <code>feature_importance_dict</code> : dict[str, list]
</br>
</br>
&emsp; <code>y_true</code> : pd.DataFrame
</br>
</br>
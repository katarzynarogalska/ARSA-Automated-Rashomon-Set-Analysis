[back](index.md)

# Converter - abstract class

<div style="background-color: #7ea1ee7a; padding: 10px; border-radius: 4px; ">
class rashomon_analysis.converter.<strong>Converter</strong>
</div>
<br>
This class is an abstract class asserting all converter classes have the same set of obligatory methods. Converters are used to provide models results to the RashomonSet/RashomonIntersection in a correct format.

<br>
<br>


<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
<br>
<strong>Note:</strong> 
All methods are decorated as <code>@abstractmethod</code> and must be implemented in every child class.
<br>
<br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>create_predictions_dict()</strong>
</div>
Method for extracting trained models and their class predictions from a used framework. Returns the results in a dictionary format with model names as keys and their class prediction vector (pandas.Series) as values.
<br>
<br>
<strong>Returns :</strong> <br>
<code>predictions_dict</code> : dict[str, pd.Series]
<br>
<br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>create_proba_predictions_dict()</strong>
</div>
   Method for extracting trained models and their probability predictions from a used framework. Returns the results in a dictionary format with model names as keys and their probabilistic predictions (pandas.DataFrame) as values.
   </br>
   </br>
   <strong>Returns :</strong> </br>
   <code>proba_predictions_dict</code> : dict[str, pd.DataFrame]
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>create_feature_importance_dict()</strong>
</div>
   Method for extracting trained models and their feature importance from a used framework. Returns the results in a dictionary format with model names as keys and the list of features sorted by feature importance as values.
    </br>
    </br>
    <strong>Returns :</strong> </br>
    <code>feature_importance_dict</code> : dict[str, list]
    </br>
    </br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>save_results(<code>leaderboard, predictions_dict, proba_predictions_dict, feature_importance_dict, y_true, saving_path</code>)</strong>
</div>
Method for saving results returned by the <code>convert()</code> method in a specified or default directory.
</br>
</br>
<strong> Parameters :</strong> </br>
<code>leaderboard</code>: pd.DataFrame </br>
<em>created leaderboard to be saved as csv</em> </br>
</br>
<code>predictions_dict</code> : dict </br>
<em>created class predictions dict to be saved as pickle</em></br>
</br>
<code>proba_predictions_dict </code>: dict </br>
<em> created proba predictions dict to be saved as pickle</em> </br>
</br>
 <code>feature_importance_dict</code> : dict </br>
<em> created feature importance dict to be saved as pickle</em></br>
</br>
<code>y_true</code> : pd.DataFrame </br>
<em> extracted target column to be saved as a csv</em></br>
</br>
<code>saving_path</code> : Path </br>
<em> path to a saving directory, if not specified default is timestamp + df_name</em></br>
<br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>convert(<code>saving_path</code>)</strong>
</div>
   &emsp; Primary method performing all the necessary calculations and returning the converted objects: <br>
            1. pd.DataFrame - leaderboard with all models and their scores <br>
            2. dict : predictions_dict<br>
            3. dict : proba_predictions_dict<br>
            4. dict : feature_importance_dict (or None if feature importance was not needed)<br>
            5. pd.DataFrame : y_true <br>
    </br>
    </br>
     &emsp;<strong> Parameters :</strong> </br>
     &emsp; <code>saving_path</code>: Path </br>
     &emsp; &emsp; <em>path to a saving directory, if not specified default is timestamp + df_name</em> </br>
     </br>
     &emsp; <strong>Returns :</strong> </br>
     &emsp; <code>leaderboard</code> : pd.DataFrame <br>
     &emsp; <code>predictions_dict</code> : dict <br>
     &emsp; <code>proba_predictions_dict</code> : dict<br>
     &emsp; <code>feature_importance_dict</code> : dict<br>
     &emsp; <code>y_true</code> : pd.DataFrame <br>
    </br>
    </br>
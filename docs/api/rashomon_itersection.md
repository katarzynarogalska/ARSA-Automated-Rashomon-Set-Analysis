[back](index.md)

# RashomonIntersection


<div style="background-color: #c2deb1; padding: 10px; border-radius: 4px;">
class rashomon_analysis.<strong>RashomonIntersection</strong>(leaderboard, predictions, proba_predictions, feature_importances, metrics, epsilon, custom_weights, weighted_sum_method)
</div>
</br>
This class is used for calculating Rashomon Set Intersection for two Rashomon Sets based on two different metrics. The class inherits from RashomonSet, providing access to all metrics and attriutes implemented in the RashomonSet class, only modifies the selection of Rashomon Sets and the base model.
</br>
</br>

<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Parameters</strong>
</div>
</br>
    <strong>leaderboard</strong> : pd.DataFrame </br>
     &emsp;  Leaderboard in a DataFrame format consisting of models and their evaluation metrics scores.(Returned by converters)
    </br>
    <strong>predictions</strong> : dict </br>
    &emsp;  Dictionary with model names as keys and class prediction vectors as values. (Returned by converters)
    </br>
    <strong>proba_predictions</strong> : dict </br>
    &emsp; Dictionary with model names as keys and class probabilities prediction DataFrames as values. (Returned by converters)
    </br>
    <strong>metrics</strong> : str </br>
    &emsp; List containing two distinct evaluation metrics used to compute Rashomon Sets and determine their intersection. Evaluation metrics are used as a primary value for sorting model performances. Allowed metrics are specified in METRICS attribute. 
    </br>
    <strong>epsilon</strong> : float </br>
    &emsp; Epsilon parameter specifying the allowable deviation from the best score for each evaluation metric, within which models are included in their respective Rashomon Sets and used to compute their intersection.
    </br>
    <strong>custom_weights</strong> : list </br>
     &emsp; List with two elements specifying custom weights when searching for base model. If weighted_sum is 'custom_weights' then the user must specify weights in 2-element list with elements that sum to 1, if not leave it at default value = None.
    </br>
    <strong>weighted_sum_method</strong> : str </br>
     &emsp; Parameter that specifies the method or weights for selecting the base model. Options are:
     <ul>
    <li><strong>None</strong> or <strong>'entropy'</strong> (default): Uses an entropy-based weighting method to select the base model.</li>
    <li><strong>'critic'</strong>: Uses the CRITIC method to determine weights for selecting the base model.</li>
    <li><strong>'custom_weights'</strong>: Allows manual specification of weights as a 2-element list whose values sum to 1.</li>
    </ul>
</br>
</br> 
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Attributes</strong>
</div>
</br>
<strong>base_model</strong> : str </br>
    &emsp; Name of the model selected based on the weighted sum of the two evaluation metrics.
    </br>
     <strong>all_rashomon_sets</strong> : list </br>
    &emsp; A dictionary where each key is a metric and each value is the corresponding Rashomon set for that metric.
    </br>
    <strong>rashomon_set</strong> : list </br>
    &emsp; Names of the models that are included in the Rashomon Set Intersection for given parameters. Obtained from get_rashomon_set() method. If the size of the set happens to contain less than 2 models, the constructor throws ValueError and asks to specify different parameters such as metrics and epsilon.
    </br>
    <strong>rashomon_predictions</strong> : dict </br>
    &emsp; A subset of predictions dict parameter containing only models that are included in the Rashomon Set Intersection.
    </br>
    <strong>rashomon_proba_predictions</strong> : dict </br>
    &emsp; A subset of proba_predictions dict parameter containing only models that are included in the Rashomon Set Intersection.
    </br>
    <strong>metrics</strong> : list </br>
    &emsp; List of evaluation metrics used to compute the intersection of two Rashomon Sets, each calculated based on one of the metrics.
    </br>
    <strong>weights</strong> : pd.Series </br>
    &emsp; Pandas Series with weights either computed by selected method or passed by user as init parameter.
    </br>
    <strong>leaderboard</strong> : pd.DataFrame </br>
     &emsp; User parameter value.
    </br>
    <strong>predictions</strong> : dict </br>
    &emsp;  User parameter value.
    </br>
    <strong>proba_predictions</strong> : dict </br>
    &emsp; User parameter value.
    </br>
    <strong>metrics</strong> : str </br>
    &emsp; User parameter value.
    </br>
    <strong>epsilon</strong> : float </br>
    &emsp; User parameter value.
    </br>
    <strong>custom_weights</strong> : list </br>
     &emsp; User parameter value
     <br> 
     <strong>weighted_sum_method</strong> : list </br>
     &emsp; User parameter value
     <br> 
    

</br>
</br>
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>get_rashomon_set_for_metric(<code>metric, epsilon</code>)</strong>
</div>
&emsp; Method for getting Rashomon set for a given metric. Parameter <code>metric</code> specifies metric for which Rashomon set is to be calculated. If the value of epsilon is not specified, uses <code>self.epsilon</code> value. Returns a list of models that are in the Rashomon set for the given metric.
</br>
</br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp; <code>metric</code>: str <br>
    &emsp; <code>epsilon</code>: float, default = None
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>rashomon_models_names</code> : list
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>find_rashomon_intersection(<code>epsilon</code>)</strong>
</div>
&emsp; Method for calculating the intersection of Rashomon sets by identifying models that are present in the Rashomon set for each metric and the given epsilon. If the value of epsilon is not specified, uses <code>self.epsilon</code> value. Returns a list of model names present in the Rashomon Intersection. If the intersection is empty, returns an empty list.
</br>
</br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp; <code>epsilon</code>: float, default = None <br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>rashomon_models_names</code> : list
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>get_rashomon_set(<code>epsilon</code>)</strong>
</div>
&emsp; Method that returns the names of models included in the Rashomon Intersection for a specified epsilon and two metrics. If the value of epsilon is not specified, uses <code>self.epsilon</code> value. This method overrides the implementation from the RashomonSet class to use intersection models instead of single-metric models.
</br>
</br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp; <code>epsilon</code>: float, default = None <br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>rashomon_intersection</code> : list
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>get_rashomon_predictions()</strong>
</div>
&emsp; Override method to use intersection models, not single metric models. Returns predictions and proba predictions for models present in Rashomon Intersection. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>rashomon_predictions</code> : dict
</br>
&emsp;  <code>rashomon_proba_predictions</code> : dict
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>get_rashomon_feature_importances()</strong>
</div>
&emsp; Override method to select feature importance information for only models present in the Rashomon Intersection.
</br>
</br>
&emsp;  <code>rashomon_importances</code> : dict
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>find_base_model(<code>weight1</code>, <code>weight2</code>)</strong>
</div>
&emsp; Method for finding base_model based on user passed weight values. Returns model name which maximizes value of <code>w1 * metrics[0] + w2 * metric[1]</code>. If many models have the same sum value, base model is the first one in the leaderboard.  This method overrides the implementation from the RashomonSet class to use intersection models instead of single-metric models.<br>
&emsp;&emsp;<em>Note: Weight parameters must sum to 1.</em>
</br>
</br>
&emsp; <strong>Parameters :</strong> </br>
&emsp; <code>weight1</code>: float
<br>
&emsp; <code>weight2</code>: float
<br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>best_model</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>find_worst_model()</strong>
</div>
&emsp; Method for finding the worst model based on user passed weight values. Returns model name which minimizes value of <code>w1 * metrics[0] + w2 * metric[1]</code>. If many models have the same sum value, the worst model is the first one in the leaderboard. This method overrides the implementation from the RashomonSet class to use intersection models instead of single-metric models. <br>
<br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>worst_model</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>find_same_score_as_base()</strong>
</div>
&emsp; Method used to find models in the Rashomon Intersection set that produce the same weighted sum of metrics values as base model. Returns number of models found with the same score as base model and list of their names. This method overrides the implementation from the RashomonSet class to use intersection models instead of single-metric models.
<br>
<br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>same_scores_count</code> : int
</br>
&emsp; <code>same_scores_models</code> : list
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>find_weights_entropy_based()</strong>
</div>
&emsp; Method for finding weights based on the entropy method. Returns weights as a pandas Series with index as metric names and values as weights. The weights should satisfy the constraint that they sum to 1. Entropy based weights are defined as:<br>

$$ 
{ w_i := \frac{1 - e(x_i)}{\sum_{i=1}^m(1-e(x_i))}}
$$

where

$$ 
{ e(x_i) := - \frac{\sum_{i=1}^mf_iln(f_i)}{ln(m)}}
$$

In the context of calculating the weights of two base_metrics, $f_i$ is the scaled metric value and m is the number of models in the Rashomon Intersection. Then entropy is calculated for both base_metrics as $e(x_i)$ where $x_1$ is th first metric and $x_2$ the second one.<br>
Read more about the entropy method : [Effectiveness of Entropy Weight Method in Decision-Making](https://onlinelibrary.wiley.com/doi/10.1155/2020/3564835) 
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>weights</code> : pd.Series
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>find_base_model_entropy_based()</strong>
</div>
&emsp; Method for finding base_model based on entropy method. Finds the base model by computing the weighted sum of the two metrics using entropy-based weights and selecting the model with the highest score. If many models have the same sum value, base model is the first one in the leaderboard.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>best_model</code> : str
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>find_weights_critic_method()</strong>
</div>
&emsp; Method for finding weights based on the CRITIC (Criteria Importance Through Intercriteria Correlation) method. Returns weights as a pandas Series with index as metric names and values as weights. The weights should satisfy the constraint that they sum to 1. CRITIC based weights are defined as:
<br>
</br>

$$ 
\displaystyle
{w_j = \frac{c_j}{\sum_{k=1}^{n} c_k}, \quad j = 1,\dots,n}
$$

where

$$ 
\displaystyle
{c_j = \sigma_j \sum_{k=1}^{n} (1 - \rho_{jk}), \quad j = 1,\dots,n}
$$
 
$\sigma_j$ denotes standard deviation of the normalized values of criterion $j$ across all alternatives and $\rho_{jk}$ is Pearson correlation coefficient between criteria $j$ and $k$. In case of finding weights based on two base metrics $n=2$.

Read more about the CRITIC method : [Selected Multi-Criteria Decision-Making Methods and Their Applications to Product and System Design](https://arxiv.org/pdf/2407.09931) 

&emsp;&emsp;<em>Note: This method involves computing the correlation matrix and standard deviations of the metrics. If CRITIC cannot be applied due to insufficient variation caused by identical metric values, or other numerical issues, it falls back to the entropy-based method.
</em>
&emsp; <strong>Returns :</strong> 
&emsp; <code>best_model</code> : str
</br>
    

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>find_base_model_critic_based()</strong>
</div>
&emsp; Method for finding base_model based on CRITIC method. Finds the base model by computing the weighted sum of the two metrics using CRITIC-based weights and selecting the model with the highest score. If many models have the same sum value, base model is the first one in the leaderboard.
</br>
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>best_model</code> : str
</br>
</br>
    

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>get_rashomon_metrics(<code>delta</code>)</strong>
</div>
&emsp; Method for getting all Rashomon Intersection metrics in a dictionary format.  Delta parameter is a threshold for probabilistic ambiguity and discrepancy. Returns all numeric metrics and information on Rashomon intersection (not including VPRs and Agreement Rates). This method overrides the implementation from the RashomonSet class to use intersection models instead of single-metric models.
</br>
<br>
&emsp; <strong>Parameters :</strong> </br>
&emsp; <code>delta</code>: float, default = 0.1
</br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>metrics</code> : dict
</br>
</br>

<div style="color: #60824f; font-size: 0.9rem;">
    <strong>summarize_rashomon(<code>delta</code>)</strong>
</div>
&emsp; Method for printing all calculated metrics for Rashomon Intersection in a structured format. This method overrides the implementation from the RashomonSet class to use intersection models instead of single-metric models.
<br>
<br>
&emsp; <strong>Parameters :</strong> </br>
&emsp; <code>delta</code>: float, default = 0.1
</br>



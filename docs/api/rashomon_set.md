[back](index.md)

# RashomonSet

<div style="background-color: #7ea1ee7a; padding: 10px; border-radius: 4px;">
class rashomon_analysis.<strong>RashomonSet</strong>(leaderboard, predictions, proba_predictions, feature_importances, base_metric, epsilon)
</div>
</br>
This class is the core class of the package. It creates the Rashomon Set for a given epsilon value and selected evaluation metric. 
</br>
</br>

<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Parameters</strong>
</div>
</br>
    <strong>leaderboard</strong> : pd.DataFrame </br>
     &emsp;  Leaderboard in a DataFrame format consisting of models and their evaluation metrics scores. (Returned by converters)
    </br>
    <strong>predictions</strong> : dict </br>
    &emsp;  Dictionary with model names as keys and class prediction vectors as values. (Returned by convertees)
    </br>
    <strong>proba_predictions</strong> : dict </br>
    &emsp; Dictionary with model names as keys and class probabilities prediction DataFrames as values. (Returned by converters)
    </br>
    <strong>base_metric</strong> : str </br>
    &emsp; Evaluation metric to be used as a primary value for sorting model performances. Allowed metrics are specified in the METRICS attribute. 
    </br>
    <strong>epsilon</strong> : float </br>
    &emsp; Epsilon parameter specifying the allowable deviation from the best evaluation metric, within which a model qualifies for inclusion in the Rashomon Set.
</br>
</br> 
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Note</strong>
</div>
<br>
Allowed values of the <code>base_metric</code> parameter are: <br>
<strong>Binary classification: </strong>
'accuracy', 'balanced_accuracy',  'roc_auc', 'average_precision', 'precision', 'precision_macro', 'precision_micro','precision_weighted', 'recall', 'recall_macro', 'recall_micro', 'recall_weighted', 'f1', 'f1_macro', 'f1_micro', 'f1_weighted'  <br>
<strong> Multiclass classification: </strong> 'accuracy', 'balanced_accuracy', 'precision_macro', 'precision_micro', 'precision_weighted','recall_macro', 'recall_micro', 'recall_weighted', 'f1_macro', 'f1_micro', 'f1_weighted', 'roc_auc_ovo', 'roc_auc_ovo_weighted','roc_auc_ovr', 'roc_auc_ovr_micro', 'roc_auc_ovr_weighted'<br>
<br>
The <code>epsilon</code> parameter value should be greater than 0, as it represents the absolute difference threshold.
<br>
<br>
<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Attributes</strong>
</div>
</br>
<strong>base_model</strong> : str </br>
    &emsp; Name of the model that achieved the highest score for the evaluation metric specified by base_metric parameter.
    </br>
    <strong>best_score</strong> : float </br>
    &emsp; The best value of the base_metric achieved by all models.
    </br>
    <strong>worst_score</strong> : dict </br>
    &emsp; The worst value of the base_metric achieved by all models.
    </br>
    <strong>rashomon_set</strong> : list </br>
    &emsp; Names of the models that are included in the Rashomon Set for given parameters. Obtained from get_rashomon_set() method. If the size of the set happens to contain less than 2 models, the constructor throws ValueError and asks to specify different parameters such as base_metric and epsilon.
    </br>
    <strong>rashomon_predictions</strong> : dict </br>
    &emsp; A subset of predictions dict parameter containing only models that are included in the Rashomon Set.
    </br>
    <strong>rashomon_proba_predictions</strong> : dict </br>
    &emsp; A subset of proba_predictions dict parameter containing only models that are included in the Rashomon Set.
    </br>
    <strong>number_of_classes</strong> : int </br>
    &emsp; Determining number of classes in the task based on the predictions vector. Obtained from determine_number_of_classes() method.
    </br>
    <strong>task_type</strong> : str </br>
    &emsp; Classification task type - 'binary' or 'multiclass' obtained from determine_task_type() method. 
    </br>
    <strong>METRICS</strong> : list </br>
    &emsp; All evaluation metrics that are allowed for analysis. 
    </br>
    <strong>METRICS_GREATER_IS_BETTER</strong> : dict </br>
    &emsp; A dictionary containing classification evaluation metrics names and the boolean value indicating whether this metric is interpreted as 'greater is better' (e.g accuracy) or not (e.g log loss).
    </br>
    <strong>leaderboard</strong> : pd.DataFrame </br>
     &emsp; leaderboard parameter value
    </br>
    <strong>predictions</strong> : dict </br>
    &emsp;  predictions parameter value
    </br>
    <strong>proba_predictions</strong> : dict </br>
    &emsp; proba_predictions parameter value
    </br>
    <strong>base_metric</strong> : str </br>
    &emsp; base_metric parameter value
    </br>
    <strong>epsilon</strong> : float </br>
    &emsp; epsilon parameter value 
</br>
</br>


<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>determine_task_type()</strong>
</div>
&emsp; Returns whether the task type for a given dataset is binary or multiclass classification based on prediction vectors. If another task type is determined, the method throws ValueError. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>task_type</code> : str
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>determine_number_of_classes()</strong>
</div>
&emsp; Method for determining number of classes in the task based on predictions vector.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>number_of_classes</code> : int
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>determine_number_of_samples()</strong>
</div>
&emsp; Method for determining number of samples in the task based on predictions vector.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>number_of_samples</code> : int
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>find_base_model()</strong>
</div>
&emsp; Returns the name of the model which achieved the best score for the evaluation metric specified by base_metric parameter. Uses the METRICS_GREATER_IS_BETTER to include the differences in metrics evaluation.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>base_model</code> : str
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>find_worst_model()</strong>
</div>
&emsp; Returns the name of the model which achieved the worst score for the evaluation metric specified by base_metric parameter. Uses the METRICS_GREATER_IS_BETTER to include the differences in metrics evaluation.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp;<code> worst_model</code> : str
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>find_same_score_as_base()</strong>
</div>
&emsp; Returns the number and names of models which achieved the same score for the evaluation metric specified by base_metric parameter as the base_model. Used especially when there are multiple models with the same scores.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>same_scores_count</code> : int
</br>
&emsp; <code>same_scores_models</code> : list
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>get_rashomon_set(<code>epsilon</code>)</strong>
</div>
&emsp; Returns the names of models that are included in the Rashomon Set for a specified epsilon and base_metric. Rashomon set is defined as: </br>

$$ 
S_\epsilon(h_0) := \lbrace h \in H : R(h_0) \le R(h) + \epsilon \rbrace
$$
where $h_0$ is the base_model, H is a set of all models in a hypothesis space and R is a selected risk function (base_metric). </br>
Read more about the Rashomon Set : [Predictive Multiplicity in Classification (Definition 1)](https://proceedings.mlr.press/v119/marx20a/marx20a.pdf)
</br>
</br>
&emsp; <strong>Parameters :</strong> </br>
&emsp; <code>epsilon</code>: float, default = None
</br>
&emsp;&emsp;<em> When a different epsilon value is not specified the method uses the epsilon parameter value.</em>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>rashomon_set</code> : list
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>get_rashomon_predictions()</strong>
</div>
&emsp; Returns the subsets of predictions and proba_predictions dictionaries containing only models that are included in the Rashomon Set.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>rashomon_predictions</code> : dict
</br>
&emsp;  <code>rashomon_proba_predictions</code> : dict
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>get_rashomon_feature_importances()</strong>
</div>
&emsp; Returns the subsets of the feature_importance_dict containing only models that are included in the Rashomon Set.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>rashomon_feature_importances</code> : dict
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>binary_ambiguity()</strong>
</div>
&emsp; Calculates binary ambiguity of a rashomon set by counting all observations where at least one model made a different class prediction than the base model. Those observations are considered ambiguous. Returns the fraction of ambiguous observations. Ambiguity is defined as:</br>

$$ 
\displaystyle
{ \alpha(h_0) := \frac{1}{n}\sum_{i=1}^n max_{h \in S_{\epsilon}} \mathbf{1}[h(x_i) \neq h_0(x_i)]}
$$
where $S_\epsilon$ is the Rashomon Set and $h(x_i)$ is the models predction for observation $x_i$.</br>
Read more about binary ambiguity : [Predictive Multiplicity in Classification (Definition 3)](https://proceedings.mlr.press/v119/marx20a/marx20a.pdf)
</br>
</br>
Note : Method available only for binary classification task type.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>binary_ambiguity</code> : float
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>multiclass_ambiguity()</strong>
</div>
&emsp; Calculates multiclass ambiguity of the Rashomon Set by counting all observations where at least one model made a different class prediction than the base model. Those observations are considered ambiguous. Returns the fraction of ambiguous observations. Multiclass ambiguity is defined as:</br>

$$ 
\displaystyle
{ \alpha(h_0) := \frac{1}{n}\sum_{i=1}^n max_{h \in S_{\epsilon}} \mathbf{1}[argmax(h(x_i)) \neq argmax(h_0(x_i))]}
$$
where $S_\epsilon$ is the Rashomon Set and $h(x_i)$ is the class probabilities prediction vector for observation $x_i$, then the $argmax(h(x_i))$ is the predicted class. </br>
Read more about muliclass ambiguity : [Rashomon Capacity: A Metric for
Predictive Multiplicity in Classification (Equation 2)](https://arxiv.org/pdf/2206.01295)
<br>
<br>
Note: Method available only for multiclass classification task type.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>multiclass_ambiguity</code> : float
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>probabilistic_ambiguity(<code>delta</code>)</strong>
</div>
&emsp; Calculates probabilistic ambiguity of the Rashomon Set by counting all observations where at least one model made a different risk prediction than the base model. Risk predictions need to have a difference greater than delta to be considered conflicting. Returns the fraction of ambiguous observations. The definition of probabilistic ambiguity is as follows:</br>

$$ 
\displaystyle
{ \alpha(h_0, \delta) := \frac{1}{n}\sum_{i=1}^n \mathbf{1}[max_{h \in S_{\epsilon}} |g(x_i) - g_0(x_i)| \ge \delta ]}
$$
where $S_\epsilon$ is the Rashomon Set and $g(x_i)$ is the risk probability prediction $P(y_i=1|x_i)$ for observation $x_i$. </br>
Read more about probabilistic ambiguity : [Predictive Multiplicity in Probabilistic Classification (Definition 3)](https://arxiv.org/pdf/2206.01131)
<br>
<br>
Note : Method available only for binary classification task type.
</br>
</br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp;<code>delta</code> : float
</br>
&emsp;&emsp;<em>delta parameter indicates the minimum difference between two risk probabilities for the predictions to be considered conflicting.</em>
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>probabilistic_ambiguity</code> : float
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>binary_discrepancy()</strong>
</div>
&emsp; Calculates discrepancy for binary classification task by counting how many predictions differ between base and reference model. Then choses the max sum of different predictions across all models from the Rashomon Set. Discrepancy is defined as:

$$ 
\displaystyle
{ \delta(h_0) := max_{h \in S_{\epsilon}} \frac{1}{n}\sum_{i=1}^n  \mathbf{1}[h(x_i) \neq h_0(x_i)]}
$$
where $S_\epsilon$ is the Rashomon Set and $h(x_i)$ is the models predction for observation $x_i$.</br>
Read more about binary discrepancy : [Predictive Multiplicity in Classification (Definition 4)](https://proceedings.mlr.press/v119/marx20a/marx20a.pdf)
</br>
</br>
Note: Method available only for binary classification task type.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>binary_discrepancy</code> : float
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>multiclass_discrepancy()</strong>
</div>
&emsp; Calculates discrepancy for multiclass classification tasks by counting how many predictions differ between base and reference model. Then chooses the max sum of different predictions across all models from the Rashomon Set. Multiclass disrepancy is defined as:<br>

$$ 
\displaystyle
{ \delta(h_0) := max_{h \in S_{\epsilon}} \frac{1}{n}\sum_{i=1}^n  \mathbf{1}[argmax(h(x_i)) \neq argmax(h_0(x_i))]}
$$
where $S_\epsilon$ is the Rashomon Set and $h(x_i)$ is the class probabilities prediction vector for observation $x_i$, then the $argmax(h(x_i))$ is the predicted class. </br>
Read more about muliclass discrepancy : [Rashomon Capacity: A Metric for
Predictive Multiplicity in Classification (Equation 2)](https://arxiv.org/pdf/2206.01295)
<br>
<br>
Note : Method available only for multiclass classification task type.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>multiclass_discrepancy</code> : float
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>probabilistic_discrepancy(<code>delta</code>)</strong>
</div>
&emsp; Calculates discrepancy for binary target task by counting how many risk predictions differ between base and reference model. For predictions to be considered conflicting their difference must be greater than delta. Then choses the max sum of different predictions across all models from the Rashomon Set. Probabilistic discrepancy is defined as follows:</br>

$$ 
\displaystyle
{ \delta_\epsilon(h_0, \delta) := max_{h \in S_{\epsilon}}\frac{1}{n}\sum_{i=1}^n \mathbf{1}[ |g(x_i) - g_0(x_i)| \ge \delta ]}
$$
where $S_\epsilon$ is the Rashomon Set and $g(x_i)$ is the risk probability prediction $P(y_i=1|x_i)$ for observation $x_i$. </br>
Read more about probabilistic discrepancy : [Predictive Multiplicity in Probabilistic Classification (Definition 4)](https://arxiv.org/pdf/2206.01131)
<br>
<br>
Note : Method available only for binary classification task type.
</br>
</br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp; <code>delta</code> : float
    </br>
&emsp;&emsp;<em>delta parameter indicates the minimum difference between two risk probabilities for the predictions to be considered conflicting.</em>
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>probabilistic_discrepancy</code> : float
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>viable_prediction_range()</strong>
</div>
&emsp; Calculates the viable prediction range for each observation in the test dataset as the min and max risk probability predicted across all models in the Rashomon Set. Wide prediction range suggests high uncertainty about the observations prediction. VPR for the given observation is defined as: </br>

$$
\displaystyle
{ V_\epsilon(x_i) := [min_{g \in S_\epsilon} g(x_i), max_{g \in S_\epsilon} g(x_i)] }
$$
where $S_\epsilon$ is the Rashomon Set and $g(x_i)$ is the risk probability prediction $P(y_i=1|x_i)$ for observation $x_i$. </br>
Read more about Viable Prediction Range : [Predictive Multiplicity in Probabilistic Classification (Definition 2)](https://arxiv.org/pdf/2206.01131)
<br>
<br>
Note : Method available only for binary classification task type.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>vprs</code> : list[tuple[float, float]]
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>agreement_rate()</strong>
</div>
&emsp; For each observation, calculates the percentage of models, which made the same class prediction as the base model. If all models from the Rashomon Set predicted the same class as the base model, the agreement rate for the observation equals 1. 
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>agreement_rates</code> : list[float]
</br>
</br>
<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>percent_agreement()</strong>
</div>
&emsp; Calculates the proportion of observations for which each model from the Rashomon Set predicted the same class as the base model. Returns a dictionary mapping model names to their corresponding agreement percentages with the base model. If a given model made the same predictions for all observations as the base model, its percent agreement equals 100%.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>percent_agreements</code> : dict[str, float]
</br>
</br>


<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>rashomon_ratio()</strong>
</div>
&emsp; Calculates Rashomon Ratio which is the ratio of the Rashomon Set size to the total number of models present in the leaderboard. 
</br>

$$
\displaystyle
\hat{R}(H, \epsilon) := \frac{\text{vol}(S_{\epsilon}(h_0))}{\text{vol}(H)}
$$

where $\text{vol}(S_{\epsilon}(h_0))$ denotes the "volume" of the Rashomon Set — in our empirical setting this corresponds to the number of models in the Rashomon Set. Similarly, $\text{vol}(H)$ represents volume of hypothesis space, in this case number of models generated by AutoML framework.


Read more about the Rashomon Ratio in: [A Study in Rashomon Curves and Volumes: A New Perspective on Generalization and Model Simplicity in Machine Learning (Definition 2)](https://arxiv.org/pdf/1908.01755v2)
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>rashomon_ratio</code> : float
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>get_patterns_rashomon_set()</strong>
</div>
&emsp; Method to retrieve all unique prediction patterns from the Rashomon Set, representing the collection of predictions produced by each model in the set. Returns a set of patterns in the Rashomon Set.
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>patterns</code> : set
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>get_patterns_hypothesis_set()</strong>
</div>
&emsp; Method to retrieve all unique prediction patterns from models present in the hypothesis space (leaderboard).
</br>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>patterns</code> : set
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>pattern_rashomon_ratio()</strong>
</div>
&emsp; Method for calculating Pattern Rashomon Ratio, defined as ratio of the number of unique prediction patterns in the Rashomon Set to the total number of unique predictions patterns in the hypothesis space (leaderboard).
</br>

$$
\hat{R}_{\mathrm{pattern}}(H, \epsilon) := 
\frac{\lvert \lbrace h(X) : h \in S_\epsilon \rbrace \rvert}
     {\lvert \lbrace h(X) : h \in H \rbrace \rvert}
$$

where $X$ denotes the dataset all the models were trained on, and $h(X)$ denotes all predictions made by model $h$ across all samples in the dataset. 

$H$ is the hypothesis space (in this case all models present in the leaderboard), and $S_\epsilon$ is the Rashomon Set.

Read more about the Pattern Rashomon Ratio in: [A Study in Rashomon Curves and Volumes: A New Perspective on Generalization and Model Simplicity in Machine Learning (Definition 3)](https://arxiv.org/pdf/1908.01755v2)

 </br>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>pattern_rashomon_ratio</code>: float
</br>
<br>


<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>rashomon_capacity( <code>sample_index</code> )</strong>
</div>
&emsp; Method for calculating Rashomon Capacity for a given sample. The parameter <code>sample_index</code> should be an index of a sample the Rashomon Capacity is to be calculated. The output value is a float in the range [1, c], where c is the number of classes in the classification task. </br>
&emsp; If Rashomon Capacity equals 1, then all the models produced the same outputs for given sample, so there is no predictive multiplicity. <br>
&emsp; If Rashomon Capacity equals c, that indicates that the models produce maximally diverse predictions for the given sample, resulting in highest predictive multiplicity. 
<br>
&emsp; Read more about Rashomon Capacity: <a href="https://arxiv.org/pdf/2206.01295" target="_blank">Rashomon Capacity: A Metric for Predictive Multiplicity in Classification (Definition 2)</a>.
<br>
<br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp; <code>sample_index</code> : int
    <br>
    <br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>rashomon_capacity</code> : float
</br>
<br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>generate_transition_matrix( <code>sample_index</code> )</strong>
</div>
&emsp; Method for generating transition matrix for a given sample. Transition matrix (m, c) is a matrix, where m corresponds to the number of models included in the set, while c denotes the number of classes associated with the prediction task. This matrix is used by the Blahut–Arimoto algorithm to compute the channel capacity.
</br>
</br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp; <code>sample_index</code> : int
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>transition_matrix</code> : np.ndarray
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>blahut_arimoto_algorithm( <code>transition_matrix</code>,  <code>max_iterations</code>, <code>tolerance</code>)</strong>
</div>
&emsp; Method for computing the <em>channel capacity</em> for a given sample. 
Channel capacity is defined as the maximum mutual information between the channel input <i>X</i> (here representing the models in the Rashomon set) and the channel output <i>Y</i> (the corresponding probabilistic predictions), maximized over all possible input distributions <i>p(x)</i>. <br>
&emsp; Intuitively, this algorithm finds the probability distribution over models (inputs) that maximizes how informative their predictions (outputs) are.
<br>
&emsp; For more details and inspiration, see the <a href="https://github.com/HsiangHsu/rashomon-capacity" target="_blank">Rashomon Capacity GitHub repository</a>.
</br>
<br>
&emsp; <strong>Parameters :</strong>
&emsp;<ul>
    <li><code>transition_matrix</code> : np.array, matrix with m rows (models from the Rashomon Set) and c columns (number of classes for specified task). The columns of the transition matrix represent the class probability distributions predicted by each model for every class for specific sample.</li>
    <li><code>max_iterations</code> : int, maximum number of algorithm iterations, default = 1000</li>
    <li><code>tolerance</code> : float, error tolerance for algorithm to stop iterations, default = 1e-8</li>
</ul>
&emsp; <strong>Returns :</strong> </br>
&emsp; <code>channel_capacity</code> : float
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>cohens_kappa()</strong>
</div>
&emsp; Method for calculating Cohen's Kappa metric for every model in the Rashomon Set relative to the base model.
Cohen's Kappa measures agreement between two models predictions adjusted for agreement expected to occur by chance. 
<br>
Values range from -1 to 1, where 1 indicates perfect agreement in models predictions, 0 means agreement that would be expected by chance and -1 denotes no agreement where models make opposite predictions.

The formula for calculating Cohen's Kappa is defined as follows:
$$
\displaystyle
\kappa = \frac{p_o - p_e}{1 - p_e}
$$
where $p_o$ denotes observed agreement between two models (proportion of matching predictions generated by both models, see percent agreement metric) and $p_e$ is the expected agreement by chance, calculated from the marginal proportions of predictions for each class by the models.
<br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>cohens_kappa_dict</code> : dict
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>cohens_kappa_matrix()</strong>
</div>
&emsp; Method for calculating the Cohen's Kappa metric for every pair of models in the Rashomon Set. It returns a symmetric matrix where the entry at [i, j] represents the Cohen's Kappa score between model i and model j. 
Diagonal entries are 1.0, representing a model compared with itself.
<br>
<br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>kappa_matrix</code> : pd.DataFrame
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>get_rashomon_metrics( <code>delta</code> )</strong>
</div>
&emsp; Method for returning all Rashomon Set related metrics and attributes in a dictionary format. The retuned properties are: base model, rashomon set size, task type, number of classes, rashomon ratio, pattern rashomon ratio, ambiguity, discrepancy, probabilistic ambiguity, probabilistic discrepancy, VPRs, agreement rates, percent agreements, mean rashomon capacity, min rashomon capacity, max rashomon capacity, std rashomon capacity. 
</br>
</br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp; <code>delta</code> : float, default = 0.1 <br>
    &emsp; &emsp; <em>delta parameter used in probabilitisc_ambiguity() and probabilitic_discrepancy() methods for binary task type</em>
</br>
    &emsp; <strong>Returns :</strong> </br>
    &emsp; <code>metrics</code> : dict
</br>
</br>

<div style="color: #3F51B5; font-size: 0.9rem;">
    <strong>summarize_rashomon( <code>delta</code> )</strong>
</div>
&emsp; Method for printing key Rashomon Set related metrics and attributes on the console. The printed properties are: base metric, base model, models with the same score as base, best and worst score across all rashomon set models, rashomon set size, task type, number of classes, rashomon ratio, pattern rashomon ratio, ambiguity, discrepancy, probabilistic ambiguity, probabilistic discrepancy, min agreement rate, max agreement rate, std agreement rage, percent agreements, mean rashomon capacity, min rashomon capacity, max rashomon capacity, std rashomon capacity. 
</br>
</br>
    &emsp; <strong>Parameters :</strong> </br>
    &emsp; <code>delta</code> : float, default = 0.1 <br>
    &emsp; &emsp; <em>delta parameter used in probabilitisc_ambiguity() and probabilitic_discrepancy() methods for binary task type</em>
</br>
</br>
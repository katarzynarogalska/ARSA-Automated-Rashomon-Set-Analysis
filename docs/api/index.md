[home](../index.md)

# ARSA documentation 
In this section you may find a detailed description of the package modules and features. 

1. <strong>[Converter](abstract_converter.md)</strong> </br>
    Converter is an abstract class defining methods that should be implemented in all subclasses. All of the converters are responsible for converting raw models input into files,which can be further processed to create the <code>RashomonSet</code> and <code>RashomonIntersection</code> objects. Those classes implement methods for extracting the leaderboard, predictions, probability predictions and feature importances from trained models provided by the user.<br>
 
    1.1 [PredictorConverter](autogluon_converter.md)</br>
    1.2 [H2OConverter](h2o_converter.md) <br>
2. <strong>[Rashomon Set](rashomon_set.md)</strong> <br>
    RashomonSet class is a primary class of the package, implementing all metrics used to describe and analyze the Rashomon Set. <br>
3. <strong>[Rashomon Intersection](rashomon_itersection.md)</strong> <br>
    RashomonIntersection class is a subclass of the Rashomon Set allowing the specification of two base metrics instead of just one. This class proposes a new way of creating and analysing the Rashomon Sets. <br>
4. <strong>Visualizers</strong><br>
    The main purpose of the Visualizers is to create the plots and descriptions of key Rashomon Set elements. Those visualizations are further displayed on the dashboard created as a result of the chosen pipeline. <br> 
    4.1 [Visualizer](visualizer.md)<br>
    4.2 [IntersectionVisualizer](intersection_visualizer.md)<br>

5. <strong> [Builder](pipeline_abstract.md)</strong> <br>
    Builder is an abstract class defining methods that should be implemented in all subclasses. All those objects are used to create and launch pipelines accepting different forms of user input and resulting in the creation of the desired objects and launching the dashboard for further analysis.<br> 
    5.1 [BuildRashomonAutogluon](pipeline_user_input_rashomon_autogluon.md) <br>
    5.2 [BuildRashomonH2O](pipeline_user_input_rashomon_H2O.md) <br>
    5.3 [BuildRashomonIntersectionH2O](pipeline_user_input_intersection_H2O.md)<br>
    5.4 [BuildRashomonIntersectionAutogluon](pipelines_user_input_intersection_autogluon.md)<br>
    5.5 [BuildRashomonFromConverted](pipeline_converter_rashomon.md)<br>
    5.6 [BuildIntersectionFromConverted](pipeline_converter_intersection.md)<br>

<strong>Note:</strong> User guide notebooks for Pipelines creation may be found in a github repository of the package. 
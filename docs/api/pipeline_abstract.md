[back](index.md)

# Builder - abstract class

<div style="background-color: #c2deb1; padding: 10px; border-radius: 4px;">
class rashomon_analysis.pipelines.<strong>Builder</strong>
</div>
<br>
This class is an abstract class asserting all pipeline classes have the same set of obligatory methods.

<br>
<br>


<div style="background-color: lightgray; padding: 3px; border-radius: 0px;">
<strong>Methods</strong>
</div>
</br>
<strong>Note:</strong> 
All methods are decorated as <code>@abstractmethod</code> and must be implemented in every child class.
<br>
<br>
<div style="color: #60824f; font-size: 18px;">
    <strong>preview_rashomon()</strong>
</div>
&emsp; Method for presenting all trained models and their scores (leaderboard) and the Rashomon Set size plot to help the user choose the right epsilon parameter value. 
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>set_epsilon()</strong>
</div>
&emsp; Method for setting the value of <code>epsilon</code> parameter. Has to be completed before the <code>build()</code> method. 
</br>
</br>
<div style="color: #60824f; font-size: 18px;">
    <strong>build()</strong>
</div>
&emsp; Primary method of all pipelines. Creates all the necessary objects from given arguments, returns them and launches the Streamlit dashboard in the background if launch_dashboard parametr is set to True.
</br>
</br>

<div style="color: #60824f; font-size: 18px;">
    <strong>dashboard_close()</strong>
</div>
&emsp; Method used to close the Streamlit dashboard launched in the <code>build()</code> method. Kills all the Streamlit processes to avoid zombie process running in the background.
</br>
</br>

    
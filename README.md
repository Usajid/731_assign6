
D(St)reams of Anomalies (Assignment # 06- EECS 731)
==============================


### Quick Note:
If you are interested in only looking at notebook, please access the notebook in **/notebooks/anomalyDetection.ipynb**.

/notebooks: Contains the notebook of this assignment.

/data: Contains the data csv file (machine_temperature_system_failure.csv)

### Objective:

<ul>
<li>Pick one dataset from given Anomaly Detection Benchmarks</li>
<li>Do feature engineering as a pre-process for Anomaly Detection</li>
<li>Do Anomaly Detection based modeling to detect anomalies in the given dataset</li>
</ul>

### Dataset:

I used the **Machine Temperature System Failure** dataset (https://github.com/numenta/NAB/tree/master/data) for this Anomaly Detection modeling assignment. (Data csv file is in /data/machine_temperature_system_failure.csv).

### Process:

<ul>
<li>First I did feature engineering. Please refer to notebook for more details.</li>
<li>Then, I did change in value over time graphical anlysis on the given dataset.</li>
<li>Finally, we trained and evaluated two anomaly detection based models separately on the given dataset to detect anomalies.</li>
</ul>

### Discussion and Results:
According to the given dataset we are using, there are **three anomalies** in it. We have to detect these anomalies using some Machine Learning Algorithm suitable for this problem. First we analyze the dataset and anomalies by making a time plot as follows:

![Given Dataset Over Time Graph](figs/fig1u.png)


As shown above, we can see three anomalies. The left-most anomaly is easy to detect, but next two anomalies are much closer to the normal data points. So, this makes it a challenging task for us. Next, to analyze the change in value over time for differetn data points, we plot the value change per datapoint over time as follows:

![Change in Value Over Time Graph](figs/fig2au.png)

As shown in the above graph, we can now clearly see that three anomalies have the highest peaks or changes as compared to other data points. It makes it more clearer to us. Now we can focus on these anomalous data points and model algortihms for their detection. We use this information in our modeling process as detailed in the notebook. Before starting the modeling process, we also analyze the Exponentially Weighted Moving Averages (EMWA) that are helpful in smoothing the graph as follows. But we skip them being not much useful.


![Given Dataset Over Time Graph](figs/fig2u.png)


For modeling the Anomaly Detection problem, we trained and evalauted following two algorithms:


<ul>
<li>One Class SVM</li>
<li>Isolation Forest Model</li>
</ul>


![Once Class SVM based Anomaly Detection Graph](figs/fig3u.png)




![Isolation Forest based Anomaly Detection Graph](figs/fig4u.png)



<ul>
<li>Random Forest Regressor</li>
<li>XGBoost Regressor</li>
<li>Linear Regessor</li>
</ul>

Once above regressors were trained, we evaluted them separately on three evaluation metrics,as follows:

<ul>
<li>Mean Absolute Error (MAE)</li>
<li>Mean Squared Error (very good in telling about the variance in result values, so more desirable metric)</li>
<li>Scikit-learn Regression Score (Maximum value = 1.0) </li>
</ul>

The evaluation results for three regressors are as follows:

**Random Forest Regressor:**

MAE: **4.54832675696375**

MSE: **36.48255827784976**

Multi Target Output Random Forest Based Regressor Score: **0.701**

**XGBoost Regressor:**

MAE: 6.956283390349816

MSE: 77.05458382962796

Multi Target Output XGBoost based Regressor Score: 0.37

**Linear Regressor:**

MAE: 7.233133556966823

MSE: 82.39727180323428

Multi Target Output Linear Regressor Score: 0.326

### Conclusion

Anomaly detection is a unique problem, as normal classification or regression based approaches are not applicable directly on this type of problem, because of the imbalanced nature of the data. In this assignment, we analyzed two anomaly detection algorithms, namely **One Class SVM** and **Isolation Forest Algorithm**. One class SVM was proved to be much faster and efficent, but Isolation Forest based model gave much effective results but slower in processing. So, we can use either of them based on the requirement (e.g Real Time processing reuiqred or not etc.). Please see /notebooks/anomalyDetection.ipynb for more details.







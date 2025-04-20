# SC1015-Lab-REP2-Team4
SC1015 Lab REP2 Team 4's Mini-Project Submission 
Joanna Wu Haoyue (U2322092E), Sricharan Balasubramanian (U2322339L), Travis Tan Hai Shuo (U2322928D)

# Dataset and Problem Definition
The dataset we chose from Kaggle was "US Accidents (2016 - 2023)" by Sobhan Moosavi. The accident data were collected from February 2016 to March 2023, using multiple APIs that provide streaming traffic incident (or event) data. The dataset currently contains approximately 7.7 million accident records. 

In light of our upcoming exchange at UC Berkeley, the 3 of us are excited to go on many roadtrips to explore California. However, we are concerned about road safety and want to know when driving there is most accident-prone and how weather conditions correlate to accidents, so we can be more cautious during those times. Hence, we scoped this dataset down to accidents that happened in California (1.7 million data points). Coincidentally, we realised California had the highest recorded number of road accidents, inspiring a greater use case. With this project's insights, emergency services like firefighters and hospitals can have an early warning system to help them allocate rescue resources optimally, reducing the fatality of road accidents. These insights can be integrated into GPS systems to alert drivers when they are driving in accident-prone conditions, minimising road accidents.

# Data Preparation and Cleaning
To clean the dataset, we first removed columns we deemed irrelevant to our problem statement with valid justifications. Then, we converted the dataset's features into appropriate data types so they are easier to handle. The NULL values were handled next, and with the dropping of certain tuples, our dataset has been reduced to 1.5 million entries. Next, the dataset was normalised and outliers were handled. Lastly, some data points for weather attributes were merged to improve interpretability. 

# Exploratory Data Analysis/Visualisation
We have a few hypotheses that we wish to validate and subsequently feed into our ML algorithms for predictions:

- Which regions in California have the most accidents, and which
- What trends can we identify in the frequency of accidents against the time of the day, and the day of the week?
- Do accidents occur in all weather conditions or only in certain weather conditions?

We start with a plot of the entire California map with the accidents displayed. From this plot, it is clear to us that the accidents are not homogeneously distributed in California. Moreover, we see accidents along lines through the state. We confirm this with further visualisations. The city distribution shows a clear imbalance in distributions. The split by street is a bit more homogeneous, but also shows high cardinality. We then analyse the time distribution, identifying trends in peak hours and weekday-weekend splits. We cross validate the region and time trends with heatmaps and note that these trends stand valid across all streets and cities. For weather, a correlation analysis of the various weather factors showed no strong correlation, preventing us from reducing features. Moreover, we noted a trend of unclear weather contributing heavily to the occurrence of accidents, making weather a key factor that we subsequently model. To conclude our EDA, our three dimensions of region, time+day and weather are all validated. We narrow down specifically to investigate cities and streets for region, peak hour trends and weekday-weekend splits for time+day, and indicators of adverse weather.  

# Machine Learning Techniques
We decided to focus on time series forecasting to predict the rate of accidents in the next hour, given the limitations of our dataset for binary classification and severity prediction. The dataset is positive-only, which makes it unsuitable for binary classification, and severity prediction suffers from extreme class imbalance.

For feature engineering, we created a target variable (Accident_Next_Hour) to predict accident rates in the next hour and added a time lag feature (Accident_Prev_Hour). We also converted Start_Hour to cyclic features using Hour_Cos and Hour_Sin. We applied target encoding to the ‘City’ variable and ordinal encoding to the ‘Day_of_Week’ variable.

In the data transformation phase, we tuned hyperparameters for RandomForestRegressor, GradientBoostingRegressor, and LinearRegression using RandomisedSearchCV. We compared model results using metrics like MSE, MAE, and R². After switching to a classification approach, we binned accident rates into four categories: none (0), low (≤2), medium (≤5), and high (>5).

To address class imbalance, we applied Synthetic Minority Oversampling Technique (SMOTE). We then trained and tested classification models, including RandomForestClassifier, GradientBoostingClassifier, LogisticRegression, XGBoostClassifier, and HistGradientBoostingClassifier, comparing results using F1 score, precision, recall, and accuracy.

# Data-Driven Insights and Recommendations

# Beyond the Course
We applied several advanced techniques beyond the typical syllabus to enhance model performance. To address class imbalance, we used the Synthetic Minority Oversampling Technique (SMOTE), which oversamples underrepresented data points to produce more accurate results. For high cardinality categorical data, we implemented target encoding, which accounts for the relationship between categories and the target variable, avoiding the unintended patterns introduced by methods like label encoding.

We also performed a hyperparameter grid search to fine-tune model parameters, such as tree depth and the number of estimators for RandomForest, ensuring we achieved the best results. To improve our time series forecasting, we introduced time lag data, providing additional context and making the model more predictive. Lastly, we considered the cyclic nature of hours by converting them into hours_sin and hours_cos, allowing us to represent time more effectively than using simple numerical values.

# Individual Contribution
Joanna Wu: Intro + Problem definition + Data preparation and cleaning
Sricharan Bala: Exploratory Data Analysis + Visualisation + ML 
Travis Tan: ML models + Out of syllabus + Limitations 

# Resources
Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, and Rajiv Ramnath. “A Countrywide Traffic Accident Dataset.”, 2019.

Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, Radu Teodorescu, and Rajiv Ramnath. "Accident Risk Prediction based on Heterogeneous Sparse Data: New Dataset and Insights." In proceedings of the 27th ACM SIGSPATIAL International Conference on Advances in Geographic Information Systems, ACM, 2019.


# SC1015-Lab-REP2-Team4
SC1015 Lab REP2 Team 4's Mini-Project Submission 
Joanna Wu Haoyue (U2322092E), Sricharan Balasubramanian (U2322339L), Travis Tan Hai Shuo (U2322928D)

# Dataset and Problem Definition
The dataset we chose from Kaggle was "US Accidents (2016 - 2023)" by Sobhan Moosavi. The accident data were collected from February 2016 to March 2023, using multiple APIs that provide streaming traffic incident (or event) data. The dataset currently contains approximately 7.7 million accident records. 

In light of our upcoming exchange at UC Berkeley, the 3 of us are excited to go on many roadtrips to explore the beautiful state of California. However, we are concerned about road safety and want to know when driving on the streets is most accident-prone and how weather conditions correlate to accidents, so we can be more cautious during those times. Hence, we scoped this dataset down to accidents that happened in the state of California (1.7 million data points). Coincidentally, we realised California had the highest recorded number of road accidents, inspiring a greater use case. With this project's insights, emergency services like firefighters and hospitals can have an early warning system to help them allocate rescue resources optimally, reducing the fatality of road accidents. These insights can be integrated into GPS systems to alert drivers when they are driving on certain streets during accident-prone times or weather conditions, minimising road accidents.

# Data Preparation and Cleaning
To clean the dataset, we first removed columns we deemed irrelevant to our problem statement with valid justifications. Then, we converted the dataset's features into appropriate data types so they are easier to handle. The NULL values were handled next, and with the dropping of certain tuples, our dataset has been reduced to 1.5 million entries. Next, the dataset was normalised and outliers were handled. Lastly, some data points for weather attributes were merged to improve interpretability. 

# Exploratory Data Analysis/Visualisation

# Machine Learning Techniques

# Data-Driven Insights and Recommendations

# Extra Effort

# Resources
Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, and Rajiv Ramnath. “A Countrywide Traffic Accident Dataset.”, 2019.

Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, Radu Teodorescu, and Rajiv Ramnath. "Accident Risk Prediction based on Heterogeneous Sparse Data: New Dataset and Insights." In proceedings of the 27th ACM SIGSPATIAL International Conference on Advances in Geographic Information Systems, ACM, 2019.


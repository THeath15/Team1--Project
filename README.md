# Group 1 – KU Data Analytics Online Bootcamp
Project Name: Second Segment
Member: John Johnson, Michele Samspon, Stephen Long, Theresa Heath 

# Communication Protocols:
Project MMeeting Calendar: Team members can sign in/out anytime on below Zoom meeting time schedules. 
Monday to Friday : 7pm to 10pm 
Saturday to Sunday: 1pm to 4pm

# Selected Topic: 
Market volatility during international conflict 

# Reason topic was selected:
With the current situation of Russia’s military invading Ukraine, our team has agreed to tackle an exploratory analysis  on investor takes to war and uncertainty during international conflicts.

# Description of source of Data / Other Resources and Links:

	The Mapping can be found here:  
	https://ucdp.uu.se/downloads/index.html#armedconflict-dataset-version-21.1.csv &
	https://ucdp.uu.se/downloads/ucdpprio/ucdp-prio-acd-211.pdf
	Stock Market Dataset:  https://www.kaggle.com/rishidamarla/stock-prices-over-a-30-year-period 
	
# Questions we hope to answer with the data (reflecting on dataset)

a.	Does the number of the conflict have proportional impact?

b.	Does the geographical location matter to the number of conflict? 

c.	Does the market bounce back after 90 days from the start of the conflict?

d.	Which territory / region or location was greatly affected by the conflicts?

e.	Describe the 9/11 market before, during and after the conflict?

# Description of data exploration  and  analysis phase of the project
Data search  using Google and  Kaggle website (see above resources used for this project). Dataset Stock Market Dataset and the datawar set from url above were downloaded and saved as:
	 - Dowjones.csv
	 - Nasdaq. csv
	 - SP500.csv  
 	 - War_dataset.csv

Using Jupyter Notebooks the dataset were uploaded to Amazon Web Services. We use Python for cleaning up war dataset file was initiated and joining and cleaning up database for the 3 stock market file for Dowjones, Nasdaq and SP500. 

# Image Files and Dashboard :
https://public.tableau.com/app/profile/michele.sampson/viz/MarketTrendbyRegion/Dashboard1?publish=yes
https://github.com/THeath15/Team1--Project/blob/main/Group1%20presentation%20revised%203.pptx
			      

# Technologies, languages, tools, and algorithms used throughout the project :
	- Excel
	- Python
	- Machine learning
	- QuickDBD
	- GoogleSlide /Powerpoint 
	- Tableau
	- QuickDBD 
	- AWS 
	
	![alt text](https://github.com/THeath15/Team1--Project/blob/8adc3fabdc14929a6bd3b56218bf5bedf785e964/Images/ERD%20Diagram.PNG?raw=true)

# Machine Learning Model:

- Description of preliminary data preprocessing:
	- The conflict data is preprocessed and uploaded to the AWS database via the Jupyter notebook: ***conflict_cleaning.ipynb***.
	The different stock data sets are preprocessed and uploaded to the AWS database via the Jupyter notebook: ***stock_cleaning.ipynb***.
	
-  Description of preliminary feature engineering and preliminary feature selection, including the decision-making process:
	- The feature engineering and preliminary feature selection was performed in the ***ml_dev.ipynb*** Jupyter notebook.
	The first restriction in the data was selecting only the conflict data where we had stock data available.
	- Next, a function called ```find_nearest_date()``` was created to find the nearest stock date given the conflict date, this would be used to merge the stock data to the conflict data in a new dataframe.
	A binning function, ```create_bins()``` was created to allow the easy generalization of binning as there are potentially hundreds of different countries/governments, so this would help to prevent the blowing up of the number of features, given the relatively small number of conflicts.
	- Binning was performed on all the object dtype columns using the aforementioned ```create_bins()``` function.
	The actual encoding was performed using ```Pandas.get_dummies()``` method.
	- A simple Pandas merge is then used to combine the conflict and stock data, where stock data that is missing any values are dropped, and then NaNs are filled with 0s.
	
-  Description of how data was split into training and testing sets:
	- The data was split with 80% going to training and the other 20% going to test set.
	- The random_state seed was set to 42 to produce reliable results for sharing amongst the group.
	- Stratification of the split wasn't necessary because this was a regression problem, rather than a classification problem.
	
-  Explanation of model choice, including limitations and benefits:
	- The Extra Random Trees Regressor Ensemble model was selected for machine learning.
	- The primary limitations for this type of model can be extended training time if there is a significant amount of data, and the decision tree model itself could change drastically with the introduction of new data, rather than adjusting the weights on a previously trained model if this had been a deep learning algorithm.
	- However, for this particular data set there are not too many data points, hence the training time is relatively fast.
	Conflicts around the world don't arise too frequently as measured by the Uppsala Conflict Data Program (UCDP), as they are defined to occur with 25 or more battle-related deaths in a calendar year.
	- The major benefits of this model include: being able to see the feature_importances after the training to see which of the features are most relevant in making stock predictions, being able to easily parallelize the training of the model as this is an ensemble method, and being able to easily explain/understand the model after the training.

- Explanation of changes in model choice (if changes occurred between the Segment 2 and Segment 3 deliverables):
	- No changes to the presently used ML model were made. 
	- A cursory code was made for a deep neural network model for comparison's sake and the predicted values for the period of September 11th 2001 were nowhere close to the actual market behavior.

- Description of how they have trained the model thus far, and any additional training that will take place:
	- The model was trained for 100 extra random trees in parallel.
	The "extra" in extra random trees comes from the fact that the cut points for the nodes are selected randomly, rather than optimally as would be done in a purely random forest regressor.
	
- Description of current accuracy score:
	- For this regression model the R<sup>2</sup> value is approximately equal to 0.9985 which indicates that much of the variation in the observed data can be attributed to the features used during the modelling process.
	This value is suspiciously high, and may likely be an indication of overfitting.
	
	## Outputs label(s) for input data
	https://github.com/THeath15/Group1-Project---Sketch-it-out/blob/e2f1ec6065925112a6ae1c13e7a7f1781fbfcf7e/Images/ml_flowchart.png

# Database: 

Sample data that mimics the expected final database structure or schema 

https://github.com/THeath15/Group1-Project---Sketch-it-out/blob/main/Images/ERD%20Diagram.PNG

https://github.com/THeath15/Group1-Project---Sketch-it-out/blob/main/Images/Database%20ERD%20coding.txt


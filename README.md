# ml-model-nba

This project aims to predict the results of games in the National Basketball Association (NBA). A combination of jupyter notebooks files are used to scrape data from the web,
to parse that data, and to predict the games using machine learning models.
1. Data Scraping (get_data.ipynb)
2. Data Parsing (parse_data.ipynb)
3. Prediction Modeling (predict.ipynb)

# Data Scraping
This notebook is responsible for collecting data from basketball-reference.com as it contains a detailed box view of all NBA statistics. I used the Playwright library which allows us to 
launch to websites and navigate through specific webpages to access the needed information. BeautifulSoup is used to parse html/xml and this is how I was able to grab successfully extract the information.

# Data Parsing
Once the raw data is collected in the form of html, we need to process and parse the data much more. This will allow us to use it for our machine learning models. In this part, I use pandas and BeautifulSoup
to continue to process and clean the data. I also used OS to interact with the file system, enabling me to read and write to files.

# Prediction Modeling
The final step in the project involves building and training machine learning models to predict the outcomes of games. I refined the dataset more, involving the removal of unnecessary columns and 
handling of missing values, ensures the data is in optimal shape for modeling. I used normalization to compress the values from range 0 - 1 to put them on scale, which helps in improving the performance
and convergence of the models. I also used SequentialFeatureSelector to best select the features, identifying the most important variables when predicting game outcomes. A function was also created
to contain the rolling averages as a feature, this would allow us to see the performance of a team in it's last 15 games, an important feature when predicting games. The dataset was split 
into training and testing sets using cross-validation allowing us to reduce overfitting and test our performance.

Various models were explored in this project to determine the best-performing model. The models used were: XGBoost Classifier, Random Forest Classifier, and Ridge Classifier.
XGboost Classifier: An implementation of gradient-boosted decision trees designed for speed and performance. It uses a boosting technique where multiple weak models (decision trees) 
are combined to form a strong predictive model. Each tree corrects the errors made by the previous ones, 
Random Forest Classifier: Builds multiple decision trees during training and outputs the class that is the mode of the classes for classification or regression of the individual trees. 
Each tree in the forest considers a random subset of features, which helps in reducing variance and improving the model's robustness against overfitting.
Ridge Classifier: Ridge Classifier is a linear model that is particularly effective for binary classification tasks where the relationship between features and the target variable is relatively straightforward.
It includes a regularization term that penalizes large coefficients, which helps prevent overfitting.

In this domain, the Ridge Classifier ends up out performing the other 2 models with an accuracy of 65% prediction which is considered to be quite good since in a binary classification, 
guessing the outcomes of games would inevitably result in a 50/50 split and since the outcomes of games are inherently unpredictable.

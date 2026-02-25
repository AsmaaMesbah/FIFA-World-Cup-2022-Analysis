# FIFA-World-Cup-2022-Analysis
# 1. Summary
This project analyzes match statistics from the FIFA World Cup 2022 to determine which features are most strongly related to winning. Using exploratory visualization, correlation analysis, and logistic regression modelling, it was found that shots on target had the highest predictive power for match outcomes. Visual and statistical methods both supported the conclusion that attacking performance is a key factor in winning a match. 

# 2. Analysis Plan 
## 2-1. Aim
With the FIFA World Cup 26 around the corner, an analysis of the previous tournament (FIFA World Cup 22) can give useful insights for fans, analysts, teams, and even casual viewers about what to predict while watching the next world cup. This project aims to examine whether specific match statistics - such as possession, shots on target, goal preventions, etc, have a correlation with the match outcome (loss, draw, or win). The results of this analysis can identify which statistics are most strongly correlated with winning, and therefore can help viewers better understand key performance indicators during live matches and may also offer tactical insights for teams preparing for the next tournament. 
## 2-2. Analysis Method 
To analyze which match statistics are most strongly associated with winning in the FIFA World Cup 2022, exploratory data analysis, as well as predictive machine learning techniques, were used. 
1. Exploratory Visualization  
   The focus in this study was on analyzing the following features:
   * Possession
   * Shots on target
   * Goal preventions
   * Number of goals scored
   
   Box plots were used to visualize how each feature varied across the three match outcomes: **win, draw, and loss**. This helped in understanding the central tendency, variability, and general trends in the data. 
2. Correlation Heatmap  
   To assess relationships between features and the outcome variable, a correlation heatmap was created using **Pearson correlation coefficients**. This allowed for visualizing the strength and direction of the linear relationships among the chosen features.  
   Although `result` is a categorical variable, it is encoded numerically for the purpose of correlation analysis. Heatmaps were chosen for their effectiveness in visually representing variable relationships between variables. 
3. Logistic Regression  
To formally evaluate which features were most predictive of winning, **logistic regression** was implemented. Since the match outcome is not continuous but a binary variable (win or not win), logistic regression was an appropriate choice.  
The result column was converted to a binary target variable:
    * 1 if team 1 won
    * 0 if the match was a draw or a loss

    The following features as predictors:  
      * Possession (team1)
      * Shots on target (team1)
      * Goal prevention (team1)

    These features were selected based on earlier exploratory insights and correlation analysis. 
4. Prediction Visualization
To support interpretation, each features was plotted against the **predicted probability of winning** using the fitted sigmoid function. These plots help show the effect of each feature on the model's prediction in an intuitive way. 
5. Model Evaluation
Model accuracy was calculated by comparing the predicted outcomes with the actual match results. This provided a basic but effective measure of model performance.  
**The model was adapted from the book in reference 3**

## 2-3. Data Used for Analysis
The data set used in this project was created by Diego Farchione and posted on Kaggle (See reference 1). The author created the dataset by means of web scraping and posted it as a ready-to-use csv file. 

# 3. Data Analysis 
## 3-1. Data Cleaning & Pre-processing 
In this section, the data was cleaned and prepared for easier analysis. This was done by: 
* removing the '%' sign in the columns that contain it and keep the data as plain numbers.
* making sure the numeric data is stored as float/int/double etc. not as strings.
* checking for missing values.

In addtion, since the goal of this project is to examine the effects on the results of a soccer game, a 'result' column was added such that it contains one of the following values:
* 1: win (team1)
* -1: loss (team1)
* 0: draw

# 4. Analysis Result 
The analysis showed that certain match statistics had strong associations with match outcomes.
* Shots on target had the most noticeable effect: teams with more shots on target were more likely to win.
* Possession showed a mild positive trend, but some teams still lost even with high possession percentages.
* Goal preventions had a less clear effect and appeared to be more common in losing teams, possibly reflecting strong opposing attacks.

## Logistic Regression 
The logistic regression model achieved an accuracy of approximately 73.4% in predicting whether team1 would win. 
Visualizations using fitted sigmoid curves also confirmed that shots on target had a clear increasing effect on win probability, while the effect of possession was present but less steep. 

# 5. Observation
This analysis suggests that attacking performance, especially shots on target, is a key factor in determing match outcomes. Although possession is often considered important as it shows which team controls the match more, it was not always a decisive indicator of winning. Teams could dominate possession and still lose if they lacked effective shots on goal.  
Defensive metrics like goal preventions did not strongly predict winning; in fact, higher numbers of goal preventions often occurred in teams that were under heavy pressure.   
The logistic regression model helped quantify the effects of these features. However, the model's accuracy is limited due to the small dataset (only 64 matches), and more advanced models could be explored in future work. 

# 6. References
* Diego farchione, "Fifa World Cup 2022: Complete Dataset", Kaggle, updated 2022, [https://www.kaggle.com/dataset/die9origephit/fifa-world-cup-2022-complete-dataset?resource=download] (Accessed: 2025-07-10)
* pandas, "pandas.DataFrame.apply - pandas 2.3.1 documentation", pandas, URL: [https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html] (Accessed: 2025-07-27)
* 伊藤真『Pythonで動かして学ぶ！あたらしい機械学習の教科書 第3版』翔泳社，2022年，6.1.7節

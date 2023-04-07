# Video Game Sales Analysis

This project analyzes video game sales data to gain insights into factors that influence game sales, including genre, publisher, and ratings.

## Prerequisites
1. Python 3.x
2. Jupyter Notebook
3. pandas, numpy, matplotlib, seaborn packages


## Data Cleaning
- Filled missing values in the following columns with 'Unknown' or the column median: Name, Platform, Year_of_Release, Genre, Publisher, Developer, Rating.
- Converted the Year_of_Release, Critic_Count, and User_Count columns to integers.
- Handled outliers by setting minimum values of 0 for the NA_Sales, EU_Sales, JP_Sales, Other_Sales, and Global_Sales columns.
- Filled missing values in the Critic_Score, Critic_Count, User_Score, and User_Count columns with their respective column means.
- Normalized the numeric columns using the StandardScaler from the sklearn package. Updates: this approach eventually led to the sales data of Global sales becoming negative and finally discarded.

## Exploratory Data Analysis
- Plotted scatterplots to examine the relationship between Critic Score and Global Sales, and between User Score and Global Sales.
- Grouped the data by genre and examined the total global sales for each genre using a bar chart.
- Identified the top 10 publishers based on total global sales and created a filtered dataset to compare their performance to other publishers.
- Examined the correlation between count of genres per publisher using a heatmap.
- Investigated the relationship between count of games per publisher and global sales using a scatterplot.
- Identified the publishers with the highest average ratings using a bar chart.
- Calculated the number of unique games with metacritic ratings sold globally each year using a line chart.
- Calculated the mean, median and mode of sales by each region as well as total globally.
- Identified which individual game have the highest sale price globally.
- Identified the Sales of games by each individual platform for each region.

These analyses addressed the following questions:
1. What does critic/user scores and global sales look like?
2. How does genre affect global sales?
3. How much better do popular publishers perform?
4. Is there a correlation between count of genre per publisher?
5. How do count of games per publisher relate to global sales?
6. Which publishers have the highest average ratings?
7. How many unique games, with metacritic ratings, are sold globally each year?

Addition research:
- Plot the sales distribution of different game genres and discuss how game genres affect global sales.
- Draw a line chart of the number of game releases and sales in each year to study the impact of historical reasons on the number of game releases.
- Analyze the sales ratio of different regions and draw a pie chart to study the impact of regions on sales.

## Model Building

To forecast game sales in this project, we constructed both classification and regression models.
One-hot encoding was used by the model to encode categorical columns. 80% of the data were used for training, and 20% was used for testing and to enhance the performance of the model, we scaled the data using StandardScaler.

### Classification Task
- We intended to predict if a game has high user ratings (binary classification) based on factors such as sales, critic scores, and other pertinent information.
- Using accuracy and F1 scores, we assessed the performance of the categorization models.
- The Support Vector Machine has the highest accuracy and F1 score of any model.

### Regression Task
- We set out to forecast worldwide video game sales using factors including genre, publisher, and user reviews.
- Using the use of mean squared error (MSE) and mean absolute error, we assessed the effectiveness of the regression models (MAE).
- The Random Forest Regressor was the model that performed the best in terms of MSE and MAE.

## Results and Evaluation
In this part, we provide the classification and regression model findings and assess the effectiveness of both models.

### Classification Results

Gaussian Naive Bayes: Accuracy: 0.5861, F1 Score: 0.3391
K-Nearest Neighbors: Accuracy: 0.9638, F1 Score: 0.8308
Support Vector Machine: Accuracy: 0.9907, F1 Score: 0.9608
Random Forest: Accuracy: 0.9967, F1 Score: 0.9861
The best-performing model for classification was the Random Forest, with an accuracy of 0.9967 and an F1 score of 0.9861.

### Regression Results

Linear Regression: Mean Squared Error: 0.4565, Mean Absolute Error: 0.5272
Random Forest Regressor: Mean Squared Error: 0.0838, Mean Absolute Error: 0.2057
The best-performing model for regression was the Random Forest Regressor, with a mean squared error of 0.0838 and a mean absolute error of 0.2057.

## Company Stock Prices(including references for Challenges/Concerns)
- Line graph to examine the relationship between major video game developers stock prices over a 12 year period.
- Two bar graphs showing the average closing stock value by year for both Nintendo and Microsoft to focus on the difference in trends in the early 2010s
- Reference list of platforms Nintendo(publisher) games are on.
- Reference graph showing the sales of Nintendo consoles from 1997 to 2021

## Challenges/Concerns
**Limited data**
Our dataset of over 16,000 games had a fair amount of blank values sprinkled through out it. These tended to be on the less popular games whereas if there were blanks in the top 50 or so games it would be more noticeable. There were few enough examples that we were not concerned with proceeding with our analysis, however, we cannot know what impact this truly has on our models. We also had the restriction of limited time periods covered. The data for the 16,000+ games was last updated 6 years ago, which means we are missing about 6 years worth of data between then and modern day. We still have plenty of data to create our models, but the videogame industry as changed quite a bit in the past 6 years. There has been more of a push towards online gaming membership where players no longer buy the games themselves, but rather pay a monthly fee to have access to a wide library of games(similar to the shift from itunes to apple music). Both Sony(PlayStation) and Xbox have been pushing in this direction making it difficult to accurately track game sales in terms of copies sold. This concept in itself will need to have its own algorithm to calculate the revenue of a game and how to tie that in with copies sold.


**Various factors not considered**
While there are numerous factors to consider for predicting game sales, one factor seems to be highlighed these stock trends. Console eras can have a major impact on game sales and stock values. The best example is Nintendo. This publsiher is unique in that all of their published games are only available on Nintendo platforms(Reference 2). This means thier sales are dependent on not only the game itself, but the consumer reception of their platform as well. The unique dip of Nintendo's stock from 2011 through 2016 perfectly aligns with thier release of the Wii U platform. This new platform was a low point in Nintendo's sales and consumer reviews for their latest console(Reference 3). If Nintendo's games can only be played on their consoles, and their consoles were unpopular during this time period, it only makes sense that Nintendos stock would drop unlike the trends of the other top publishers. It is unusual for a Nintendo console to be received so poorly but it shows how each console release cycle presents an unforeseen risk or opportunity for Nintendo's stock values that will also impact game sales. 

This ties into the factor of policy and development intervals as well. The cycle of both consoles and game releases will impact sales, especially depending upon the time of year the game is released. An example is the game CyberPunk 2077, which was a highly anticipated game to be released mid 2020. The next generation of both PlayStation and Xbox consoles were to be released late 2020(they typically release around the same time). CyberPunk 2077 got delayed to release in December 2020, about a month after the new console releases. The CyberPunk release was also cursed with numerous glitches/bugs that it was almost considered unplayable on multiple platforms. If CyberPunk could have aligned there release to have a successful product launched around the same time of a console release, that game will be associated tightly with that newest console. Gamers who just bought a new console would love to play a newly released game on it. While Covid was a key driver to CyberPunks delays, it overall had an unsuccessful launch and did not live up to its hype. Game delays or more often games releasing with glitches are something we cannot factor in to our models as we do not have data to predict unsuccessful day one releases.  

## Usage

In alignment with our powerpoint presentation:
1. Open the "dataCleaning.ipynb" file in Jupyter Notebook to view the cleaning process for our data.
2. Open the "Data Visualizations and EDA.ipynb" file in Jupyter Notebook, which pulls the data from file "cleaned_vgames_data.csv".
4. Run each cell in the notebook to reproduce the analysis.
5. Use the generated EDA visualizations for our initial market analysis.
6. Open the "VideoGame_Model.ipynb" file in Jupyter Notebook, which pulls the data from file "cleaned_vgames_data.csv".
7. Run each cell in the notebook to reproduce the analysis.
8. Reference the generated visualizations for our various regression and classification models.
9. Open the "Publisher Stocks & Impacts to Game Sales.ipynb" file in Jupyter Notebook, which pulls the data from files "act_bliz.csv", "ea.csv", "microsoft.csv" and "nintendo.csv".
10. Run each cell in the notebook to reproduce the analysis.
11. Reference the generated visualizations and notes for our analysis on stock prices and the relationship with game sales.

## Data
The video game sales data used in this analysis can be found in the cleaned_vgames_data.csv file in the data folder. The data was sourced from Kaggle, and includes information on video game titles, release dates, platforms, genres, publishers, sales by region, and ratings.

An additional data source was used to analyze the the stock trends of 4 major video game developers from 2010 to 2022. CSV files "act_bliz.csv", "ea.csv", "microsoft.csv" and "nintendo.csv" were uploaded to the file "Publisher Stocks & Impacts to Game Sale.ipynb" to compare tends with game sales. This data aided us in assessing our challenges and concerns.

## Contributor

Kim Dineen 
Yi Yang
Patel Dhrumil Chiragbhai
Arnav Goel

## Acknowledgements
We would like to thank the Kaggle community for providing the video game sales dataset used in this analysis.
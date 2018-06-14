# *Data Analytics Project* 
## *About*
Project focuses on analysis of FIFA 18 players data.
## *Data source*
The dataset was extracted from website [sofifa.com](https://sofifa.com/) using **Python** **Pandas** methods.
## *Built with*
The project was implemented with [Python](https://python.org/) programming language using **Jupyter Notebook** from [Jupyter](https://jupyter.org/).
## *Team members*
| Member | Github |
| --- | --- |
| Yaroslav Khamar | [https://github.com/YarkoKhamar](https://github.com/YarkoKhamar/) |
| Pylypchak Oleg | [https://github.com/liole](https://github.com/liole/) |
| Mykhailiuk Ivan | [https://github.com/IvMykh](https://github.com/IvMykh/) |
| Kavetsky Andrii | [https://github.com/AndriyKavetsky](https://github.com/AndriyKavetsky/) |
## TODO
- [x] Extract the dataset from the website
- [x] Clean the data and prepare dataset for analysis
- [x] Exploratory analysis
- [x] Perform PCA
- [x] Perform Clustering
- [x] Implement position predictor
- [x] Construct an optimal (best) team possible

For more complete information on our goals, please refer to our [Trello](https://trello.com/b/8txcuPMS/data-analytics-project/) board.

## How-to
The dataset, extracted from the website is in **.csv** format. If you wish to use **Jupyter** and conduct further analysis, just insert this line in the beginning of respective notebook in order to load the dataset into **Pandas DataFrame** variable **df**.

```python
%run init.ipynb
```

# Project report

## Introduction

The dataset contains lot's of information, regarding players physical attributes as well as their wages, playing positions and national backgrounds. This provides us with wide variety of opportunities to analyze the correlations of different attributes, compute statistical quantities, representing the averages of characteristics needed, to become a professional player and so on. We also can apply supervised and unsupervised learning techniques to obtain new knowledge about the specifics of some groups of players as well as derive general conclusions of the dataset as a whole.

The team work has been organized through ```git``` version control system; the remote repository can be found [here](https://github.com/YarkoKhamar/DAProject/tree/Development).

The project task management system used for our project is ```Trello```; the all the activity can be found [here](https://trello.com/b/8txcuPMS/data-analytics-project). 

## Description

The main dataset being analyzed consists of the information about 17 000 players (as of September 2017) and contains around 70 variables (various skills measures, physical characteristics etc.). 

To extend it, we joined it with another one containing some missing information about football club (Country, League Level etc.). 

Besides this, in order to perform the profitability analysis for football clubs, we imported yet another dataset to keep track of some particular variables in span of several years.  

## Tasks

All the results of our work can be categorized in the following way:

- [Data Cleaning](DataCleaner.ipynb)
- [Exploratory analysis](ExploratoryAnalysis.ipynb)
- [Unsupervised learning + PCA](PcaClusteringGeneral.ipynb)
- [Supervised learning](PositionPredictor.ipynb)
    
### Extra tasks
- [Optimal team generation](TeamSelection.ipynb)
- [Clubs profitability analysis](ProfitAnalysis.ipynb)

## Conclusions

Having performed the analysis of our dataset we can draw some interesting conclusions.

1. Prior to the analysis itself, the data preprocessing stage took place consisting of:
    - *data retrieval*. 
    - *data cleaning* - the dataset has been cleaned from null (NaN) data, unnecessary rows and columns.
    - *data merging* - several datasets have been combined into one to perform some specific tasks.
    
2. From the exploratory analysis we obtained some results:
    - Distributions of the variables are mostly normal. On the other hand, we had some exponential distributions(e.g. Wage), or a combination of a few normal distributions, corresponding to different playing positions.
    - To perform correlation analysis we had to split database in 2 parts(otherwise, we will observe some paradoxes). Some of columns represent physical characteristics of players, they are highly correlated, especially inside logical groups.
    - Observing, exponential relation between overall rating and wage, we saw, that some good players are underpaid. We analyzed this phenomenon, later, with geographical tools.
    - From joined variable correlation, we can conclude, that with age, players get closer to their potential. Also, we managed to get an approximation of player's potential from his age and reaction.
    - By geographical analysis, we concluded, that the best clubs are in Europe, underpaid players in terms of wage are mostly located in Ukraine, Greece and Czech Republic. Players with most potential are coming from Asia, but play for Finland, Switzerland and Denmark.
    - The most popular formation if found to be 4-4-2
    - Value of the players grow, as they play farther forward in the field.
    
3. Unsupervised Learning & PCA provided us with the following results.
    - Principal component analysis has been performed for the whole dataset as well as for the goalkeepers and outfielders separately. 
    - We discovered that 2/3 of the variance of the whole dataset is carried by two first principal components. This means that our data can be visualized on the plane quite well.
    - We tried to give the meaning to first two principal components. Namely, for the whole dataset the 1st PC has to do with goalkeeper vs outfielder variability, and the 2nd PC has to do with the general position on a pitch (defender, midfielder or striker).
    - The attributes specific to particular position on the field (goalkeeper, defender, striker etc.) tend to be highly correlated.
    - Similar conclusions have been drawn for the goalkeepers and outfielders separately.
    - The PCA by league levels shows that, firstly, general structure of the factorial plane is maintained for all league levels (roughly the same as in the overall case), and secondly, the lower is the league level, the 'worse' are the players.
    - The further league levels analysis shows that the less is the league level, the more diverse are the players (in the sense of corresponding principal components explained above)
    
    - The cluster analysis exhibits two clusters with high silhouette score - goalkeepers vs outfielders. Since this result is quite obvious, the further analysis has been done for larger number of clusters.
    - Clustering of goalkeepers and outfielders separately shows that either there are no well-separated clusters or the K-Means approach with its centroidal model of cluster is not a right choice for this dataset.
    - Clustering separately by league levels shows the different structure of clusters (the interpretation of clusters varies according to a league level).
    
4. We have performed supervised learning analysis, implementing 3 models of classification: Logistic Regression, Neural Networks and Decision trees. 
    - Before modelling and predicting the outcomes, we've extracted the needed columns of a players dataset, that best represent each player, with accordance to his respective position. We've decided to exclude the goalkeepers at the beginning, since their attributes are unique only to them and it will be relatively easy for a classificator to correctly predict the outcomes. 
    - During the analysis, we decided to split our positions list to 2 categories of classes: 1) defensive and attacking positions; 2) classify all positions as separate classes. 
    - After preparing learning and testing datasets (we've normalized the data for more accurate performance), we have taught our models (model fitting) and tested them, to see the outcome. 
    - For each model we've calculated the accuracy score of the predictions. We've have also plotted the confusion matrix for Logistic Regression model, looked for optimal parameters, that would boost the performance of the neural network architecture, we have chosen (Multi-Layer Perceptron) as well as plotted (if possible) and rendered the graph during the Decision tree analysis. 
    - As a result, we conclude that supervised learning outcomes were much better in the cases of 2 classes of positions, rather when we tried to predict players positions on a target set of fourteen classes. 
    - The results we've got were about 80% accuracy in average in the first case, mentioned in the above sentence, and about 40% accuracy in average in the second case. 
    - We've also tried to improve the results of logistic regression by using only the most important attributes (which we calculated along the way). This improvement was not huge, but visible, in the case of 2 classes of positions. 
    - In the end we also brought back the goalkeepers just to make sure, that our models work accurately during their classification. The average overall accuracy hasn't improved a lot, which was expected, given the specifications of data and attributes as a whole. 
    - We can conclude, that, the more target set is richer in a sense of sheer quantity of classes to be classified, the worse is the accuracy of the predictions. But, if taking only 2 classes of playing positions, the outcomes are quite nice and useful. 
    - This prediction can be applied in some real-world situations, e.g. when scouts are looking at young players, whose position is not necessarily defined, they can use classification techniques to help them take right course in their respective careers.
    
5. Besides this, our goal was to implement the algorithm for 'perfect team' construction. 
    - We formulated it as a mathematical boolean programing problem: given a playing formation and the amount of money available, find a set of 11 players satisfying the constraints in sense of preferred position and value.
    - The problem has been solved by use of the third-party python library.
    - We also provided an example of its solution for a sample input data.
     
6. The final objective was to analyze club profitability.
    - To do this, we used archive data, and simulated plyers transfer, keeping track of the balance of each team.
    - Comparing this to estimated data from a news agency(since such data is not public), the first two entries turned out to be the same, others may be the result of not up to date dataset.
    - Popular clubs are mostly in the bottom of this rating, because, they spend a lot of money on the best players.
    - Joining this analysis with an average team ratings, we determined clubs, which bring up good players to be successful, not just buy them. Real Madrid became a top team in this rating.
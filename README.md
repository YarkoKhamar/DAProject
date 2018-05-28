# *Data Analytics Project* 
## *About*
Project focuses on analysis of FIFA 18 players data.
## *Motivation*
The dataset contains lot's of information, regarding players physical attributes as well as their wages, playing positions and national backgrounds.
This provides us with wide variety of opportunities to analyze the correlations of different attributes, compute statistical quantities, representing the averages of characteristics needed, to become a professional player and so on.
We also can apply supervised and unsupervised learning techniques to obtain new knowledge about the specifics of some groups of players as well as derive general conclusions of the dataset as a whole.
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
## Tasks
- [x] Extract the dataset from the website
- [x] Clean the data and prepare dataset for analysis
- [ ] Exploratory analysis
- [ ] Perform PCA
- [ ] Perform Clustering
- [ ] Implement position predictor
- [ ] Construct an optimal (best) team possible

For more complete information on our goals, please refer to our [Trello](https://trello.com/b/8txcuPMS/data-analytics-project/) board.

## How-to
The dataset, extracted from the website is in **.csv** format. If you wish to use **Jupyter** and conduct further analysis, just insert this line in the beginning of respective notebook in order to load the dataset into **Pandas DataFrame** variable **df**.

```python
%run init.ipynb
```
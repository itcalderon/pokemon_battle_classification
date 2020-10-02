# pokemon_battle_classification

The goal of this project is to create a classification model that will correctly predict the outcome of a Pokemon battle. The data for this project was found on [Kaggle](https://www.kaggle.com/terminus7/pokemon-challenge) and contains two different datasets: (1) Pokemon data for 800 unique Pokemon and (2) 50,000 battle outcomes for battles between two Pokemon which were calculated using an undisclosed algorithm. Along with creating an accurate classification model, I hope to give insight to Pokemon Trainers about which Pokemon characteristics are most likely to guarantee victory in battle. 

In this repository there are four notebooks:
  * **pokemon_data_cleaning**: Details the initial data cleaning process.
  * **pokemon_stats_eda**: Data exploration and hypothesis testing on Pokemon stats (HP, ATK, DEF, etc.). It also contains the feature engineering and the creation of the final dataset for the battle EDA and modelling. 
  * **pokemon_battle_eda**: Explores what characteristics are likely to contribute to a Pokemon's victory. It focuses on Pokemon types and status.
  * **pokemon_classification_model**: Walks through the modeling process and analysis of the results of the models. 
 
 # Models
 
All models used all features created during the EDA process. Pokemon types were transformed into numerical values (0-153) and Pokemon IDs (1-800) were used instead of names to pass them into the model. Four models were ran: three Decision Tree Classifiers (one with no regularization and two with regularization using sklearn GridSearchCV) and one Random Forest Classifier (which was put through a GridSearchCV, as well). The overarching goal was to get the best accuracy score possible while maintaining interpretability, since I wanted to give inside on which Pokemon characteristics made victory more likely. All models had an accuracy score between 0.91-0.93 and all were consistent in determining the most important features. In the end, the Random Forest Classifier was chosen to analyze the most important features. 

# Key Features

The most important features:

  * **Pokemon Speed**: A Pokemon is more likely to win a battle if it has a higher speed stat. Additionally, the bigger the speed advantage a Pokemon has over its opponent the better its chances of winning are. 
  
  ![Image](wins_by_speed_advantage.png?raw=true)
  
  Negative values mean the Pokemon is at a speed disadvantage while positive values mean it is at an advantge. The difference is quite drastic. Even just a small disadvantage could mean defeat for a Pokemon. 
  
  * **Pokemon Stat Total**: A Pokemon's stat total is the sum of all its stats. It takes into account the different attack stats as well as the defensive stats like HP, Defense, and Special Defense. 
  
  ![Image](wins_by_stat_advantage.png?raw=true)
  
  We can see that the bigger the stat total advantage the more likely it is for a Pokemon to win. It is worth noting that the relationship between stat total advantage and win percent is less drastic than for speed. 
  
  * **Pokemon Attack**: We can see a similar relationship to the previous two features. As attack advantage increases, a Pokemon is more and more likely to win. 
  
  ![Image](wins_by_attack_advantage.png?raw=true)
  
  Compared to the other stats, the change in win percent as attack advantage increases is more constant and less dramatic than the previous two features. 
  
# Conclusion and Next Steps

According to this data set and models ran, a Pokemon Trainer should prioritze speed and attack when builing their team of Pokemon. It seems that aggressive play is much more favoable than defensive play. Further, they should prioritze training Pokemon that have high stat totals. Raw power is the key to winning a Pokemon battle. 

Unfortunately, Pokemon battles are much more complex than how they are presented in this data set. The creator states that they had to leaves some features out to simplify the dataset. It would be interesting to construct a new dataset/model/algorithm that takes all features of Pokemon into account and deals with all the intricacies of a Pokemon battle, particularly type-effectiveness. 
  


# lolData Report
Authors: Jeffrey Garret, Jesse Krepelka

Introduction:
We have created a model which can predict a players avg KDA over the course of a season based on various loosely related stats.

Originally we had planned to predict the MVP of each season but due to the nature of the game and stats it quickly became apparent this was unfeasable. Our backup plan was to predict a players season performace (by KDA) without the use of kills, deaths, or assits.

DATA: 
Our data comes from the playerstats section of oracleselixir.com. https://oracleselixir.com/stats/players/byTournament
According to the source, 'In most of the stats on this site, values are calculated for each individual game, then averaged across games.'
The player stats are stored as an average over each season of play. 
In our data we cut out any player who had fewer than 6 games played per team per season.
In order to increase our accuracy we used the PolynomialFeatures library from sklearn.

Methods: 
We imported all data into a pandas df and cleaned it up using pandas functions. 
Then we used seaborn to help find some correlation among various features visually.
Following this we trained an sklearn LinearRegression model to predict for us using various stats we had found to have an influence on KDA but were not directly linked to it.
In order to improve the accuracy of our results we made use of sklearn's PolynomialFeatures which got us up to an r-squared score of ~0.91

Results: 
We found that with a high degree of accuracy we were able to predict an individuals KDA within a small margin of error given the following stats: 
	- (W%) Win percentage
	- (KP) Kill participation (What percentage of the teams kills was an individual part of)
	- (DPM) Damage dealt per minute of game time
	- (DTH%) Death percentage (What percentage of the teams deaths was an individual responsible for)
	- (Pos) Position (Top, Jungle, Middle, Bottom, Support)

Discussion: 
The accuracy of our model is an interesting exploration into the abstract data that we dont regularly think about. Polynomial features has improved the accuracy of the prediction to typically be within a rounding error. To test the model we passed data from Cloud9's support player in the current season (gathered 2/26/21), whos current KDA is 2.9 and recieved a prediction of 2.897.
	
Summary:
This project highlights the effectiveness of statistical analysis across an focussed dataset but it is likely to lose accuracy quickly if more diverse data is included. For example it is unlikely that we would be able to construct a similar model for global leagues as there is very little interaction between the leagues meaning large differences in skill level and method of play exist.

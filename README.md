# lolData Report

Introduction

Originally we had planned to predict the MVP of each season but due to the nature of the game and stats it quickly became apparent this was unfeasable. Our backup plan was to predict a players season performace (by KDA) without the use of kills, deaths, or assits.

DATA:
Our data comes from the playerstats section of oracleselixir.com. https://oracleselixir.com/stats/players/byTournament
According to the source, 'In most of the stats on this site, values are calculated for each individual game, then averaged across games.'
The player stats are stored as an average over each season of play. 
In our data we cut out any player who had fewer than 6 games played per team per season.
In order to increase our accuracy we used the PolynomialFeatures library from sklearn.

Methods
We imported all data into a pandas df and cleaned it up using pandas functions. 
Then we used seaborn to help find some correlation among various features visually.
Following this we trained an sklearn LinearRegression model to predict for us using various stats we had found to have an influence on KDA but were not directly linked to it.
In order to improve the accuracy of our results we made use of sklearn's PolynomialFeatures which got us up to an r-squared score of ~0.91

Results
We found that with 90% accuracy we were able to predict an individuals KDA given the following stats: 
	- (W%) Win percentage
	- (KP) Kill participation (What percentage of the teams kills was an individual part of)
	- (DPM) Damage dealt per minute of game time
	- (DTH%) Death percentage (What percentage of the teams deaths was an individual responsible for)
	- (Pos) Position (Top, Jungle, Middle, Bottom, Support)

Discussion
What might the answer imply and why does it matter? How does it fit in with what other researchers have found? What are the perspectives for future research? Survey about the tools investigated for this assignment.
	
Summary
Most important findings.

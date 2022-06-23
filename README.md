# NBA-Playoff-prediction

## 1. Problem Statement

The goal of this project is to predict the final outcome of the playoffs using the
official statistics of all the games played by the NBA from January 2004 to March
2021. This report explains the implementation of the simulation program used.
Briefly, the program works by taking as input the list of teams in the playoffs
and simulates $N$ times 7 matches for each round, returning as the final output a
probability of victory for each team. In each match played, a Machine Learning
model is used to predict the winner.

## 2. Data 

The complete dataset available is made up of 5 .csv files: \emph{(games.csv, games
details.csv, players.csv, ranking.csv, teams.csv)}. Only the data from games.csv
were used in this project. The features available for each row are: \emph{(game date,
game id, home team, visitor team, field goal percentage home, field goal three -
point percentage home, free throws made home, rebound home, assists steals -
home, blocks home, field goal percentage visitor, field goal three point percent-
age visitor, free throws made visitor, rebound visitor, assists steals visitor, blocks -
visitor, home win, visitor win)}. The variables represent the statistics of each
match played from January 2004 until March 2021 for both the home team and
the visitor. The binary variable we want to predict is home win {0,1}, 0 defeat,
1 win.


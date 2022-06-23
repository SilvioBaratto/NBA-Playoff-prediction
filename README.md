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

The complete dataset available is made up of 5 .csv files: _(games.csv, games
details.csv, players.csv, ranking.csv, teams.csv)_. Only the data from games.csv
were used in this project. The features available for each row are: _(game date,
game id, home team, visitor team, field goal percentage home, field goal three -
point percentage home, free throws made home, rebound home, assists steals -
home, blocks home, field goal percentage visitor, field goal three point percent-
age visitor, free throws made visitor, rebound visitor, assists steals visitor, blocks -
visitor, home win, visitor win)_. The variables represent the statistics of each
match played from January 2004 until March 2021 for both the home team and
the visitor. The binary variable we want to predict is home win {0,1}, 0 defeat,
1 win.

## 3. Proposed solution

The proposed solution is to create a program that simulates the playoffs. This
program consists of three main parts: a Machine Learning model capable of
predicting the winner of a match, a stochastic features data generator on which
to use the classifier, and finally the simulation program, which returns the final
scoreboard. The figure below shows the flow diagram of the complete simulation
model and the implementation for each part is explained in the sections below.

### 3.1 Train the classifier

The goal is to create a function, which, taking two teams as input, returns the
winner. To make the winner prediction, it was decided to test three different
Machine Learning models, to compare their effectiveness and choose the best
one. The Scikit-Learn library in Python was used for the implementation of
the models. The games.csv dataset was divided by the 70% training set and 30%
test set. To train the classifier it has been considered only the match statistics
features, 10 in total. The output variable we want to predict is home win.
Scikit-Learn allows us to use the models without hyperparameterization, so it
was decided to make a comparison of the models with and without optimizations.
The models have been optimized using the GridSearchCV function, which
allows us to loop various fittings using combinations of hyperparameters chosen
by us. Accuracy and AUC were chosen as metrics to evaluate the models.

### 3.2 Generate feature values

To simulate the result of the playoffs it is also necessary to generate possible
data on which to predict the future result of the games. To achieve this goal,
a game sample function has been created, which, taken as input two teams,
generates possible features of a match. First of all, to create these features,
the original dataset was taken considering the most recent data, therefore to
predict the 2022 season it was considered from 2020 onwards. For each team it
was created a separate datasets with the match statistics results they obtained in
each game of games.csv, therefore 5 features were taken as we do not distinguish
the scores between home or visitor. Using the Fitter library available for
Python it was possible to obtain the statistical distribution for each of the 5
features for each team. The game sample function in the simulator therefore
generates a random sample of features from the distribution for each of the two
input teams and by putting the features together it is possible to generate a
possible result of a match between the two teams.

### 3.3 Simulate playoffs

The simulator takes as input the list of teams admitted to the playoffs and is
composed of three functions: _(play ngames, play round, simulate)_. The play -
ngames function takes two teams as input and generates a sample of features
using game sample for each of the 7 games, the result for each game is predicted
using the classifier. In the _play\_round_ function, _play\_ngames_ is repeated for each
round, eliminating the eliminated teams from the list. Finally, to get a statistic
and return a probability in the _simulate_ function, N iterations of play round
are made and for each round of the playoffs it is kept track of the times in which
a team has managed to pass to the next round. Therefore the final result of the
simulation is the probability that a team has to move on to the next round.




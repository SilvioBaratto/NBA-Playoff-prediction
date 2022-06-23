# NBA-Playoff-prediction

The goal of this project is to predict the final outcome of the playoffs using the
official statistics of all the games played by the NBA from January 2004 to March
2021. This report explains the implementation of the simulation program used.
Briefly, the program works by taking as input the list of teams in the playoffs
and simulates $N$ times 7 matches for each round, returning as the final output a
probability of victory for each team. In each match played, a Machine Learning
model is used to predict the winner.

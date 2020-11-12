# A Pitch Control Model
![alt text](https://raw.githubusercontent.com/jb-c/Pitch_Control_Model/master/Pitch%20Control%20Images/64984.png "Logo Title Text 1")

## Introduction
This project explored the model proposed in the paper [Beyond Expected Goals](https://www.researchgate.net/profile/William_Spearman/publication/327139841_Beyond_Expected_Goals/links/5b7c3023a6fdcc5f8b5932f7/Beyond-Expected-Goals.pdf) which aims to quantify which areas of the pitch are controlled by each team.

## Overview of How It Works
Each point on the pitch is couloured a shade of red or blue which is proportional to the probability that the red or the blue team control that point.
So dark red regions are very likely to be controled by the red team, blue regions are likely to be controlled by the blue team and white regions are equally likely to be controlled by each team.

The probability that a team controls a point is calculated in the following manner
* We divide the pitch into a discrete grid of cells, and select one to investigate.
* We then calculate a good estimate of how long the ball would likely take to get to this point from its current location, I use a simple projectile model with a drag term and bound the possible flight paths of the ball using some realistic assumptions (eg max ball velocity)
* We then calculate how long it would take each player to reach the grid cell from their current location. This is in general a hard problem to solve analytically and so I came up with some good heuristics.
* Players close to the ball have some probability of controling the ball (modelled as a poisson process)
* The probability that a team controls the ball is the normalised sum of the individual player control probabilities given as a solution to a differential equationdescribed in the paper

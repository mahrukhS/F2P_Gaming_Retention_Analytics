# F2P_Gaming_Retention_Analytics

(There is no dataset provided. I only uploaded the code I used as well as the result. Please look at the attached PDF for a full presentation.)

We analyzed data spanning the initial day to day 7 post-game installation to forecast a player's likelihood of remaining in the game by day 14. Our predictive classification model leverages factors like user behavior, in-game metrics (such as win rate), and engagement patterns to identify players with high potential for long-term retention.

Predicting which players will play our game by machine learning models
The data was divided into training data for the model to learn and validation/testing data to evaluate the model with unseen data. We experimented with three machine learning algorithms: Logistic Regression, Random Forest, and Gradient Boosting. All algorithms were compared, and the best one was selected as our final model.

![im_1](https://github.com/user-attachments/assets/005541db-d815-416f-a6c7-1907961a7e06)

## Using day 7 player data might be too late as we continue to lose player base
As demonstrated in the plot, the longer we wait for players to play and collect data, the better the model can predict whether a player would quit the game. However, we noticed that most players would quit right after playing the game, resulting in a continued loss of the player base as we waited for data. Moving forward, the optimal day for data collection needs to be evaluated, but for now, we used day 7 data as it offered the best-performing models.

Gradient Boosting was chosen as our final model. Based on day 7 testing data, the model effectively captured 65% of all retention within the top 6% of the total population, prioritizing those with the highest retention likelihood. The model provided a similar performance to Random Forest but used simpler measures, making it easier to comprehend.

![im_2](https://github.com/user-attachments/assets/ed30728c-ff1a-4b3b-a6bf-f4b117a3759d)
![im_3](https://github.com/user-attachments/assets/df39536b-9db7-4934-a850-a6b9ab064f37)
![im_4](https://github.com/user-attachments/assets/231342d0-feb7-403d-a4c5-ca9c180e8332)


## How our classifying models work in detail
We defined day 14 retention as true if players were still playing the game on day 14. Our goal was to predict 6% of total players as retained, based on the average of total players in our data. We evaluated our models using the F1 score, which is an equal combination of Precision and Recall.

![im_5](https://github.com/user-attachments/assets/959d8dc2-7604-453f-ad1c-b85a24a64d1c)

First, our models assigned a retention likelihood for every player in our data. Next, we ranked players based on the likelihood, from the most to the least likely to keep playing our game. Finally, we looked at the top 6 percentile to identify the likelihood cutoff (22.6%) and classified players who were more than 22.6% likely as retained.

By not using a 50% cutoff, our models lost some accuracy, as it would overly classify retained players. However, using data from day 0 to day 3, no players had more than a 50% likelihood of being retained (our data is imbalanced, so the model simply placed everyone below 50%). The cutoff needed to be changed for us to classify such a model. This also improved our model performance, enhancing Recall at the cost of less Precision.

![im_6](https://github.com/user-attachments/assets/f881cee3-cc11-47fc-afdf-b8a76faa6b1f)



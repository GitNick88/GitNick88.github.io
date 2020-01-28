My very first blog post was based on a dataset from the National Hockey League (NHL) from 2011 to 2018.  I anaylized some visuals from the dataset so formulate a few conclusions about goal scoring in the NHL. I talked through accuracy, popularity and which shots accounted for the most goals.  Now it's time to venture through the world of being drafted into the most intense level of hockey that there is.

This blog post is similar to the last post in at it's all about scoring goals.  Where it's different is WHO is scoring the goals.  This time, you are the goal scorer. 

![wrist shot](https://media.giphy.com/media/3oKIPDfsoARm0HbWYU/giphy-downsized.gif)

That's right.  That GIF might as well be you.

Below I have an interface for you to predict how many goals you are going to score next season hockey season.  I'll give you a few points for reference but feel free to mess around with the sliders as much as you'd like.  Each widget has the type of shot that you'll take.  Keep in mind what this web app is doing...  It's calculating the coefficient and intercept for each type of shot as it pertains to goal scoring.  If that doesn't make sense, no prolem.  It simply means that my linear regression model adds up all the data between goals by shots verses goals total and comes up with the best pattern that it can.  Once it detects the pattern, we are able to fit a model around the data and begin with predictions.  You'll notice that as you add/subtract shots from your personal prediction for next season, the python function that I've created repredicts the amount of goals that you'll score.

A few things to keep in mind as you become an allstar:
1) The top 50 forwards in the NHL have anywhere between 2 to 4.5 shots per game.  That amount multiplied by the total games in a season, maybe with a few playoff games thrown in the mix, that amounts to somewhere between 180 and 405 shots on goal.  Try and stay between those numbers.  If you think you're going to have the best season ever next year, feel free to deviate!
2) 

With that said, let's get to how well you are going to do next year!

INSERT WEBAPP

Here were the stats from some well known players from last season (2018-2019)
-Sydney Crosby had 220 shots with 35 goals
-Alexander Ovechkin had 338 shots with 51 goals
-Patrick Kane 341 shots, 44 goals
-Connor McDavid had 242 shots with 41 goals

How many shots and goals did you have?  

From a technical perspective, we need to ask how accurate our predictive model is.  First, if we just guessed, what type of error rate might we have in simply predicting your goals by simply calculating the mean of goals.  The "guessing" mean score of the dataset puts us right at 7.3.  Does our model improve that number?  After creating a train, validate, and test split on the data, the model gave a 6.63 for the validation set and a 6.52 mean absolute error rate for the test data.  What do we gather from this?  That our prediction model is better than simply guessing based on the mean of the data.  The mean absolute error tells us how much error we can expect from our model.  The amount of error decreased as we switched from "guessing" to linear regression.  Is the model perfect?  Nope.  As the old statistic model goes, "all models are wrong, but some are useful."  This model is useful in predicting the amount of goals for a given player in the coming hockey seasons.

Here is the link to my google colab notebook for those who are interested:
https://colab.research.google.com/drive/1H8iMeZdrjF_beTEFS2XrSCdZnIJcEMwN

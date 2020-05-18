![Airbnb Logo](/img/airbnb_logo.PNG)

I have yet to stay in an Airbnb.  I had it on my to-do list until the Coronavirus struck the US this spring.  My goal was to take my wife on our 10 year anniversary on a trip to Philadelphia where we could hang out together, enjoy some good food, and check out some cool historical sights.

Other than that, my only other bit of experience with Airbnb is with a Neural Networks project I was given in Unit 3 at Lambda School.  As a matter of fact, my task was to help deploy a webapp with another person in my group because at the time I didn't have any experience with Neural Networks.

I decided to snag the dataset from that project and try it out on my own without any help, after I finished Unit 4 (Unit 4 is entirely focused on deep learning).  Here's what the data looked like:

![Data](/img/airbnb_summary.PNG)

When dealing with a project like this, one of the first things I like to look at is correlated values to my target.  In this case I could use the '.corr()' function in python to see the correlated values but I wanted a visual so here's the corrrelated values in relation to price.

![Correlation Data](/img/airbnb_corr.PNG)

Starting from the left you have the greatest negatively correlated features and all the way to the right are the features with the greatest positive correlation.

Before starting Lambda School I heard the word correlation tossed around so many times.  I must admit, I never knew that correlation was an actual math equation.  For example, I own a restaurant and I have always believed that my business is positively and negatively affected by weather conditions.  This would describe a correlative relationship between the two features.  I never knew, however, that it was a simple math equation.  Correlation is a measurement of how two things change in relation to eachother.

Knowing that, we can look and see that 'accommodates' has the highest positive correlation to 'price', which, if you think about it makes perfect sense because the more people a property can accommodate, the higher the price should be.  That's the relationship.  The more guests at a location, the more it costs.

From there, I built a few box plots to visualize the distributions:

![Model Prediction](/img/airbnb_box1.PNG)

![Model Prediction](/img/airbnb_box2.PNG)

Notice how the bodies of the boxes start in the bottom left and ascend as they move to the right?  That's because the data tells us that as there's a general increate in accommodations and bedrooms, there is a general increase in price.

After looking for the story in the data, it's time to build the model!  First, start with a train/test split of the data and then apply a scaler method to be performed on both 'X' sets of data.

![Model Prediction](/img/airbnb_model1.PNG)

Then, build out the neural network and fit the model.  Because this is a regression problem I wanted to track the loss function of 'mean_absolute_error' and only run on 400 epochs because having run it on 500 or more lead to some overfitting shown in the validation data.

How did this model perform with an actual prediction?  I took index location 90 to try out how the model performed.  You can see the predicted amount and the actual amount on the last line:

![Model Prediction](/img/airbnb_prediction.PNG)

Notebook: [Here](https://github.com/GitNick88/GitNick88.github.io/blob/master/AirBNB_Tensorflow_keras.ipynb)

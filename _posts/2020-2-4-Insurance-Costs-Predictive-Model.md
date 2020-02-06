![Healthcare Costs](/img/healthcare costs.PNG)

Have you ever wondered how insurance companies determine how much people pay on their premiums for health insurance?  Perhaps a better question is: Why on earth is health insurance so high?

I've heard so many explinations... I've heard people say that the reason that health care costs so much is because of doctor salaries.  I once heard an ER doctor explain to me the costs of his insurance policy to defend against mal practice lawsuits - and that, according to him, was the reason that premiums were so high for customers.  I've heard people explain their desire for socialized medicine and how that would help bring down costs.  I've heard a lot of ideas.  What does the data indicate about the rising costs of healthcare premiums?

I found a dataset from Kaggle.com which gave some data pieces that could help provide some interesting insigts into the costs of medical expenses.  Here's what the top of the dataframe looks like:

![Top Dataframe](/img/dfhead.PNG)

As you can see, the dataset has records of a customer's age, sex, bmi, how many children they have, whether or not they smoke, and finally their region in the US. The very lost column is what the insurance company charges each individual.

What I want to do is talk about a few things related to the data. After that, I want to show you a predictive tool, a linear regression model, to help the insurance company determine how much to charge their future customers.  Before I walk through the model itself, I want to point out a few things about what was significant within the data.

## What the data is communicating:
1) The baseline:
If the insuarnce company were to ask what is the best way to predict future costs of future customers, I would start with a baseline.  This is a simple figure, almost like a guess.  A guess isn't a good place to end up, but it's a good starting point.  What I did was take the simple mean of all of the charges and came up with a figure of $13,270.42.  That means for future incoming customers, the company could use the baseline as a reference point for anticipating how much they should charge future customers.  Obviously, though, we don't want to stick with the baseline, we want to build a model that has a higher accuracy rating than a simple average.  So going forward, remember that our baseline guess (without the predictive model) as to the future charges to new customers will be $13,270.

2) Another interesting question that should be asked is what happens if we remove smokers from the dataset?  And what about obesity?
Just taking a quick glance at the dataset I realized that as I ran my eyes down the 'charges' column, prices seemed somewhat static.  They would range between $1,000 and $4,000.  Then suddenly, there would be a large spike in charges to say, $39,000.  I kept seeing this pattern take place where these spikes could pop up out of nowwhere.  Why the sudden spike in cost?  I created a new dataframe that separated out smokers vs non smokers and I compared the total mean costs (for our baseline) of $13,270.42 and calculated the mean for non smokers and the average dropped down to $8,434.27!  Just by removing smokers from the category, we can see a decrease in insurance costs by roughly 36%!

I continued on in my desire to improve the predictive costs for the insurance company (still, without a predictive model) and I ran the statistics for how much charges drop if obesity is taken into consideration.  It turns out that if I remove customers who have a bmi greater than 30 (a bmi greater than 30 is considered obese) then the baseline charges to the customer do not imporve.  Is there a correlation between obesity and healthcare costs?  Maybe, but this dataset didn't drop any hints about the relationship.  If there is indeed a correlation then we either need more data or we need a different way of coming to that conclusion.

One visual that helps display the causal relationship on all of the features and how they impact premiums is by a feature importance chart. Take a look at this!  It will become very clear what has the greatest impact on cost:

![Feature Importances](/img/top feature importance.PNG)

Smoking has, by far, the greatest impact on healthcare costs.

3) The last question that I was curious to ask was: Do men or women cost more money? My original though was that men, on average, would cost less than women.  I was wrong.  Men cost on average $13,956 and women $12,569.

## How accurate is my predictive model?
As I've stated before, baselines are helpful as a reference point but I think we can improve our understanding of healthcare costs if we do better with a predictive model.  If we want to anticipate future costs we need to use a linear regression model that fits better to the data, rather than just an average of the totals.

To build a model, I separated out from the dataset a training set, validation set, and a testing set.  That way we can run the test data as data that the model has never interacted with.  This will give us our R Squared score.  Then I tested two difference types of models and in the end I fit a XGBoost model because it got a higher rating.

![Top Dataframe](/img/XGBoost.PNG)

I ran the testing data to get a final R Squared score and got a .89.  What does .89 mean?  Well, a score of 1 would mean that the coefficient created from the model would explain 100% of the variance of the data.  In other words, the model would be perfect.  That's not realistic.  I wouldn't trust a perfect predictive model because nothing in life is perfect.  So .89 tells me that the model captures 89% of the variance of the data in relation to the model's coefficient.  That's a great sign that we can be confident that when given new data, the model will capture a good prediction with a small margin of error.

What does our model do for price?  Our model, with a training data set, predicts that incoming customers are probably going to cost somewhere around $8794.32.  Remember that the R Squared score says that the model explains 89% of the variance so $8,794 isn't supposed to be an exact number, but it's better than just taking the simple baseline average of the total.

## Let's look at a few visuals from the model:

The first visual here shows the relationship between our target (charges) and a singular feature; in this case it's 'age'.  This visual helps us see as age increases, so does the model's prediction of cost:

![PDP Age](/img/PDP for age.PNG)

Here's a second visual representation of the data.  This time, it incorporates two features, 'age' and 'bmi'.

![Age and BMI](/img/age and bmi.PNG)

If you pick an age, and then a bmi, and follow the chart to where the two intersect, you'll see what the model predicts the costs to be based on those two features alone.  Now, it's important to consider that if someone is listed as a smoker or a nonsmoker, the costs will be pulled in either direction based on the input from the customer.  Remember the feature imporances chart?  It's clear that smoking has the greatest influence on costs to the insurance company.  So on that chart above, a 25 year old with a bmi of 25 would be estimated, from the model, to pay a yearly premium of around $7907.  If the customer is a nonsmoker, that would drastically pull that number down.  If they are a smoker, that information would cause the costs to go up. The point of this chart above is to show how these two features interact with eachother in the model.

## Let's look at an actual prediction from my Jupyter Notebook:

Once the model had been trained and fit it was time for the fun stuff, the predictions!  Here you can see the python code and then directly under was the output.  Here is my example:

![Age and BMI](/img/prediction.PNG)

My notebook asks for some input and once it is submitted and the code cell is ran it will make the prediction.  In this case, with these parameters, the cost for this individual would be $3,446.  With this model in hand, this would be very useful for the insurance company because now they can use this model to predict premium price of future customers.  Always remember, models are not perfect. Remember the R Squared score from the XGBoost pipeline?  It had a score of .89 which means that the model fits the data very closely and so we can be confident that if the  model predicts that the cost for this individual is $3,446 then there may be some variance in actual costs, but it will be relatively close.  That's the power of predictive models!

Have you ever wondered how insurance companies determine how much people pay on their premiums for health insurance?  Any perhaps a better question is: Why on earth is health insurance so high?

I've heard so many explinations... I've heard people say that the reason that health care costs so much is because of doctor salaries.  I once heard an ER doctor explain to me the costs of his insurance policy to defend against mal practice lawsuits - and that, according to him, was the reason that premiums were so high for customers.  I've heard people explain their desire for socialized medicine and how that would help bring down costs.  I've heard a lot.  Most of the time, the explination comes from the perspective of the customer.  What I want to do in this blog post is explain insurance costs from the perspective of the insurance company.

I found a dataset from Kaggle.com which gave some data pieces that could help provide some interesting insigts into the costs of data

INSERT PIC OF DF.HEAD

As you can see, the dataset has records of a customer's age, sex, bmi, how many children they have, whether or not they smoke, and finally their region.

What I want to do is talk about a few things related to the data. After that, I wanted to create a predictive tool, a linear regression model to help the insurance company determine how much their customers will cost them during a 12 month period.

## What the data is communicating:
1) The baseline:
If the insuarnce company were to ask how much should they expect each customer to cost, I would start with a baseline.  This is a simple figure, almost like a guess.  A guess isn't a good place to be, but it's a good starting point or a point of reference.  What I did was take the simple mean of all of the costs and came up with a figure of $13,270.42.  That means for future incoming customers, the company could use the baseline as a reference point for anticipating future costs of futures customers.  If a business knows what their costs are, it makes it easier to forcast how much they will need to charge customers for premiums.  Obviously, though, we don't want to stick with the baseline, we want to do better than that.  We want to come up with a figure that gives us stronger predicting power and a decent amount of accuracy.  We will go over this in the predictive model section.
2) What happens if we remove smokers from the dataset?  And what about obesity?
Just taking a quick glance at the dataset I realized that as I ran my eyes down the 'charges' column, prices seemed somewhat static.  They would range between $1,000 and $4,000.  Then suddenly, there woul be a large spike in charges to say, $39,000.  And again I kept seeing this pattern take place where these spikes could pop up out of nowwhere.  Why the sudden spike in cost?  I created a new dataframe that separated out smokers vs non smokers and I compared the total mean costs (for our baseline) of $13,270.42 and calculated the mean for only non smokers and the average dropped down to $8,434.27!  Just by removing smokers from the category, we can see a decrease in insurance costs by roughly 36%!

I continued on in my desire to improve the costs for the insurance company and I ran the statistics for how much on average costs drop if obesity is taken into consideration.  It turns out that if I remove customers who have a bmi greater than 30 (a bmi greater than 30 is considered obese) then the baseline cost to the insurance company doesn't imporve.  Is there a correlation between obesity and healthcare costs?  Maybe, but this dataset didn't drop any hints about the relationship.  If there is indeed a correlation then we either need more data or we need a different way of coming to that conclusion.
3) Do men or women cost more money?
My original though was that men, on average, would cost less than women.  I was wrong.  Again, looking at the baseline, men cost on average $13,956 and women $12,569.

## How accurate is my predictive model?
As I've stated before, baselines are helpful as a reference point but I think we can improve our understanding of healthcare costs.  If we want to anticipate future costs we need to use a linear regression model that fits better to the data, rather than just an average of the totals.

To build a model, I separated out from the dataset a training set, validation set, and a testing set.  That way we can run the test data as data that the model has never interacted with.  This will give us our accuracy score.  The tested two difference types of models and in the end I fit a XGBoost model because it got a higher accuracy rating.

INSERT PIC OF XGBOOST

I ran the testing data to get a final R Squared score and got a .89.  What does .89 mean?  Well, a score of 1 would mean that the coefficient created from the model would explain 100% of the variance of the data.  That's really unrealistic.  I wouldn't trust a perfect predictive model because nothing in life is perfect.  So .89 tells me that the model captures 89% of the variance of the datain relation to the model's coefficient.  That's a great sign that we can be confident that when given new data, the model will capture a good prediction with a small margin of error.

What does our model do for price?  Our model, with new data, predicts that incoming customers are probably going to cost somewhere around $8794.32.  This was the calculation of mean absolute error on our testing data.  That's good news!



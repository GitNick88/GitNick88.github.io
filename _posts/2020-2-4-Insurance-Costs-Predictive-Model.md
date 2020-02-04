Have you ever wondered how insurance companies determine how much people pay on their premiums for health insurance?  Any perhaps a better question is: Why on earth is health insurance so high?

I've heard so many explinations... I've heard people say that the reason that health care costs so much is because of doctor salaries.  I once heard an ER doctor explain to me the costs of his insurance policy to defend against mal practice lawsuits - and that, according to him, was the reason that premiums were so high for customers.  I've heard people explain their desire for socialized medicine and how that would help bring down costs.  I've heard a lot.  Most of the time, the explination comes from the perspective of the customer.  What I want to do in this blog post is explain insurance costs from the perspective of the insurance company.

I found a dataset from Kaggle.com which gave some very interesting data pieces that could help provide some interesting insigts into the costs of data

INSERT PIC OF DF.HEAD

As you can see, the dataset has records of a customer's age, sex, bmi, how many children they have, whether or not they smoke, and finally their region.

What I want to do is talk about a few things related to the data. After that, I wanted to create a predictive tool, a linear regression model to help the insurance company determine how much their customers will cost them during a 12 month period.

## What the data is communicating:
1) The baseline:
2) What happens if we remove smokers from the dataset?
3) Do men or women cost more money?

## How accurate is my predictive model?
I used a method to my predictive model called xgboost.  I separated out from the dataset a training set, validation set, and a testing set.

INSERT PIC OF XGBOOST

I ran the testing data to get a final prediction 

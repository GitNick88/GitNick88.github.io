![Water Pump](/img/Tanz Water Pump.jpg)


Back in December, 2019 I started my quest in Data Science at Lambda School with the hopes of moving out of the restaurant business and into the world of data and machine learning.  I'm blown at away at what I've learned so far.  Lambda has been a huge challenge and my best way of describing my Data Science experience so far in week 6 is like drinking from a fire hose.  Here's a great visual:

![Fire Hose](https://media.giphy.com/media/14qwRKAyXLEQ9O/giphy.gif)

That said, I've learned some really ammazing things.  I've learned a lot of python, SQL, predictive modeling and even more exciting: I'm seeing how data science can change the world.

In week 6 we were given a task to work on a predictive classification model using decision tree and random forest algorithms on water pumps in Tanzania.  There were three types of classifiers for each pump in Tanzania: functional, non-functional, and functional but needs repair.  The goal was to come up with a model that will help us determine which ones to visit to fix for the people to have fresh drinking water.  How cool is that!

Here's the codition for the assigment for this challenge: there is only enough funds to fix 2000 water pumps so we have to find a way to make sure that we are not wasting any time trying to figure out if certain water pumps are functional or not.  We don't have funds to send people out to water pumps that are functional, we only want to send technicians out to pumps that are either non-functional or functional but need repair.  So where do we start?  A little python code and a baseline:

![Water Pump](/img/baseline.PNG)

What does that show us?  That the total percentage of 'functional' waterpumps makes up 54.3% of the data.  Over half of the water pumps work just fine.  How does that help us?  Well, if we were to simply send out technicians to water pumps in Tanzania that would mean that every 100 pumps visited, 54 of them wouldn't need any attention.  That seems like a lot of wasted time.  Said another way, in order to fix 2000 water pumps, just by guessing (without a model), technicians would have to visit 3,683 in order to fix 2000.

Remember there's only enough funds to fix 2000 pumps.  Think about the cost of visiting 3,683 pumps.  Here's a plotted visual of all the pumps in the country:

![Water Pump](/img/Tanzania Map.PNG)

What if we could create a predictive model that would help us predict accuracy that was significantly higher than a mere guess?  That's what we did in our week 6 Sprint (Sprint, in Lambda terms, refers to a week).

Initially we wanted to form a train and test set on the data, which we did.  We fit the model and scored it for validation accuracy from a random forest classifier.  We got a validation accuracy of 81%!  So now we have a trained model that is significantly better than our baseline (which was an educated guess).  Now, we have a model that can tell us via predicting which pumps are indeed in need of a technician and it's 81% accurate in it's predictions. With that much of an accuracy rating, we'd only have to send technicians to 2,469 water pumps to fix 2,000!  That's far less than 3,683 that our baseline estimate was giving us.  But can we do any better?

![Water Pump](/img/Tanz Water Pump.jpg)


Back in December, 2019 I started my quest in Data Science at Lambda School with the hopes of moving out of the restaurant business and into the world of data and machine learning.  I'm blown at away at what I've learned so far.  Lambda has been a huge challenge and my best way of describing my Data Science experience so far in week 6 is like drinking from a fire hose.  Here's a great visual:

![Fire Hose](https://media.giphy.com/media/14qwRKAyXLEQ9O/giphy.gif)

That said, I've learned some really amazing things.  I've learned a lot of python, SQL, predictive modeling and even more exciting: I'm seeing how data science can change the world.

In week 6 we were given a task to work on a predictive classification model using a decision tree and random forest algorithms on water pumps in Tanzania.  There were three types of classifiers for each pump in Tanzania: functional, non-functional, and functional but needs repair.  The task was simple.  A non-profit has a budget to fix 2000 water pumps but they do not have reliable information on which water pumps to fix.  Send out help to locations that didn't need repair was a huge waste of that budget.  Rather than sending out technicians to every single water pump, and potentially waste money trying to find them, the project was to create a model that could help determine which ones had a high probability of needing repair.  Dispatch could send out technicians to these pumps to fix them so the Tanzanian people would have fresh drinking water.  How cool is that!

So where do we start?  A little python code and a baseline:

![Water Pump](/img/baseline.PNG)

What does that show us?  That the total percentage of 'functional' waterpumps makes up 54.3% of the data.  Over half of the water pumps work just fine.  How does that help us?  Well, if we were to simply send out technicians to water pumps in Tanzania that would mean that every 100 pumps visited, 54 of them wouldn't need any attention.  That's a lot of wasted time and money.  Said another way, in order to fix 2000 water pumps, just by guessing (without a model), technicians would have to visit 3,683 in order to fix 2000.

Remember there's only enough funds to fix 2000 pumps.  Think about the cost of visiting 3,683 pumps.  Here's a plotted visual of all the pumps in the country:

![Water Pump](/img/Tanzania Map.PNG)

What if we could create a predictive model that would help us predict accuracy that was significantly higher than a mere guess?  That's what we did in our week 6 Sprint (Sprint, in Lambda terms, refers to a week).

Initially we wanted to form a train and test set on the data, which we did.  We fit the model and scored it for validation accuracy from a random forest classifier.  We got a validation accuracy of 81%!  So now we have a trained model that is significantly better than our baseline (which was an educated guess).  Now, we have a model that can tell us via predicting which pumps are indeed in need of a technician and it's 81% accurate in it's predictions. With that much of an accuracy rating, we'd only have to send technicians to 2,469 water pumps to fix 2,000!  That's far less than 3,683 that our baseline estimate was giving us.  But can we do any better?  I think so!

We used a "pipeline.predict_proba(X_val)" function on the validation data which returned an array of probabilities.  These probabilities are a percentage of how confident the model feels about making its guess.  Some predictions were .20 confident, some were 98%.  From there, we simply wanted to see all of the predictions that the model had a confidence value greater than 50% and then return those guesses to us.  Then we did the same process again but this time we wanted only predictions returned to us that the model was 92% confident about (We chose 92% because of the distribution of confidence values) and we saw these results:

![water pump results](/img/water_pump_results.PNG)

Notice at the bottom, that the precision we would have if we sent technicians on 2000 trips...  Around 98% of those wells would actually be broken and non functional.  Is the model perfect?  Of course not.  Consider, though, how well we would have done had we just guessed which wells needed a technician.  We would have been closer to 50% accurate.  With this model, we can be certain we would have an accuracy rate much higher than that!

This was hands down the coolest project we did at Lambda.  Not only was it challenging to me to have to figure out a good model but it was all about helping people out in a sensible way!


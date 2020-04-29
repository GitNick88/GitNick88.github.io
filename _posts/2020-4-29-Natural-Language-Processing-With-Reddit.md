![Reddit Logo](/img/Reddit_logo.PNG)

I'm not a huge Reddit user although when researching whether or not to attend Lambda School I managed to come across a rather lengthy post on how terrible Lambda School is.  I read that post and thought, "there's no way the school can be that bad."  I'm glad I didn't listen to the concluding advice from that individual.

Upon completing all of my Data Science curriculumn at Lambda I'm very thankful to have continued on.  The subject that I've enjoyed the most was Natural Language Processing (NLP).  Do date, there's nothing cooler than being able to create a predictive modeling using such a large amount of text data.  I was so excited, I even told my wife that I feel like creating a model with NLP makes me feel like I have a super power.  She wasn't having it, though.  Oh well, it's still my favorite thing I've done at Lambda.

# Our unit 4 project:

At the end of every unit (each unit is 1 month) we had a final project to build.  Unit 4 project was really interesting because we had to work with other data science students and web developer students to build a project together.  The unit 4 project I was assigned to was to build an NLP model that would allow a user to input some text and have a predictive model return to that user which subreddit that text belonged in.  For example, if someone wrote, "History if my favorite subject.  I love to read historical accounts about ancient Rome and Greece. I'm also a big World War 2 buff and I collect objects with historical significance" the model should return to the user that this post belongs in the 'history' subreddit category.

The data science team started with some data scraping from the reddit API.  That allowed us to pull a large sample of posts from each subreddit category.  Once my data science team member pulled the data, I was in charge of building a model that would predict the category for the user's input (A link to my actual notebook is at the bottom of this post).

I tried several different models to see which one would perform the best.  This once that we published seemed to perform the best for us.  We started with this data:

![Data Frame](/img/reddit_df.PNG)

Once we had a good looking data set, we wanted to apply a preprocessing function to the text to clean it, drop stopwords, drop punctuation and return every character as lowercase.

![Preprocessing FN](/img/reddit_preprocessing.PNG)

The function get's incorporated during the TfidfVectorizer pipeline creation once we have a train/test split of the data:

![Reddit Model](/img/reddit_model.PNG)

Now onto the fun stuff, the predictions!  My teammate built a function for us to use that would plug into our flask app and return the top 5 predicted values:

![Reddit Return Function](/img/reddit_return_fn.PNG)

From here I created 4 fake posts and input them through the model to see what the model would predict.  Here's what it came up with:

![Test One](/img/reddit_test_one.PNG)
![Test Two](/img/reddit_test_two.PNG)
![Test Three](/img/reddit_test_three.PNG)
![Test Four](/img/reddit_test_four.PNG)

Here you can see these results.  Not bad!  The model lists each prediction in order from the five most likely categories.  We deployed this project through flask and worked with web students to deploy to their website so the user could in fact input their post, as I did in the 4 examples above.

Link to Jupyter Notebook: https://github.com/GitNick88/GitNick88.github.io/blob/master/Unit_4_Build_NLP_Model1.ipynb

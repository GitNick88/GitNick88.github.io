![Common Shots](/img/pavel-datzyuk.jpg)
###### Detroit Red Wings forward - Pavel Datzyuk


# "It's hockey night in Hockeytown!"  

Growing up, I heard those words every other evening on tv right before the refs dropped the puck.  Some of the best players to ever play the game played in Detroit.  Detroit was also one of the original six hockey teams to join the National Hockey League (NHL).  People in Michigan have a real soft spot for hockey and in 1996, the Red Wing franchise ran a marketing campaign and decided to begin referring to Detroit as Hockeytown. 

Hockey is a great game.  Even for people who don't enjoy sports as much.  The fights, the hitting, the fast pace and the goal scoring all contribute to three exciting periods of glory.  Hockey ran through our blood so much that our parents used to have us watch hockey to feel better:

![wrist shot](https://media.giphy.com/media/uObkDJ0HA62Z2/source.gif)

All joking aside, there are so many facets and strategies to the game.  Not only is the game about strategy but it's all done at a very fast pace.  Oh, and it's essential to mention, it's all done on ice...  Imagine playing with some of the best players around the world. Most passes from player to player are completed 12 feet from eachother.  Often times slapshots can travel 100+ mph.  Not to mention, the game is full contact.  That's right.  Players slam into eachother skating at full speed.  Sometimes they result in injury and sometimes they receive cheering and applause.  Either way, the two best things about hockey are the hitting/fighting and the goalscoring.  Unfortunately I don't have a dataset on NHL fights but I do have one on goals scored from 2011-2018.

I set out with an anticipation of a few ideas about what I might find in this dataset.  For starters, I thought that wrist shots would be the most common, the most accurate, and the most responsible shot type for scoring goals.  For those unaware, here's what a wrist shot looks like:

![wrist shot](https://media.giphy.com/media/l2JhMrZjI8IgTXn4k/giphy.gif)

Did you see how the player dragged the puck from behind him and used his weight as leverage to take his shot?  That's what a wrist shot is.  The reason that I thought I'd find the wrist shot the most accurate is because forwards love taking wrist shots.  They're easier to release because often times the puck is already in shooting position when a player is stick handling.  Also, they can be very quick shots which can easily trick a goalie.  Even with these thoughts in mind I came to see that while a lot of goals are scored via the wrist shot, they are not the most accurate shots as my original thoughts lead me.  So what are the most accurate?  What type of shots resulted with the most goals?  Let's talk through several of these questions.  I know that most hockey fans are interested in several different types of data that would come from this dataset so lets dive into the following four questions and I will demonstrate my findings through a few visuals:

1. What were the most common shots?
2. What shots scored the most goals?
3. What were the most accurate shots?
4. What position predominantly scores each type of goal?

Hockey fans ask these questions all the time.  How could we possibly figure out all of this information?  Good thing the National Hockey League was so generous to publish a dataset for our use.  The dataset is 7068 rows by 42 columns which equates to 296,856 instances recorded!  Don't worry I cleaned and trimmed it down a bit.  I've also used some handy python skills to help us interpret the information rather consicely.  That said, let's start with question number one...

## 1) What were the most common shots?
The types of shots that are recorded are as follows: wrist shots, backhanded shots, deflected shots, slap shots, snap shots, tipped shots and wraparound shots.  Before we begin the actual analysis from the dataset...  do you have any guesses as to which one was most common?

Before I flipped the switch on datawrangling I guessed that wrist shots were most common.  I have a slight advantage because I played hockey myself for several years.  I was a forward and I know that I myself, and other fowards, were very comfortable taking wrist shots.  They tend to be the easiest shots to take, unlike a slapshot which requires an awful lot of strength and can be difficult to direct.  Outside of my own experience, I loved watching the likes of Pavel Datsyuk (pictured above) and Henrik Zetterberg and they both had lazer-like abilities to score with wrist shots.  Even the old legends like Wayne Grezky and Gordie Howe had a wickedly accurate wrist shot.

If you guessed wrist shots like I did, you'd be right!  Here's a visual of the most common shots taken in the NHL from 2011-2018:

![Common Shots](/img/most common shots.PNG)

Look at those numbers!  The chart doesn't show this but the total shots taken totals to 566,171.  On the chart, wrist shots account for 285,420 of those shots which is 50.4%!  That's a lot of wrist shots!  Did all of those wrist shots turn into actual goals, you ask?  Let's tackle that next.

## 2) What shots scored the most goals?
With a wide variaty of the types of shots we have a few different options.  We already know that wrist shots accounted for 50.4% of all shots taken from 2011 to 2018... but we haven't talked about accuracy yet.  It could be the wrist shots in the NHL are not as accurate and didn't score many goals.  On the other hand, if wrist shots are the most common by a long shot, even with low accuracy levels, they could still account for most of the goals scored.  Any guesses as to which types of shots scored the most goals?  Here's the chart to detail the most goals by type of shot:

![Most goals](/img/Most goals scored.PNG)

If you guessed wrist shots, you were right!  Wrist shots are on a hot streak!  Per our dataset, wrist shots are the most common shots taken and resulted in the most goals.  I suppose it makes sense...  Since half of the total shots taken were wrist shots, even if the accuracy is a small number it would still account for a lot of the goals scored since there were 285,420 wrist shots and only 50,923 total goals scored.  Quantity doesn't always gaurantee quality though, as they say.  Let's take a look at our next metric deduced from our dataset: accuracy.

## 3) What were the most accurate shots?
The way I look at accuracy is sort of simple.  As long as a shot is put on goal (it either hits the goalie or it scores) then it gets counted in the total shots category.  Then I take the total number of goals scored by the type of shot and divide it by the total number of shots taken by that type.  The equation is (total goals)/(total shots)...  For example, we know that the total of wrist shots scored were 25,265 and the total amount of wrist shots taken were 285,420.  With our accuracy equation in mind, we divide 25,265 by 285,420 and we realize that 8.8% of all wrist shots went in.  I'm calling this an accuracy rating because it reflects the likelyhood of wristshots turning into goals.  Of 100 wrist shots taken, roughly 8 to 9 of them go in.  How does that measure up to the other types of shots?  Any guesses?

![Most goals](/img/Shot Accuracy.PNG)


I remember as a kid, first learning how to play hockey, having an innate desire to take slap shots at the goalie all the time, thinking that they would be the most likely to go in due to the speed and force at which the puck flies.  This wasn't the case for me.  In fact, I had a terrible time aiming and putting the puck where I wanted with slap shots so I stuck with the good old wrist shot.  Here's a slow motion example of what a slap shot looks like:

![wrist shot](https://media.giphy.com/media/HMHRGXyYJbSpy/source.gif)

I suppose the accuracy rating for slap shots makes sence since slap shots are, 1) very hard to pull off, 2) very hard to aim with, 3) take a long time for a defensive player to let a slap shot go.

Clearly the two winners for "accuracy" are deflected and tipped shots.  These are instances where a player will take a shot, and there will be a teamate standing in front of the opposing goalie in hopes to block the goalie's ability to see the puck or even to tip or deflect the direction of the puck at the last minute.  Can you imagine being a goalie where you have a puck flying at you at 90 mph and it suddenly changes directions 5 feet from you?  Impossible to stop.  The data and the concepts seem to be saying the same thing: deflected or tipped shots are really difficult to stop for a goalie and therefore the most accurate.  While wrist shots are the most common, the highest scoring, they're about half as accurate as tipped and deflected shots.  When it comes to accuracy, tipped and deflected shots are king.

Onto the distinctions between forward and defensive goals!

## 4) What position scores the most goals?
Like most games, there are often physical distinctions between types of players.  In football, a lot of good quarterbacks are tall and have very strong arms for throwing.  Most offensive lineman are larger body types because of their need to use their stature to defend and block.  Hockey is similar.  It's fairly typical that forwards are more agile while defensive players are usually more sturdy and weigh more.  These implications can come out in the game play.  Wrist shots, for example, don't necessarily require a lot of body weight to release the puck, where slapshots do.  Knowing that, we might ask ourselves who is more likely to take slapshots vs wrist shots or wraparounds vs deflected shots.  Asking these questions gets into the common discussion among hockey enthusists about who scores more goals, forwards or defense?

Let's first look at total goals scored for forwards vs defense

![Most goals](/img/forwards vs defense pie chart.PNG)

The pie chart, for me, visualizes what I expected from the data that forwards tend to score most of the goals.  In fact, in almost every type of shot recorded, forwards scored twice as many times as defense.

# Final remarks to the directors of the NHL:

Let's pretend that the board of directors for the National Hockey League want some valuable insights from this dataset.  What might we say?  Here are three things I came up with that are noteworthy points:

1) If your desire is to see more scoring in the NHL, encourage players to get more shots on goal. Perhaps focus on shot types that have a high coversion rate of goal scoring such as deflected and tipped shots.  According to hockey-reference.com the average amount of shots on goal per game in 2018 was 31.3  If players were to find a way to increase the shots by another, say, 4 or 5 shots per game that could lead to more goals across the board.

2) Again, if your desire is to see more scoring in each game, tell your players to take more wrist shots.  Look at the correlation that wrist shots have to goal scoring...  Correlation values that are near '1' have a strong positive correlation.  The correlation value in this instance is .937 so tell the players "wrist shots, wrist shots, wrist shots!"

![Most goals](/img/wrist shots and goals correlation.PNG)

![Most goals](/img/goals vs wrist correlation.png)
###### Here is a visual on a chart of the correlation with a line drawn for best fit.

3) While looking for some anomilies from the data I noticed that the defensive players took 66,509 slapshots and only scored 2,981 (success rate of 0.2%) goals where forwards took 43,726 and scored 3,284 goals (success rate of 7.5%).  This was the only category where the defense had more shots than offense in any category and yet their success rate was significantly lower.  Why might this be?  Positioning on the ice?  Is it that slap shots are simply not accurate?  Is it that defensive players are taking the shots and the forwards are tipping/deflecting the puck and thereby the forwards are getting credited with the goals instead of the defense?

Remember that I stated the two most exciting things about hockey are the goals and the fights.  We just covered the goals, keep your eyes out for a hockey fights dataset and we can analyze that next!

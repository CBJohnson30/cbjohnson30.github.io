# Classifying Colorado Counties based on Voting History using Unsupervised Learning

With election season upon us I thought it was time to finally write about a project I did a few months back. This project steamed around the question, “How do political commentators tell if a county historically votes in favor of Democrats, Republicans or is it considered a swing county?” I was able to ask two political consultants in Colorado this question and both of them answered the question the same way of “With all of our experience of working in the state of Colorado we just know.” Being a data scientist and an analytical thinker this answer did not sit well with me, thus leading me to this project.

With a question in hand, the next step was to figure out how I was going to answer this question. The first part of this was to find, select, and collect my data. With a lot of voting information being public data the Colorado Secretary of State’s website was the first place I went to. Next, I had a few choices to make on what data I was going to use. The Colorado Secretary of State’s website has every voting result made so I had the option to choose from everything possible. I know voter turnout increases when people vote for people and that the bigger the names help inspire the public to vote as well. This led me to decide that I want voting results from “Top of the Ticket Elections.” These types of elections tend to be most talked about and the reason most people vote. For this reason, I picked voted results from Presidential, Gubernatorial, Senate, and Congressional races. Also, I only went back to the year 2012. This let me focus on a five-year time span that included eight different races. My thinking was that this was enough data to get an accurate result but not go back to far to only get a view of the current political climate. Also, to keep it simple I only took vote counts from the top Democrat and top Republican vote-getter in each race.

After setting my data parameters and finding the data on the Colorado Secretaries of State’s website there was some cleaning and joining I had to do before I could train a model. The best way to pull the information was to actually copy it off of the website and past it into an excel spreadsheet. (Lazy I know, but it was easier than using the unorganized excel spreadsheet that is downloadable or web scrapping the even messier website. You got to do what is easiest sometimes.) When I got my data in a workable format it was time to do some joining for some of the races. This was necessary for all congressional races because some congressional districts split counties. For example, Boulder County is apart of both congressional district 2 and 4. In this case, I combined the votes for Democrats from district 2 and 4 in Boulder County to get total votes for Democrats from Boulder County. I did the same for Republican votes and the handful of other counties that deal with split districts as well. To normalize the data I made a percentage of total votes for each party. This will allow me to better compare differently sized counties together so large or small counties to not throw off or skew my model.

The next step in my process was to build a model. For this type of problem I knew I was going to need an unsupervised learning model due to the fact that I had no target variable to train a model on.

Side note, but unsupervised learning has slowly become my favorite ways to analyze data and find patterns that I could not see or think of to look for. I think it is incredibly underused and can offer value to a lot of problems people are trying to solve but, this might be a conversation for another blog. Anyways, I highly recommend people look into it.

The type of model I needed to use for this problem screamed clustering model. I wanted to see which counties behaved similarly to each other and label them in groups. I know of two main clustering unsupervised learning models, K-Means and DBSCAN (Density-Based Spatial Clustering of Applications with Noise). While both of these models are unsupervised clustering models there is one big difference between them. K-Means lets you pick how many clusters the model will find while DBSCAN will choose how many clusters the model will give you by itself. While both models could work for this data set, my problem statement asked for 3 different groups, Republican, Democrat, or Swing. Because of that, I went with K-Means purely because I was able to set the number of clusters that my model would search for.

When running a K-Means model, it will assign each data point a number based on the cluster that is assigned to. I choose K=3, for the 3 clusters I wanted, and those numbers were 0, 1, and 2. To find out what these numbers meant according to my problems context I graphed my data points using a pair-plot and set the hue of the graph to the label the model gave that point. After some analysis and zooming on the labels of the graph, I determined what each label meant and relabeled them to DEM, REP, or Swing for a simpler understanding.

To double check my model and look at my results, I transferred all my data to Tableau and graphed each race in there. As I was looking at my results closer, I started to notice that my Swing or “Middle” classification did not hover around the center of the voting spectrum.

![2016_senate](..\assets\images\classifying_counties_images\2016_senate.png)

Most of these counties always voted for the Republican. While this classification was the middle third of the counties in Colorado, it did not include counties that only hover around the center mark(an equal percent vote towards each party) when it comes to voting percentages. This led me back to my data and to try a different model. The model I tried next was a DBSCAN. The results did not come out as well as the K-Means model I already tried. The majority of the counties would result in a “-1” classification. This means that the data point was too noisy to classify for the model. Even after testing different minimum samples and different values if EPS, (EPS is the maximum distance two points can be to be considered the same classification) most of the counties were still classified as “-1”. With a majority of points not being classified, I knew that a DBSCAN model would not work for my needs.

My next step was to go back to the K-Means model and try different K’s in the model. The different K’s I tried were 4, 5, and 6. Roughly looking the results from each model I knew I was more on track for what I was looking for. I loaded these results into Tableau and was able to closely look at each model to see the classifications. I knew with more than 3 classifications I would need more label names than just Democratic, Republican and Swing. I am going to add the words “Lean”, “Safely”, and “Solid” in front of Democratic and Republican to give me some flexibility in classifying these new labels.

The K-Means where K=4 included the labels; Lean Democratic, Lean Republican, Solid Democratic, and Solid Republican.

![2014_senate](..\assets\images\classifying_counties_images\2014_senate.png)

While I think the K-Means model of K=4 does a lot better job at classifying counties than the K=3 model it does not identify the “Swing” counties I am looking for.

The K-Means where K=5 included the labels; Leam Democratic, Lean Republican, Safely Republican, Solid Democratic and Solid Republican.

![2016_senate_l6](..\assets\images\classifying_counties_images\2016_senate_l6.png)

This was it. I was able to identify four counties that sit right in the middle of the voting spectrum. While Republicans do tend to win these counties, normally the race is within a few points and Democrats have won in these counties which is good enough to earn the classification of “Swing.” These counties are a subsection of the Lean Republican classification from the K=4 and K=5 models. Below is the full state of Colorado with each of the counties classifications.

![state_map](..\assets\images\classifying_counties_images\state_map.png)

Now to put on a political junkie hat and talk about a few things I found interesting for those who are interested.

While going through this project I few races caught my eye and I found them interesting. The first sets of races that caught my eye were all of the House races. What first caught my eye about these races is that they are the least linear looking of all the graphs. Also, house races are the most jumbles between the classifications as well. This is because House elections are not statewide elections and each district has its own set of people running for that office. This causes each a high chance for the election to behave abnormally causing disparity mentioned above in the graph. A great example of this is the 2016 election as seen in the graph below.

![2016_congress](..\assets\images\classifying_counties_images\2016_congress.png)

Another interesting point it is that the higher profile races from each year are more linear than the other elections that took place for the said year. Presidential races tend to be the highest profile races and tend to have the highest turnouts as well. When graphed these tend to be more linear than Governor, Senate, or House races. Below are the 2012 Presidential and 2014 gubernatorial races.

![top_ticket_races](..\assets\images\classifying_counties_images\top_ticket_races.png)

The last point I would like it to make is about the 2014 gubernatorial race as seen above. It the race with the least crossover between the classifications, it actually has no crossover all. I do not know if this is a fluke because I only have one gubernatorial race in my data. If this is not a fluke though and other gubernatorial races behave like this as well, it would be safe to say that the best way to understand Colorado would be through its gubernatorial elections.

To view the rest of the graphs please go to my Tableau Public Profile at: https://public.tableau.com/profile/cbjohnson30#!/

To view the code used to do this please go to my GitHub at: https://github.com/CBJohnson30
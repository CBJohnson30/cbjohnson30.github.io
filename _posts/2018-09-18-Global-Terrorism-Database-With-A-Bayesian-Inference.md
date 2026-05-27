# Global Terrorism Database with a Bayesian Inference

One of my projects during General Assembly’s Data Science Immersive course was to use the Global Terrorism Database to draw analysis using Bayesian techniques. This project consisted of three parts. The first part was to do some EDA (Exploratory Data Analysis) and visualizations that would help you better understand the data. The second part was to was to make a Bayesian Inference on a section of the data of our choosing. The last part was to make a prediction on the number of “Bombing/Explosion” type attacks for the year 1993.

## Data

The Global Terrorism Database is created and maintained by the National Consortium for the Study of Terrorism and Responses to Terrorism (START). It was compiled in 2006. It does not include the year 1993 due to the lack of data collection for that year. The Global Terrorism Database advisory board estimated that they only collected data on roughly 15% of attacks for that year. Some of the more standout columns include; Date columns, region, county, attack type, target type and the number of kills. You can read more about the data collection process and finer details about the dataset on the codebook at http://start.umd.edu/gtd/downloads/Codebook.pdf.

## Part 1

The first part of this project was to do some EDA and familiarize yourself with the dataset in order to complete part two and three. I first started by looking through codebook and trying to background information on what some of the columns in the dataset mean. The first one I looked at was ```attacktype```. There are nine different types of attacks that get classified in this dataset. Some of the types I paid attention too were Bombings/Explosions, Assassinations, and Armed Assaults. These were particularly important because Bombings/Explosions are important to part three and going into the project I wanted to try to use Assassination or Armed Assaults for an inference subject for part two.

With all of the time series information and geographical information, I knew that the best and most interesting way to understand this data would be by using visualizations. I first wanted to look at attack type over the years included in the dataset. Using Tableau, I was able to create an informative graph by being able to separate out each attack types to look at the number of each attack by year. Then, I was able to give each region there own color inside the graph to give some geographical context as well. A screenshot of Bombings/Explosions below but please go to my Tableau Public account to interact with the graph.

![attack_type](..\assets\images\global_terrorism_images\attack_type_by_year.png)

One of my major takeaways from this graph is a piece of information that will be useful for part three of this project when I try to predict the number of bombings/explosions that happen in 1993. By just looking at this graph I can guess that the number I am looking for will be between 1000 and 1500.
The next visualization I created was one to focus on the geographical information of each attack throughout the years in the data set. Using tableau once again I was able to plot the location on each attack on a world map by year. Below is a screenshot of the visualization set for the year 1980.

![attack_world](..\assets\images\global_terrorism_images\attacks_around_the_world.png)

By viewing this on the Tableau Public account you can interact with the visualization to change the year of the attacks being shown. When creating this on Tableau Desktop the transition between years is smoother and allows you to more clearly see the movement in attacks around the world.

## Part 2

The second part of this project was to create a Bayesian inference on this data set. The question I asked was if there was a significant difference in deaths by “successful” armed assaults between the United States and Western Europe. For an attack to be “successful” there must be at least one death. With gun violence being a hot topic all over the world I wanted to dig a little into these types of attacks. All Bayesian Inference includes a prior belief and a posterior belief. For my prior, I used deaths in attacks in Western Europe and North America and the two posterior’s I compared were deaths in Western Europe and deaths in the United States by Armed Assaults. The first step is to find the prior’s mean and standard deviation. The mean and the standard deviation for the deaths in attacks in Western Europe and North America are 1.94 and 4.3 respectively. Next, I have plotted the mean and standard deviation for the two posteriors with a 95% confidence level. Below are the graphs of each of these:

![attack_sd](..\assets\images\global_terrorism_images\attack_sd.png)

The United States’s true mean is between 1.44 and 2.1 its standard deviation is between 1.61 and 2.87 both at a 95% confidence level. Western Europe’s true mean is between 1.44 and 2.34 and its standard deviation is between 4.81 and 5.46 both at a 95% confidence level. The last step was to plot the two posteriors against each other. This can be seen below:

![attack_sd_2](..\assets\images\global_terrorism_images\attack_sd_2.png)

In each of these graphs, the green line represents Western Europe baseline numbers for each stat I am looking at. Delta-mean is relatively close together meaning those numbers are fairly similar. The Delta-STD is the opposite, the green line is not close to the bar chart. This is because Western Europe has a much higher standard deviation than the United States. This means that Western Europe had a much wider range of deaths in their attacks. Given the nature of this data that means that Western Europe has armed assaults with a higher number of deaths than the United States.

# Part 3

The last part of this project was to try and predict the number of Bombing/Explosions attacks in the year 1993. Due to this the nature of this project I wanted to stay within the Bayesian analysis realm to do this. During my EDA(Part 1) I found a target range for the number of attacks I was looking for. My target number was between 1,000 and 1,500. My goal was to create a scatter plot of the number of Bombing/Explosions attacks and lay a line of best fit over the graph. Then I will take that point at the year 1993 and use that as my estimation for the number of attacks. The class was recommended to break down the data into sections before predicting the number of attacks. I decided to break it down by region because I saw this as a logical division of the world and trends that may be happening during this time range. To get a more accurate number I also decided to use information on 10 years on either side of the year 1993. I thought this will also help me get a better representation of what is happening in each region as well. A great example of this is when looking at the number of Bombings/Explosion attacked in the Middle East & North Africa. Around the year 2004, the number of Bombings/Explosions began to rise dramatically due to all the increase in conflicts and wars in the area. I do not want this spike in attacks to skew my predictions. After making a prediction for each region I added them to get a number for all Bombings/Explosions attacks for the year 1993. The number came out to be 1250. This is right in the middle of my range that I was looking for when I started this section.

![region](..\assets\images\global_terrorism_images\region.png)

As you can see in the graphs above I do have a problem with my line of best fit. For each of the graphs, my lines are practically horizontal even though they should have more slope to them, by just looking at the plotted points. Each graph does estimate a non-extreme number and the total estimate is in the range I was looking for. I do not know why I have this problem with the visualizations. My work can be viewed on my GitHub,(Link at the bottom of the article) if anyone has ideas why this happened please feel free to reach out to me.

All of my code can be found at my GitHub at: https://github.com/CBJohnson30/Global-Terrorism

Tableau Public: https://public.tableau.com/app/profile/cbjohnson30/vizzes
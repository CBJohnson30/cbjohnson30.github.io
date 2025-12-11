# CSUSM Advanced Visual Analytics Assignment

The Github repo for the assignment can be found here:
[GitHub](https://github.com/CBJohnson30/CSUSM-OM621-Assignment)

## Video
Here is a quick video going through the whole project.

<video controls width="800" height="500" autoplay=False src="../assets/videos/om_621_video.mp4" title="Project Overview"></video>


## Project Overview
While completing my Master's in Supply Chain Analytics, I took a class called ‘Advanced Visual Analytics' taught by Dr Majid Karimi. This repository provides an overview of the class assignments. This project detailed how we can act as data consultants, analyzing a customer's transportation invoice data to help them gain better insights and forecast transportation costs for the next 12 months, enabling them to prepare a more accurate budget. A large component of the project was looking at how invoice delay could possibly effect creating a budget for transportation cost. We detailed how to pitch the project, clean data, create exploratory analysis plots, and create a presentation-style Power BI dashboard. 

### 3 Minute Story
Running a successful business is all about reacting to the unknown. While the future is never inevitable, what if that unknown becomes smaller?  With proper data collection, a good forecasting model will make the unknown smaller. This will allow you to better prepare for the unknown, and with real-time data, you can track your progress to see if you are heading into that unknown territory. With enough warning, the unknown can be planned for, so it becomes just another bump in the road, not an unexpected sinkhole. A proper forecasting model and a live dashboard will serve as that warning, so the unknown never really surprises anyone throughout the company. 

### Storyboard

![story board](..\assets\images\om_621_images\story_board.png)
 
## Notebook Overview
The exploratory_analysis.ipynb covers all EDA and visualization analyses of the data I was given. First, it goes through looking at NaNs and creating and understanding some key variables that we will use in the visualizations. Then it proceeds to create visualizations to understand the distribution of the ‘mode’ and ‘site’ variables.  Next, it looks at the invoice delay variable and compares it to ‘mode’ and ‘site. Last, it helps build an understanding of our data to allow me to gain insights into forecasting transportation costs. 

## Power BI Overview
The Power BI workbook contains 4 different dashboards. 
- Overview
    - Looking at how much transportation costs align with each transportation mode. With the total invoice amount and the average delay by city. 
- Delay Distribution
    - Understanding the delay statistics by Transportation Mode. 
- Breakdown by Mode
    - Understanding individual transportation mode statistics and trends. 
- Forecast
    - Looking at a 12-month forecast for transportation cost.


## Takeaways and Findings
- Given the heavy seasonality in transportation costs, a forecasting model could provide an accurate forecast for the coming year. 
- Less than Container load and container load have the most extensive invoice delays. The business should work with its logistics partners to identify how they can reduce invoice delays. 
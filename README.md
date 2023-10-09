<center>

# Aviation Safety Data Analysis #
    
</center>

![image.png](attachment:image.png)


## Task ##
- Task

Your company is expanding into new industries to diversify its portfolio. Specifically, they are interested in purchasing and operating airplanes for commercial and private enterprises, but do not know anything about the potential risks of aircraft. You are charged with determining which aircraft are the lowest risk for the company to start this new business endeavor. You must then translate your findings into actionable insights that the head of the new aviation division can use to help decide which aircraft to purchase.

## Bottom Line ##
We will be looking for the safest personal aircraft with a popular reputation as well as a "home base" for the start of the company. Find a national location that is safe while having a high demand for personal aircraft.

## Data Understanding ##
This project uses data from the National Transportation Safety Board that includes aviation accident data from 1962 to 2023 about civil aviation accidents and selected incidents within the United States. With that, we can make a national analysis of the most common makes of personal aircraft within the 21st century, then discover which can be the safest for the consumer. 
Filtering through the data and finding a location associated to a history of minimal accidents. Some outside research maybe necessary.

## Method ##

First things first, we secure the main dataframe by creating a copy. Then filter our data by date, country, location, type of aircraft, type of flight and investigation. Filtered the year to 2012 to current day and location to only show by state.
Then dropped a column with dupliate information(Injury.Severity) and created a list of unneeded columns to drop. Only had 1 null value in 2 columns so we dropped the null rows.
After that we looked at the "Make" column and noticed duplicate information as well so we consolidated those names.
Review what make and model has the lowest injuries attributed to them.

## Results ##

- We graphed the the top 5 states with most injuries.

state_accidents = df_copy.groupby("State")["Accidents"].count()

sorted_states = state_accidents.sort_values(ascending = False)

top_5 = sorted_states.head(5)


plt.bar(top_5.index, top_5.values)

plt.xlabel("State")
plt.ylabel("Accidents")
plt.title("States with Highest Accidents")

plt.show()

Seeing that the top states CA, TX and FL.

- Then graphed to see what type of injury was most common from accidents.

injuries = df_copy[["Fatal.Injuries", "Serious.Injuries", "Minor.Injuries"]].sum()

labels = ["Fatal Injuries", "Serious Injuries", "Minor Injuries"]
values = injuries.values

plt.bar(labels, values) 
plt.xlabel("Injury Type")
plt.ylabel("Number of Injuries")
plt.title("Number of Injuries in Accidents")
plt.show()

Unfortunately, fatal is the most common type of injury from private airplane accidents.

- Finally, graphed to see what make of airplane was responsible for the most amount of injuries. Excluding uninjuried.

filtered_df = df_copy[df_copy['Uninjured'] == 0] 
top_makes = filtered_df['Make'].value_counts().head(5)

plt.bar(top_makes.index, top_makes.values)
plt.xlabel('Makes')
plt.ylabel('Number of Injuries')
plt.title('Top 5 Makes and Injuries (excluding Uninjured)')
plt.xticks(rotation=45)
plt.show()

Mooney and Cirrus and considerably lower than their counterparts.

## Recommendation - Saftey, Popularity  and Cost ##

Outside research shows that although Alaska is one of the states with higher injuries attributed to accidents it also is one of the states with the most private airstrips and personal hours flown. Private aircrafts is one of the most common ways of travel in Alaska. 

After cleaning and filtering our data we see that Mooney and Cirrus are some of the safer private aircrafts. Outside research shows that Mooney is more cost effective than Cirrus by 20% and Mooney has been in the aviation business for almost 100 years.

From the results of our data and outside research we believe the best recommondation based on safety, popularity and cost is

## Alaska as home base and the Mooney M20 for our personal aircraft ##


## Future Discoveries ##

- Expansion: international and/or commercial
- Aircraft varieties: helicopters and/ or airbusses

## For more information ##

Please review full analysis in our [Jupyter Notebook](https://github.com/ginaguerin/Aviation-Saftey-Analysis/blob/master/Index.ipynb) or our [Presentation](https://github.com/ginaguerin/Aviation-Saftey-Analysis/blob/master/Final.Slides.pptx)


## Repository ##

- This is the ReadME.md
- This is the [Index.ipynd](https://github.com/ginaguerin/Aviation-Saftey-Analysis/blob/master/Index.ipynb) Showing the breakdown of our anaylsis and the code.
This is the [Slides](https://github.com/ginaguerin/Aviation-Saftey-Analysis/blob/master/Final.Slides.pptx) showing the presentation for our analysis.
- This is the [Data](https://github.com/ginaguerin/Aviation-Saftey-Analysis/tree/master/data) we worked with as well as our filtered data.
- This is the [Tableau Dashboard](https://public.tableau.com/app/profile/gina.guerihn/viz/PrivateAviationAnalysis/Dashboard1) we created from our filtered data.
- This is the [Images]() Showing the graphs and tableau graphs from our analysis.



## Outside Research ##

- [Rob Report](https://robbreport.com/motors/aviation/top-private-aviation-states-eg17-2753874/)

- [General Aviation News](https://generalaviationnews.com/2017/10/24/what-states-top-the-charts-for-general-aviation/#:~:text=A%20new%20post%20on%20The,active%20states%20for%20general%20aviation.)

- [Plane and Pilot Magazine](https://www.planeandpilotmag.com/article/10-cheapest-birds-in-the-sky/)

- [Fly Aeolus](https://flyaeolus.com/blog/buying-a-small-airplanes-5-cheap-airplanes-that-offer-quality/)









https://www.planeandpilotmag.com/article/10-cheapest-birds-in-the-sky/


https://flyaeolus.com/blog/buying-a-small-airplanes-5-cheap-airplanes-that-offer-quality/
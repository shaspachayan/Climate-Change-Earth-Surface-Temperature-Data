

Introduction

Welcome to Climate Data Analysis project, where I explore historical temperature data to uncover trends, fluctuations, and regional disparities over centuries. This dataset presents a treasure trove of insights into Earth's changing climate, yet it comes with complexities, including shifts in data collection methodologies and potential biases.

Data Sources

- Early Temperature Records: Technicians collected temperature data using mercury thermometers, where even minor variations in visit times could impact measurements.

- 1940s Airport Relocations: The construction of airports in the 1940s prompted the relocation of many weather stations, potentially introducing discontinuities in the data.

- 1980s Electronic Thermometers: In the 1980s, the introduction of electronic thermometers raised concerns about a cooling bias.

To navigate these challenges, several organizations compile climate trend data. Notably, we draw data from Berkeley Earth, affiliated with the Lawrence Berkeley National Laboratory. Their comprehensive dataset combines 1.6 billion temperature records from 16 pre-existing archives. Berkeley Earth provides well-curated data, enabling us to explore intriguing subsets (e.g., by country). Importantly, they generously share both the source data and the code used for data transformations. Furthermore, their methodology accommodates shorter time series, reducing data loss.

Data Source: Berkeley Earth Climate Data on Kaggle (https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data/data)

Data Preparation and Cleaning

1. Importing the Data

import pandas as pd
df = pd.read_csv("GlobalLandTemperaturesByCity.csv")

2. Understanding the Dataset's Dimensions

shape = df.shape

3. Exploring Columns and Datatypes

columns = df.columns

Data Cleaning and Preprocessing

- We address data quality by removing NaN values from the AverageTemperature column.
- We streamline the dataset by discarding columns AverageTemperatureUncertainty and Longitude.
- We enhance temporal analysis by converting the Date column from an object type to datetime and deriving the Year and Month columns.

Exploratory Analysis and Visualization

Top 5 Countries by City Count

- Our dataset spans 159 countries.
- We spotlight the top 5 countries with the most cities.

# Visualizing temperature trends for the top 5 countries with the most cities
sns.lineplot(x='Year', y='AverageTemperature', hue='Country', data=filtered_data1)

Countries with Fewer than 10 Cities

- A total of 111 countries feature fewer than 10 cities in the dataset.

Average Yearly Temperature

- We compute the average yearly temperature and visualize it for the top 5 countries.

average_yearly_temperature = df.groupby(['Country', 'Year'])['AverageTemperature'].mean()

Posing Questions

To glean valuable insights, we pose and address the following questions:

1. What is the relationship between temperature and time?
   
2. How does temperature fluctuate over time?
   
3. Where can we find the locations with the highest and lowest temperatures?
   
4. What are the anticipated temperature trends in the future?

Conclusion

In conclusion, our Climate Data Analysis project delves into historical temperature data, unearthing profound insights into temperature trends, regional nuances, and beyond. Understanding the interplay of temperature and time is pivotal for mitigating the impacts of climate change. Climate models serve as instruments for projecting future temperature trends, underscoring the importance of proactive measures in an ever-warming world.

Helpful Resources

- A Overview of Matplotlib (https://python-graph-gallery.com/matplotlib/)
- An Introduction to Seaborn (https://seaborn.pydata.org/tutorial/introduction.html)

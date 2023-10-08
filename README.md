


# Climate Data Analysis: Uncovering Historical Temperature Trends

## Introduction

This project delves into the intricate world of historical temperature data analysis. Our dataset provides a wealth of information about temperature trends, fluctuations, and regional disparities over centuries. However, the data comes with inherent complexities, including shifts in data collection methodologies and potential biases.

## Data Sources

- Early temperature data was painstakingly collected by technicians using mercury thermometers. Even minor variations in visit times could impact measurements.
- In the 1940s, the construction of airports prompted the relocation of many weather stations, potentially introducing discontinuities.
- In the 1980s, the introduction of electronic thermometers raised concerns about a cooling bias.

To address these complexities, numerous organizations compile climate trend data. Notably, NOAA’s MLOST, NASA’s GISTEMP, and the UK’s HadCrut are the most frequently referenced land and ocean temperature datasets.

For this analysis, we leverage data from Berkeley Earth, associated with the Lawrence Berkeley National Laboratory. This comprehensive dataset amalgamates 1.6 billion temperature records from 16 pre-existing archives. It is thoughtfully curated, facilitating the extraction of intriguing subsets (e.g., by country). Berkeley Earth also generously shares both the source data and the code used for data transformations. Moreover, their methodology accommodates shorter time series, reducing data loss.

## Data Preparation and Cleaning

### 1. Importing the Data

```python
import pandas as pd
df = pd.read_csv("GlobalLandTemperaturesByCity.csv")
```

### 2. Understanding the Dataset's Dimensions

```python
shape = df.shape
```

### 3. Exploring Columns and Datatypes

```python
columns = df.columns
```

### Data Cleaning and Preprocessing

- Removing NaN values from the `AverageTemperature` column.
- Discarding columns `AverageTemperatureUncertainty` and `Longitude`.
- Converting the `Date` column from an object type to datetime and deriving the `Year` and `Month` columns.

## Exploratory Analysis and Visualization

### Top 5 Countries by City Count

- The dataset encompasses 159 countries.
- We spotlight the top 5 countries with the most cities.

```python
# Visualizing temperature trends for the top 5 countries with the most cities
sns.lineplot(x='Year', y='AverageTemperature', hue='Country', data=filtered_data1)
```

### Countries with Fewer than 10 Cities

- A total of 111 countries feature fewer than 10 cities in the dataset.

### Average Yearly Temperature

- Computation of the average yearly temperature and visualization for the top 5 countries.

```python
average_yearly_temperature = df.groupby(['Country', 'Year'])['AverageTemperature'].mean()
```

## Posing Questions

To glean valuable insights, we pose and address the following questions:

1. What is the relationship between temperature and time?
2. How does temperature fluctuate over time?
3. Where can we find the locations with the highest and lowest temperatures?
4. What are the anticipated temperature trends in the future?

## Conclusion

In conclusion, this project delves into the historical temperature data, providing profound insights into temperature trends, regional nuances, and beyond. Understanding the interplay of temperature and time is pivotal for mitigating the impacts of climate change. Climate models serve as instruments for projecting future temperature trends, underscoring the importance of proactive measures in an ever-warming world.

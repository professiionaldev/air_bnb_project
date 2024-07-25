Skip to main content
Project Type - EDA
Contribution - Individual-Ashvini Gabhane
Project Name - AirBnb Bookings Analysis Exploratory Data Analysis
Project Summary -
download.jpg

The Airbnb Data Analysis project focuses on Airbnb's extensive dataset since 2008, covering 48,895 observations in 16 columns. It aims to gain insights into user behavior, enhance security, inform business decisions, refine marketing strategies, improve the user experience, and identify regional trends for global expansion. This project harnesses data to benefit Airbnb and enrich the experiences of millions of travelers and hosts.

GitHub Link -
https://github.com/professiionaldev/air_bnb_project

Problem Statement

[ ]
Write Problem Statement Here.

BUSINESS PROBLEM OVERVIEW : The Airbnb dataset presents a diverse array of business challenges. These include optimizing pricing, forecasting demand, improving customer experiences, detecting fraud, expanding into new markets, retaining hosts, managing inventory, analyzing competition, ensuring data security and privacy, and promoting sustainability. Addressing these challenges through data-driven insights is vital for enhancing Airbnb's operational efficiency, increasing revenue, and delivering a superior experience to hosts and guests.

Define Your Business Objective?
The business objective of this Airbnb booking data analysis is to optimize operations, enhance customer experiences, ensure regulatory compliance, prevent fraud, expand into new markets, and promote sustainability, all through data-driven insights.

General Guidelines : -
Well-structured, formatted, and commented code is required.

Exception Handling, Production Grade Code & Deployment Ready Code will be a plus. Those students will be awarded some additional credits.

The additional credits will have advantages over other students during Star Student selection.

    [ Note: - Deployment Ready Code is defined as, the whole .ipynb notebook should be executable in one go
              without a single error logged. ]
Each and every logic should have proper comments.

You may add as many number of charts you want. Make Sure for each and every chart the following format should be answered.

# Chart visualization code
Why did you pick the specific chart?
What is/are the insight(s) found from the chart?
Will the gained insights help creating a positive business impact? Are there any insights that lead to negative growth? Justify with specific reason.
You have to create at least 20 logical & meaningful charts having important insights.
[ Hints : - Do the Vizualization in a structured way while following "UBM" Rule.

U - Univariate Analysis,

B - Bivariate Analysis (Numerical - Categorical, Numerical - Numerical, Categorical - Categorical)

M - Multivariate Analysis ]

Let's Begin !
1. Know Your Data
Import Libraries

[ ]
# Import Libraries
import pandas as pd

import numpy as np
from numpy import math

import matplotlib.pyplot as plt

import seaborn as sns
Dataset Loading

[ ]
# Load Dataset
from google.colab import drive
drive.mount('/content/drive')


[ ]
dataset = pd.read_csv('/content/drive/MyDrive/Airbnb NYC 2019.csv')
dataset


[ ]

# Load Dataset
file_path = '/content/drive/MyDrive/Airbnb NYC 2019.csv'
ps_df=pd.read_csv(file_path)

[ ]
data_path ='/content/drive/MyDrive/Airbnb NYC 2019.csv'

[ ]
df = pd.read_csv(data_path)

Dataset First View

[ ]
# Dataset First Look
dataset.head()
Dataset Rows & Columns count

[ ]
# Dataset Rows & Columns count
dataset.shape
Dataset Information

[ ]
# Dataset Info
dataset.info()
Duplicate Values

[ ]
# Dataset Duplicate Value Count
len(dataset[dataset.duplicated()])
Missing Values/Null Values

[ ]
# Missing Values/Null Values Count
print(dataset.isnull().sum())

[ ]
# Visualizing the missing values
sns.heatmap(dataset.isnull(), cbar=False , cmap='viridis')
What did you know about your dataset?
The Airbnb dataset, consisting of around 48,895 observations and 16 columns, is a valuable resource for data analysis. It contains a mix of both categorical and numeric data. This dataset helps them make informed decisions regarding security, business strategies, customer and host behavior, and platform performance. Through this data, I understand the gains insights that guide marketing efforts, the development of new services, and more. It is a rich source of information for understanding and optimizing the Airbnb experience for both guests and hosts, contributing to the global recognition of Airbnb as a unique and personalized travel service since 2008.

2. Understanding Your Variables

[ ]
# Dataset Columns

list(dataset.columns)

[ ]
# Dataset Describe
dataset.describe(include = 'all')
Variables Description
id: Unique listing identifier.

name: Title or name of the listing.

host_id: Unique identifier of the host.

host_name: Name of the host.

neighbourhood_group: Larger geographic area or region within a city.

neighbourhood: Specific neighborhood or locality.

latitude: Geographic latitude coordinate of the listing.

longitude: Geographic longitude coordinate of the listing.

room_type: Type of room offered (e.g., entire home, private room, shared room).

price: Price of the listing per night.

minimum_nights: Minimum number of nights a guest must book.

number_of_reviews: Total count of reviews for the listing.

last_review: Date of the most recent review.

reviews_per_month: Average number of reviews received per month.

calculated_host_listings_count: Count of listings owned by the host.

availability_365: Number of available days for booking in a year.

Check Unique Values for each variable.

[ ]
# Check Unique Values for each variable.
unique_values = dataset.nunique()
print(unique_values)

3. Data Wrangling
Data Wrangling Code

[ ]
# Write your code to make your dataset analysis ready.
cat_col = dataset.select_dtypes(include = 'object').columns
print(list(cat_col))

[ ]
 #TO FIND HOW MANY NUMERICAL COLUMN PRESENT IN THIS DATASET

num_col = dataset.select_dtypes(exclude = 'object').columns
print(list(num_col))

[ ]

# REMOVE COLUMN THAT IS NOT USEFUL  OF MY OUTPUT AND ALSO CONTAINING MISSING VALUES

data = dataset.drop(['last_review'] , axis = 1)


[ ]

# TO SEE COLUMN IS REMOVE OR NOT

data.shape

[ ]

# TO CHECK HOW MANY MISSING VALUES PRESENT IN EACH COLUMN

print(data.isnull().sum())

[ ]

# TO FILL MISSING VALUES

data.fillna({'name' :  'not present' ,  'host_name' : 'absent' ,'reviews_per_month' : 0  }, inplace = True)

[ ]

# to check
data.isnull().sum()

[ ]
discontinued_listing = data[(data['price']==0 ) & (data['availability_365']==0)]
discontinued_listing

[ ]
# excludue data

data = data.loc[data['price']>0]
data
What all manipulations have you done and insights you found?
I perform Handling Missing Data ,Cleaning Data ,Data Transformation ,Data Filtering ,Categorical Variables.

and insights i found -:

Room Type: Identify the most commonly offered room type (e.g., "Entire home," "Private room," "Shared room") to understand host preferences.

Average Price per Room Type: Calculate the average price for each room type to see which type tends to be more expensive or affordable.

Average Number of Reviews: Determine the average number of reviews for listings, which can provide insights into the popularity of accommodations.

Seasonal Price Trends: Analyze how prices vary across different seasons to identify peak and off-peak periods for bookings.

Top Hosts by Listing Count: Find out which hosts have the most listings, potentially indicating successful hosts.

4. Data Vizualization, Storytelling & Experimenting with charts : Understand the relationships between variables
Chart - 1

[ ]
# Chart - 1 visualization code
plt.hist(dataset['price'], bins = 20)
plt.xlabel('Price')
plt.ylabel('Frequency')
plt.title('Histogram of price')
plt.show()

1. Why did you pick the specific chart?
To visualize the distribution of prices.

2. What is/are the insight(s) found from the chart?
Most prices are concentrated at lower values, with a few outliers at higher prices.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Offers insights for competitive pricing.

Negative Impact:High-priced listings may have lower demand.

Chart - 2

[ ]
# Chart - 2 visualization code
sns.countplot(data = dataset , x = 'room_type')
plt.xlabel('Room Type')
plt.ylabel('Count')
plt.title('Distribution of Room Type')
plt.xticks(rotation=45)
plt.show()
1. Why did you pick the specific chart?
To visualize room type preferences.

2. What is/are the insight(s) found from the chart?
Most listings are for Entire home/apartment, offering variety for travelers.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Diverse offerings cater to different customer needs.

Negative Impact: If one room type dominates, it may limit customer choices.

Chart - 3

[ ]
# Chart - 3 visualization code
plt.scatter(dataset['longitude'],dataset['latitude'], alpha=0.5, c=dataset['price'], cmap='viridis')
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.title('Geographic Distribution of Listing')
plt.colorbar(label ='Price')
plt.show()
1. Why did you pick the specific chart?
To explore geographic distribution.

2. What is/are the insight(s) found from the chart?
Listings are concentrated in specific areas, potentially due to popular tourist destinations.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact:Focusing marketing efforts in these areas.

Negative Impact: Limited diversification of listings in other areas.

Chart - 4

[ ]
# Chart - 4 visualization code : Line Plot of Reviews per Month
dataset['last_review'] = pd.to_datetime(dataset['last_review'])
reviews_over_time = dataset.groupby('last_review').agg({'reviews_per_month': 'mean'}).reset_index()
sns.lineplot(data=reviews_over_time, x='last_review', y='reviews_per_month')
plt.xlabel('Date')
plt.ylabel('Reviews per Month')
plt.title('Trend in Reviews per Month')
plt.show()

1. Why did you pick the specific chart?
To understand the trend in reviews.

2. What is/are the insight(s) found from the chart?
Reviews fluctuate over time, suggesting varying customer experiences.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Identifying peak review periods.

Negative Impact: Consistency issues may lead to negative reviews.

Chart - 5

[ ]
# Chart - 8 visualization code  : Bar Chart of Minimum Nights
sns.countplot(data = dataset ,x = 'minimum_nights')
plt.xlabel('Minimum Nights')
plt.ylabel('Count')
plt.title('Distribution of Minimum Nights')
plt.xticks(rotation=45)
plt.show()

1. Why did you pick the specific chart?
To visualize minimum stay requirements.

2. What is/are the insight(s) found from the chart?
Most listings have short minimum stays, making them flexible for travelers.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Attracts travelers looking for shorter stays.

Negative Impact: Longer minimum nights may limit bookings.

Chart - 6

[ ]
# Chart - 6 visualization code : Scatter Plot of Price vs. Number of Reviews
plt.scatter(dataset['number_of_reviews'], dataset['price'],alpha=0.5)
plt.xlabel('Number Of Reviews')
plt.ylabel('Price')
plt.title('Price vs. Number of reviews')
plt.show()
1. Why did you pick the specific chart?
To explore the relationship between price and reviews.

2. What is/are the insight(s) found from the chart?
No strong linear relationship between price and reviews.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Allows flexibility in pricing.

Negative Impact: Price adjustments may not directly impact review quantity.

Chart - 7

[ ]
# Chart - 7 visualization code :Bar Chart of Neighbourhood Group
sns.countplot(data = dataset , x= 'neighbourhood_group')
plt.xlabel('Neighbourhood_group')
plt.ylabel('Count')
plt.title('Distribution of Listing By Neighbourhood Group')
plt.xticks(rotation=45)
plt.show()

1. Why did you pick the specific chart?
To show the distribution by neighborhood group.

2. What is/are the insight(s) found from the chart?
Manhattan and Brooklyn have the most listings, indicating strong markets.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Targeted marketing in high-demand areas.

Negative Impact: Neglecting opportunities in other neighborhoods.

Chart - 8

[ ]

# Chart - 8 visualization code   :Box Plot of Price by Room Type:
sns.boxplot(data = dataset , x ='room_type' , y ='price')
plt.xlabel('Room type')
plt.ylabel('Price')
plt.title('Price Distribution by Room Type')
plt.xticks(rotation = 45)
plt.show()
1. Why did you pick the specific chart?
To compare price distributions for different room types.

2. What is/are the insight(s) found from the chart?
Entire home/apartment listings have higher prices on average.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact:Higher revenue potential for certain room types.

Negative Impact: Limited budget options if most listings are high-priced.

Chart - 9

[ ]
# Chart - 9 visualization code  Bar Chart of Availability 365
sns.countplot(data = dataset , x='availability_365')
plt.xlabel('Availability 365')
plt.ylabel('Count')
plt.title('Distribution of Availability 365')
plt.xticks(rotation=45)
plt.show()
1. Why did you pick the specific chart?
To show availability throughout the year.

2. What is/are the insight(s) found from the chart?
Most listings have high availability, appealing to travelers.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Attracts travelers with flexible booking options.

Negative Impact: Over-availability may lead to lower demand.

Chart - 10

[ ]
# Chart -10 visualization code : Box Plot of Price by Neighbourhood Group
sns.boxplot(data = dataset , x='neighbourhood_group', y='price')
plt.xlabel('Neighbourhood_group')
plt.ylabel('Price')
plt.title('Price Distribution by Neighbourhood Group')
plt.xticks(rotation = 45)
plt.show()
1. Why did you pick the specific chart?
To compare price distributions across neighborhood groups.

2. What is/are the insight(s) found from the chart?
Manhattan has higher prices, potentially due to its tourist appeal.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact:Leveraging higher prices in prime areas.

Negative Impact: Limited affordability options.

Chart - 11

[ ]
# Chart - 11 visualization code : Line Plot of Price Over Time
price_over_time = dataset.groupby('last_review').agg({'price': 'mean'}).reset_index()
sns.lineplot(data=price_over_time, x='last_review', y='price')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Trend in Listing Prices Over Time')
plt.show()
1. Why did you pick the specific chart?
To understand price trends.

2. What is/are the insight(s) found from the chart?
Prices fluctuate over time, indicating potential seasonality.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Adjust pricing to demand fluctuations.

Negative Impact: Inconsistent pricing may confuse customers.

Chart - 12

[ ]
# Chart - 12 visualization code  : Bar Chart of Calculated Host Listings Count
sns.countplot(data = dataset , x = 'calculated_host_listings_count')
plt.xlabel('Host Listing Count')
plt.ylabel('Count')
plt.title('Distribution of Host Listings Count')
plt.xticks(rotation = 90)
plt.show()
1. Why did you pick the specific chart?
To visualize host activity

2. What is/are the insight(s) found from the chart?
Most hosts have a few listings, suggesting opportunities for growth.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Encouraging hosts to expand their offerings.

Negative Impact: May lead to increased competition among hosts.

Chart - 13

[ ]
# Chart - 13 visualization code : Bar Chart of Neighbourhood (Top Neighbourhoods):
top_hosts = dataset['host_name'].value_counts().head(10)
sns.barplot(x=top_hosts.index, y=top_hosts.values)
plt.xlabel('Host Name')
plt.ylabel('Number of Listings')
plt.title('Top Hosts by Number of Listings')
plt.xticks(rotation=45)
plt.show()

1. Why did you pick the specific chart?
To identify popular neighborhoods.

2. What is/are the insight(s) found from the chart?
Promoting or expanding in these neighborhoods can attract more customers.

3. Will the gained insights help creating a positive business impact?
Are there any insights that lead to negative growth? Justify with specific reason.

Positive Impact: Identifying top neighborhoods can boost revenue and bookings by targeting high-demand areas.

Negative Impact:Failing to act on these insights can lead to missed growth opportunities and lower business performance.

Chart - 14 - Correlation Heatmap

[ ]
# Correlation Heatmap visualization code
corr_matrix = dataset.corr()
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()


1. Why did you pick the specific chart?
To explore the correlation between numerical variables.

2. What is/are the insight(s) found from the chart?
There may be some weak correlations between variables.

Chart - 15 - Pair Plot

[ ]
#  Pair Plot visualization code
numerical_columns = ['price', 'minimum_nights', 'number_of_reviews', 'reviews_per_month', 'calculated_host_listings_count', 'availability_365']
sns.pairplot(data=dataset[numerical_columns])
plt.show()
1. Why did you pick the specific chart?
I chose a pair plot to visualize relationships and interactions between multiple numerical variables because it provides a comprehensive view of potential correlations and patterns within the data.

2. What is/are the insight(s) found from the chart?
The pair plot suggests most variables are independent with no strong linear correlation, but it highlights a potential link between "number of reviews" and "reviews per month," implying more monthly reviews may result in a higher total number of reviews.

5. Solution to Business Objective
What do you suggest the client to achieve Business Objective ?
Explain Briefly.

To achieve the business objective over Airbnb analysis, I recommend the client:

Focus on top-performing neighborhoods for property investment and marketing efforts.

Optimize pricing strategies based on trends observed in the data.

Maintain consistent service quality to enhance customer satisfaction and positive reviews.

Diversify room type offerings to cater to a broader range of travelers.

Consider seasonal pricing adjustments to maximize revenue during peak periods.

Encourage hosts to expand their listings where opportunities exist.

Continuously monitor and act on data-driven insights to stay competitive and responsive to changing market conditions.

Conclusion
1)Most prices are concentrated at lower values, with a few outliers at higher prices.

2)Most listings are for Entire home/apartment, offering variety for travelers.

3)Listings are concentrated in specific areas, potentially due to popular tourist destinations.

4)Entire home/apartment listings have higher prices on average.

5)Manhattan and Brooklyn have the most listings, indicating strong markets.

6)No strong linear relationship between price and reviews.

7)Most listings have short minimum stays, making them flexible for travelers.

8)Manhattan has higher prices, potentially due to its tourist appeal.

9)Prices fluctuate over time, indicating potential seasonality.

10)Most hosts have a few listings, suggesting opportunities for growth.

In conclusion, the Airbnb dataset analysis suggests that focusing on prime neighborhoods, optimizing pricing, maintaining quality, diversifying offerings, and staying responsive to data-driven insights are key strategies for success in the short-term rental business.

In addition, the dataset reveals a diverse range of listings, indicating opportunities to cater to various customer preferences. It also underscores the importance of consistent service quality and adaptability to meet changing market demands and seasonal variations for successful operations in the Airbnb marketplace.

Hurrah! You have successfully completed your EDA Capstone Project !!!
Colab paid products - Cancel contracts here

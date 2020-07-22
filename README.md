# box-office-project

## Background

Movie provides us lots of fun, and US movie industry is absolutely one of the giants in this field. Every year billions of money is invested in movie production and the revenues are also thrilling. In this project, I’d like to use the data scraped from the famous website: box office mojo to understand what factors impact movie revenue the most.

The analysis result is only based on the data that can be extracted from box office mojo free data source.

## Installation

This project uses beautifulsoup and mysql-connector.

`pip install beautifulsoup4`

`pip install mysql-connector-python`

## Project Summarize

### 1. Data preparation

The original data only focus on “Yearly gross” for “Domestic” movie from 2015 to 2019, as the goal of this project is finding the variables that impact the overall revenue achievement of each movie rather than inspecting the daily or weekly revenue trend.

The “data extraction” notebook include the function I wrote to complete this task.

### 2. ETL

- Scraping data from box office web pages
- Clean and organize data in paticular sequence
- Save data to AWS MySql server

### 3. Data visualization

- Distribution of “Total_value” proves the long tail effect in movie industry.

![image](https://github.com/alice-heqi/box-office-project/blob/master/images/tlt.png)

- Scatter plots indicate that “Widest_release_theaters” related to “Total_revenue”.

Example:

![image](https://github.com/alice-heqi/box-office-project/blob/master/images/wide.png)

- Bar charts show around 10% companies occupied more than 90% industry revenue, the most popular movie genres and which weekday and month are the hot time for movie release.

Example:

![image](https://github.com/alice-heqi/box-office-project/blob/master/images/co-tlt.png)

### 4. Lasso

Three variables are selected by Lasso. 

`from sklearn.feature_selection import SelectFromModel`

`selected_feat` -> Index(['Duration_min', 'In_release_days', 'Widest_release_theaters'], dtype='object')'

### 5. Conclusion 

- Further checking the three selected variables, the results indicate that “in_release_days” and “Duriation_min” correlated to “genre”. The most popular genres’ mean value of these two variables also have the highest frequency in their distribution. That is, the effect of  “In_release_days” and “Duration_min” represent the effect of “genre”. 

---plots of "genre" and "Duration"

![image](https://github.com/alice-heqi/box-office-project/blob/master/images/gen-du.png)
![image](https://github.com/alice-heqi/box-office-project/blob/master/images/gen-du2.png)

---plots of "genre" and "in release days"

![image](https://github.com/alice-heqi/box-office-project/blob/master/images/gen-in.png)
![image](https://github.com/alice-heqi/box-office-project/blob/master/images/gen-in2.png)

- “Widest release theaters” correlated to “Company”. The larger the company is, the widest theaters that movie can be released. In other words, the larger the company is, the wider the movie can be broadcasted, and so the higher the movie revenue will be.

![image](https://github.com/alice-heqi/box-office-project/blob/master/images/co-wide.png)



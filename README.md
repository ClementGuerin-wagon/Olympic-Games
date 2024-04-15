# Olympic Games

### **PROJECT REPORT 🔍**

**Report Outline**

1. Introduction
2. Project Objectives
3. Data Collection and Description
4. Data Exploration and Cleaning
5. Research Questions and Exploratory Analysis
6. Predictive Analysis
7. Key Findings and Conclusion

**Tools : SQL (BigQuery, Python (skicit-learn), Looker Studio**
---
1. **Introduction**

The Olympic Games are a major global event that brings together athletes from various countries competing in a variety of sports disciplines. This project aims to explore and analyze historical data from the Summer and Winter Olympic Games, covering the period from 1896 to 2022. We conducted this project as a team and presented our findings at the Demo Day on 15/03 in Nantes.

2. **Project Objectives**

The main objective of this project was to apply all the knowledge and tools we acquired during the 9-week bootcamp. We chose the theme of the Olympic Games because, in addition to being a current topic, it offered a wealth of data for drawing relevant insights. Given the period covered, our idea was also to perform predictive analysis, particularly on the performance of France as the host country this summer.

3. **Data Collection and Description**

We searched for and selected the dataset "Olympic Summer & Winter Games, 1896-2022" on Kaggle. This dataset includes information about athletes, medals, results, and host countries of the Games, and consists of the following 4 tables:
    - olympic_athletes.csv: Personal information about athletes (name, discipline, nationality, etc.)
    - olympic_medals.csv: General information about medalists (Athlete or Team).
    - olympic_hosts.csv: Hosts (year, city, country, etc.).
    - olympic_results.csv: General information about results (Athlete or Team).
*Note that the "Results" table only contains data on the finalists of each event (qualification rounds are not included)*

**4. Data Exploration and Cleaning**

We then examined the structure of each table. We quickly discarded the olympic_athletes.csv file as it was unusable in its current state. Instead, we generated a new file through web scraping, containing the list of finalist athletes with their physical characteristics (weight, height, age, gender), their discipline type, and the type of medal obtained. Subsequently, for each table, we used Python to analyze the data distribution, identify missing values, and duplicates using functions such as ".info," ".isnull," or ".drop_duplicates." For null values, we proceeded as follows:

- For numerical data, we replaced the values with the mean.
- When more than 60% of the values were null in a column, we deleted the column.
- For categorical data, we handled null values on a case-by-case basis. Either by replacing the null value with the most frequent value or with another value. For example, in the Athletes table, the "Medals" column contained values such as "Gold," "Silver," "Bronze," or "null." We replaced the "null" values with "No medal."



**5. Research Questions and Exploratory Analysis**

Once our tables were cleaned, we brainstormed potential research questions. We listed all our ideas for each table in a shared Notion page. Here are some examples:

- Hosts: Do host countries tend to have better performances?
- Medals: What is the distribution of medals by discipline and by country?
- Results: Are there differences between the results of Summer and Winter Games?
- Athletes: What is the distribution of athletes by gender, height, weight, nationality?

With this list, we established a presentation plan in 3 main parts:

- Overview and temporal evolution (number of participating countries, disciplines, summer-winter comparison).
- International performance (top 10 medal-winning countries, correlation between hosting and performance).
- Focus on France and prediction.

From there, we attempted to answer each question by executing SQL queries in BigQuery, then connecting the new generated tables in Looker Studio to obtain initial visualizations. Sometimes, we obtained the expected answers directly, while other times, we had to create new features such as seasonality (the values "Summer" and "Winter" did not exist in the original datasets) or add the names and continents of host countries (we only had the city). We went through many successive iterations to select the most relevant insights and discard the others. To choose the best graphical representation, we drew inspiration from the Data to Viz website.

**6. Predictive Analysis**
Having identified that hosting the Games had a significant impact on the host country's performance, we naturally thought of predicting the number of medals France could obtain this summer. To do this, we used the Scikit-learn library in Python and a linear regression model. After training our model, we obtained a value of 32.5 medals, which may seem low at first. This figure needs to be reassessed considering that our dataset contained values for both the Summer and Winter Games. Therefore, we revised this figure to 55 medals (the summer/winter ratio being 85%). We also obtained a Mean Absolute Error of 14, which means that France could obtain between 41 and 69 medals. This range may seem wide, but it remains consistent with the forecasts of the international press, which are between 52 and 63 medals on average.


**7. Key Findings and Conclusion**
Our work has been rich in insights. It confirmed insights we already suspected:

- Games with increasingly more disciplines, countries, and participating athletes, and therefore, more medals.
- The leading nations in terms of medals are as expected: the USA, Russia, Germany...
- Hosting the Games has a very strong impact on performance (including for France).
We also had some surprises:
- Countries like Pakistan, Norway, or Jamaica have the best "conversion rates" (they send fewer athletes but win more medals).
- In France, judo is only the 9th sport in terms of participants but ranks 1st in terms of medals.
- Even though it outperforms, France will not beat its medal record. It will indeed be difficult to surpass the 103 medals obtained in 1900.
In conclusion, working on the theme of the Olympic Games has been a very enriching experience. It is an eminently "data-friendly" subject but can sometimes seem overwhelming. In this sense, it would be wise to target the analysis on very specific questions, or even to cross-reference them with other external data (such as GDP/per capita), especially on Machine Learning issues.

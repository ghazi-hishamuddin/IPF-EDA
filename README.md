# 🏋️ International Powerlifting Federation EDA

## Introduction

<p align="justify">
In recent times, powerlifting has gained immense popularity, especially after being featured in various mainstream media and events. Interestingly, I too found myself roped into the world of powerlifting, 
competing in two competitions in 2022. This personal involvement has not only fueled my passion for the sport but also provided me with a unique perspective on the challenges and intricacies of powerlifting!

Do take a look at the full analysis <a href='https://github.com/ghazi-hishamuddin/openpowerlifting_ipf_eda/blob/main/ipf-EDA-updated.ipynb'>here</a>! 
</p>

## Background

<p align="justify">
Driven by a curiosity to determine my own standards in this strength sport, this project was started to uncover patterns, trends, and insights about powerlifting. I wanted to also know whether my bodyweight is limiting me in getting stronger in this sport.
I delved into finding out whether bodyweight is truly a significant contributing factor to a lifter's overall performance and strength. Through visualizations and statistical analyses, key aspects are explored, and the analysis also spotlights specific athletes, examining their achievements and how they compare to others in their respective weight classes and the broader powerlifting community.
</p>


## Dataset

<p align="justify">
The dataset is obtained from the reputable <a href="https://openpowerlifting.gitlab.io/opl-csv/bulk-csv.html">OpenPowerlifting</a> project, 
consists of over 1.2 million competition records from the International Powerlifting Federation (IPF).
</p>

## Libraries Used
+ Pands
+ Matplotlib
+ NumPy
+ Scikit-learn

<hr>

# The Analysis

<b> 1. What are the most popular weight classes in IPF competitions? </b>

The most popular male weight classes are U83, and U93. While U63 is the most popular for females.

![image](https://github.com/ghazi-hishamuddin/openpowerlifting_ipf_eda/assets/142828521/d52f9fe5-4922-4729-b562-5dd5b4bf0a96)
<hr>

<b> 2. What is the distribution between male and female lifters? </b>

![image](https://github.com/ghazi-hishamuddin/openpowerlifting_ipf_eda/assets/142828521/d9259ce0-8ac5-4d4a-974a-75fe75a4aa83)
<hr>

<b> 3. How do we identify a lifter as a world-class lifter? </b>
``` python
# Creating new df with highest gl_score at the top
goodlift_df = df3.sort_values(by='gl_score', ascending=False)

# Locate the index of top_one_percent as that with the last lifter on the top 1%
top_one_percent = int(0.01 * goodlift_df.shape[0])
goodlift_df.iloc[top_one_percent]['gl_score']

''''
Output: 102.39
''''
```
I first took the top 1% to justify a lifter as elite and used Goodlift points to determine the strongest lifters in the dataset. You can find the full explaination in the origional ipynb file.

<hr>

<b> 4. Which countries breeds the highest number of World Class lifters? </b>

![image](https://github.com/ghazi-hishamuddin/openpowerlifting_ipf_eda/assets/142828521/9497f1b0-a1d6-4fb5-9914-4920b7588ba7)

USA seems to be miles ahead in the producing world class lifters. Let's take a look at the count of lifters in the dataset to understand this better.

``` python
'''' Output:

birth_country
Unknown    36688
USA        31845
Canada      4611
Russia      4227
England     3454
Name: name, dtype: int64

''''
```
It does seem like there is a significant amount of powerlifters born in the USA, which explains the huge discrepancy.

<hr>

<b> 5. What is the relationship between total weight lifted vs bodyweight? </b>

![image](https://github.com/ghazi-hishamuddin/openpowerlifting_ipf_eda/assets/142828521/9fc499eb-38cc-4df5-8a67-dcde6d5ca278)

R-squared value: 0.2887657518367255

<p align="justify">
The scatter plot shows a clear separation between male and female lifters based on their total scores and bodyweights, 
with male lifters generally achieving higher totals and having higher bodyweights. The line of points along the x-axis at total = 0 would likely represents lifters who were disqualified. For both male and female lifters, there is a positive linear correlation between bodyweight and total score. 
As bodyweight increases, the total score tends to increase as well, which aligns with the expectation that heavier lifters generally have the potential to lift more total weight! While the overall trend is linear and positive, there is still substantial variation within each bodyweight range. The R-squared value of approximately 0.29 indicates that around 29% of the variability in total scores can be explained by bodyweight alone. 
This implies that a considerable portion of the variation in total scores is attributed to factors other than bodyweight, highlighting the complexity of performance in powerlifting competitions.
</p>

<hr>

<b> 6. Where do I stand in this scatterplot? </b>

![image](https://github.com/ghazi-hishamuddin/openpowerlifting_ipf_eda/assets/142828521/3b586f23-b8a4-4535-8b89-d27a9dd1c26c)

It would seem that I'm on the higher end of the distribution. Those 3 years of hard work definetly did not put to waste! However, there is still room for improvement as there are better performing lifters in my weightclass.

<hr>

<b> 7. What might contribute most in a lifter's total score? </b>

![image](https://github.com/ghazi-hishamuddin/openpowerlifting_ipf_eda/assets/142828521/da9794c8-329a-4253-877d-d536f74c105c)

It would seem that deadlift has a very strong correlation (0.92) with total, while bench has a smaller correlation (0.89).Both the squat and deadlift appear to be strong contributors to the total score, with the bench being slightly less influential but still positively correlated.

<hr>

<b> 8. The relationship of the three movements vs bodyweight </b>

![image](https://github.com/ghazi-hishamuddin/openpowerlifting_ipf_eda/assets/142828521/bfaa8b63-1843-41a3-8f2d-554a8a55235d)

<p align="justify">
The regression line plot shows a positive linear relationship between bodyweight and the best achieved weights for squat, bench press, and deadlift. As bodyweight increases, the best lift weights tend to increase as well, which is expected given the influence of body mass on overall strength potential.
It is obvious that bench performance will always be weaker than the other two lifts. However, given that the squat regression line is steeper, this indicates that squat performance increases at a faster rate with increasing bodyweight compared to deadlift performance, based on the regression models shown! It would seem at heavier bodyweights, lifters tend to squat more than their deadlifts.
</p>

<hr>

## Concluding Remarks:
<p align="justify">
What did we learn? Bodyweight isn't the only factor that determine lift performance in powerlifting. Hypothetically, I could sit in my weightclass category (under 59kg) and be a world class lifter one day! However we found out that 
there is an implication that a considerable portion of the variation in total scores is attributed to factors other than bodyweight, which highlights the complexity of performance in powerlifting competitions. By adding more variables, 
using advanced techniques, analyzing time series, and creating predictive models we could uncover new insights and opportunities for growth in this remarkable strength sport.
</p>




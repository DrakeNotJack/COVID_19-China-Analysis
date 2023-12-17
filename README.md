# COVID_19-China-Analysis
I used pandas for the data cleaning of the Covid_19 datasets. 

Two methods are utilized:
1. For method 1, I did cleaning for each csv file, and then appended them together
2. For method 2, I used a list to hold the dataframes and concated them together, and then did the data cleaning to the combined dataframe

Found out that method 2 took much less processing time than method 1 (approximately 30% faster)

Thus, I adopted the second method, applying it to the following two tables, which includes province and global data respectively.

When I started the visulization, I found the confirmed cases and death cases trend is up and down, which is unreasonable since they are accumulated figures that would only climb.
The 3 values that are tremendously greater than their neighbors are on 12 Apr 2022, 25 May 2022, and 9 Feb 2023.
Therefore, I went back to the sources files, and did find there are duplicates entries on these 3 days due to that the last update date for 12 Apr 2022 is at 13 Apr 2022 4am whereas the last update date for 13 Apr 2022 is also at 13 Apr 2022 9pm.

So I add drop duplicate function before each csv are combined.

# COVID_19-China-Analysis
I used pandas for the data cleaning of the Covid_19 datasets. 

Two methods are utilized:
1. For method 1, I did cleaning for each csv file, and then appended them together
2. For method 2, I used a list to hold the dataframes and concated them together, and then did the data cleaning to the combined dataframe

Found out that method 2 took much less processing time than method 1 (approximately 30% faster)

Thus, I adopted the second method, applying it to the following two tables, which includes province and global data respectively.

When I started the visulization, I found the confirmed cases and death cases trend is up and down, which is unreasonable since they are accumulated figures that would only climb.
The 3 values that are tremendously greater than their neighbors are on 12 Apr 2022, 25 May 2022, and 9 Feb 2023.

Therefore, I went back to the sources files, and did find there are duplicates entries on these 3 days.
Initially, I tried adding drop duplicate function before each csv are combined, but the duplicates still exist.

Then, I dig deeper into the last update date column since it's the column I used to generate the date column, and found out that the last update date for 12 Apr 2022 is at 13 Apr 2022 4am whereas the last update date for 13 Apr 2022 is also at 13 Apr 2022 9pm, which cause duplicates.
Hence, I didn't use the LAST_UPDATE column, instead, I tried using "df1.assign(Data = string_date)" sentence to assign the correct date to the "Date" column, but it showed "['Date'] not in index" error.
So I used "df1['Date'] = pd.to_datetime(string_date)" to assign the Date column, and it works perfectly, the duplicates disappeared.

Also noted that in "Province_State" column there is a value named "Unknown", but I didn't remove it since it may affect the overall numbers although we don't know the number is from which province.




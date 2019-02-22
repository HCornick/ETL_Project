# ETL Project

## Extract

My data sources were taken from Kaggle.com and Data.gov.  The Kaggle.com file is an SQLite database that contains two tables: NationalNames and StateNames.  I was focused on the NationalNames table, which provided data from 1880-2014 on baby names, and the count of babies in the United States named each specific name by year. The Data.gov file is a CSV that contains similar information, but specific to New York City from 2011-2016.  These data resources were unfortunately too large to upload through GitHub. To view these sources, please go to:

- https://www.kaggle.com/kaggle/us-baby-names#database.sqlite for the US Baby names SQLite database.

- https://catalog.data.gov/dataset/most-popular-baby-names-by-sex-and-mothers-ethnic-group-new-york-city-8c742 for the NYC Baby Names CSV file.

## Transform

In the process of transforming the data, I first wanted to make sure that I was using the same timeframe for each data source.  The timeframe that coincides with each source is 2011-2014. Thus, after creating a dataframe from each source via Pandas, I extracted the desired rows from each dataframe.  For the National Names source, this meant selecting rows that had years "greater than or equal to" 2011.  For the NYC Names source, this refers to rows that are "less than or equal to" 2014. This way, the final result would be a true "apples-to-apples" comparison.

The next step was grouping the data in each dataframe by name, and appending a column for the sum of the "Count" column. This would ultimately give us a list of unique names, and the count of babies named each name within the selected timeframe. After completing this step (for each source), I renamed the "Count" column in each dataframe to reflect the source that it was coming from so that once the two dataframes were combined, you could distinguish the two "Count" columns: "National_Count" vs. "NYC_Count."

After combining the two dataframes, the merged table contained a list of baby names, a column for the count of babies named each name in the US, and a column for the count of babies named each name specifically in New York City. To derive more from this comparison, I chose to add an additional column to the final dataframe: "NYC % of National." This column took the count of babies named each name in NYC, and divided it by the count of babies named that same name on a National level.

## Load

The last step was taking my final Pandas dataframe of approximately 1,400 rows, and exporting it to a CSV file. You can find this file within the repository.

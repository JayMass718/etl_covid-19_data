# Extract, Transform, Load Coronavirus Data
ETL Project Report
Contributors: Julian Massiah, Jennifer Qian

For the project, our group decided to Extract, Transform and Load (ETL) data based on the current Coronavirus outbreak. We found several google spreadsheet datasets, which documented the levels of contagion in the countries around the world. Each dataset was a measurement of the contagion on consecutive days between January 22th and January 27th, at 12-hour intervals. As a result, there are a total of 12 datasets.

Using Jupyter notebook, we first imported our tools. This required us to download and utilize the Google Spreadsheet API - first connecting to Google spreadsheet API to access the data, then bringing the data back from that API. We also had to download the tool Gspread Pandas, a package used to easily open the Google spreadsheet and interact with the datasets utilizing Pandas DataFrames.

The datasets are uploaded into Pandas. Two of the twelve datasets have mismatched column names. They are changed to match the rest of the datasets.
The datasets are then joined into one dataframe. After performing said tasks, we again rename the columns. One of the main reasons for doing this is because the Forward Slash characters included in the column headers are not so friendly with SQL, and we drop them for more favorable characters.

Next, our dataframe is sorted on the State column based off of the sorting of the values in the Last Update column. These two columns are the keys to understanding the data, because the State column indicates where the contagion exists, and the Last Update column indirectly tells us how much the numbers have increased from one day to the next over this 6 day period. Such data can be used in the future to analyze the pace and direction in which the disease is spreading. 

Finally, after more transformative work - replacing blanks in the state column to underscores, as well as indicating blank State variables as “other” - we were able to upload the data into SQL. We chose SQL because it allows us to manage the data in a more relational, regressive manner; this data is relatively structured. Any information we would need to extract about the virus can be accessed by specific queries that this database language provides.

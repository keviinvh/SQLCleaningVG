# Intro

A name for data that is not cleaned is dirty data. Dirty data costs companies an average of 3 trillion dollars each year. Thus, data cleaning is essential in the analytical process.

This is a project I worked on to practice my SQL skills. I downloaded the database from Kaggle and imported it into SQL. The project and database are located in the projects folder of this repository. The database I use is SQLite. To open the file, download the SQL file from the projects folder, open your SQL database, and open the file in that software. I have notes in the projects where my thought processes are, and I have all of the code except the last code I ran commented out. To run the code, highlight the code and hit the run SQL code button, or comment out the currently active code using /* at the beginning of the code and */ at the end of the code. Remove the same symbols from the beginning and end of the code you want to run.

# Data Cleaning

The steps I take in data cleaning include:
- Removing irrelevant data
- Remove duplicates in data
- Fix structural areas
- Deal with missing data
- Filter outliers out of data
- Standardize data

I start by removing irrelevant data to make the data less overwhelming. I use the code
 
![All Data]()

to display all data in the database. To determine irrelevant data, I think about what factors could have effects on other data. For this example, I see rank as irrelevant because it is the rank of total global sales, which is given, so it is essentially a count of total global sales in a broader sense. Total global sales gives more information, so I would much rather use that than rank. I determined the basis of rank by using the current code sorting by rank and noticing the pattern and correlation between rank and  global sales using the code:

![All Data Sorted by Rank]()

Thus, I would delete the row using the SQL code (After research, I find SQLite does not support this code):

![Delete Rank]()

To remove duplicates, the only current way I know how to proceed in SQL is by using the DISTINCT command as shown in the code below:

![Remove Duplicates]()

To fix structural areas means to correct things such as misspellings, incongruent naming, improper letter casings, incorrect words, etc.

There are no structural areas in this data, but to fix misspellings, incongruent naming, or incorrect words, you would use the replace command in the format Replace(Column_name,bad_data_name, Fixed_data_name). Incongruent naming is if, for example, data has a gender column and some women are put down as girls and some are put down as females. To fix improper letter casing, I find it easier to use the UPPER() or LOWER() function to make the whole column upper case or lower case.

To deal with missing data, I find it easier to delete these rows if there are not many in a large sample size. I filter the data to see if there are any N/A values and replace these values with null to get consistent data. Then I filter the table on not null. Otherwise, if the data sample is not large enough, I replace the null values with the mean.

Next, to deal with outliers I calculate 1.5 times the first quartile of data and the third quartile of data. If the data is smaller than the first quartile calculation or larger than the third quartile calculation, it is an outlier and should be filtered out.

Finally, I standardized the data. An example is if we have ratings on a 5-point scale and we want it on a 100-point scale, we multiply the column by 20.

I struggle to find good data to clean on kaggle, and SQLite is limited compared to other databases, so I feel like the best I could currently do is explain it.

##ELT Project Technical Report##

The goal of this project was to find data, clean/transform said data and then place it into a database. The data sets that we selected for this task were building ordinance violation in the city of Chicago and US census data. This would enable a consumer of the end product to be able to query the database in order to gain insights into the relationships between population and building violations in the various Chicago zip codes.

*Data Utilised*

Both datasets came from "Kaggle.com" in the form of CSV files, and both contained extremely large amounts of data (> 200MB each) and hence some initial filtering down had to be done outside of the task as the files could not be uploaded into GitHub as they were. In order to satisfy the GitHub requirements Excel was used to trim both datasets down to just the data relevant to 2010 prior to performing the tasks required by then exercise. 

*Transformation*
For the transformation, we created new dataframes based on the initial extraction. For the “Zip” dataframe, we focused only on the zip code and population. Since the initial dataframe included a row per gender and age bracket, we summed the population based on the unique zip code. We dropped any rows with missing data to ensure there was clean data. We created a new integer id to use as a primary key for the table.

For the “Ordinance” dataframe, we focused only on the zip code, violation code, violation description, and violation date. We used the existing id from the source file to act as the potential primary key for the table. All rows with missing data were dropped to ensure clean data. The column headers were renamed with underscores in place of spaces in order to avoid query errors in future work. 

*Load*
Lastly, with the Python script, we loaded these two dataframe tables into a “violations_db” Postgres database to store the data. We chose the Postgres relational database since the two tables can be easily joined based on zip code. The “violations” table is intended for tracking ordinance violations based on zip code, whereas the “zips” table is intended for storing population based on the zip code. 

*Next Steps*
Using the Python script and Postgres, users will be able to further explore the potential trends between different Chicago ordinance violations based on zip code. Additional tables could be potentially added to explore trends based on demographic information and income as well.

# Movies-ETL
## Overview and Background
After preparing three data sets in prepatation for a hackathon directions to keep these data sets updated resulted in the the following ETL process.

## The Data
The source data consists of:
1. Wikipedia movie data in JSON format
2. ratings data in csv format
3. movie meta_data in csv format

The source data is uncleanded so Extract, Transform adn Load (ETL) was performed on it resulting in 2 PostgresSQL tables; movies and ratings.

## ETL Steps

### Step 1, Extract

The three files were extracted in Python. Using Jupyter Notebooks along with Pandas, Numpy, psycopg2 and sqlalchemy the kaggle sourced movies_metadata csv file,
available to view here xxx and the ratings csv file, available to view here xxx where brought into a Jupyter notebook and put into dataframes. The Wikipedia json file
was loaded into a list and then to a dataframe. The code is available to view here xxx

### Step 2, Clean Wikipedia Data
Re using code from the original project and step 1, avialble to view here I:
1. Brought in the clean_movie funciton. The funciton combines titles, removing the no linger needed columns. As part of this merge some of the columns are renamed.
2. Used a list comprehension to filter out tv shows and ensured data has either director or directed by data - make sure its a mvoie and nto a show.
3. Wrote a try-except block to catch errors while extracting the IMDb ID using a regular expression string and dropping any imdb_id duplicates. If there is an error,
capture and print the exception.
4. Wrote a list comprehension to keep the columns that don't have null values from the wiki_movies_df DataFrame.
5. Converted the box office data created in Step 8 to string values using the lambda and join functions.
6. Wrote a regular expression to match the six elements of "form_one" of the box office data.
7. Wrote a regular expression to match the three elements of "form_two" of the box office data.
8. Parsed dollars using a function
9. Cleaned the budget column in the wiki_movies_df DataFrame.
10. Cleaned the release date column in the wiki_movies_df DataFrame.
11. Cleaned the running time column in the wiki_movies_df DataFrame.
12. Displayed the three data frames.

### Step3, Clean Kaggle Data
Building on steps 1 and 2, and available to view here I:
1. Cleaned the Kaggle data.
2. merged the wikipedia data with the kaggle data.
3. Dropped unnecessary columns from the merged DataFrame.
4. Created a funciton to fill in missing kaggle data.
5. Filtered the kaggle data frame to specific columns.
6. Renamed the columns for clarity.
7. Tansformed and merged this with the ratings data.
8. Displayed the three data frames.

### Step 4, load PostgresSQL data base
This involved preparing a combined code set from steps 1, 2, and 3 to load into a PostgressSQL database. Specifically:
1. Creating a db string and engine.
2. loading the movies data frame to the database
3. creating code to monitor the time it took to load the ratings file. This file contains 26,024,289 rows. Its a large file so the laoding was split into chunks.
It took 3109 seconds or 51.8 minutes to load.
4. Queries were run in the database to verify row counts, displayed here.





# IMDB Challenge
## Overview
Given a data set of the IMDB top 1000 movies of all time, found in the file 'imdb_top_1000.csv' 
in this repository, you are required to write Python code that will take care of creating a SQLite 
database, loading the CSV data into the database and performing query operations on the data.

## Expected Deliverable
It is expected that you provide: 

- One or more Python files that deliver the functionality outlined below
- A requirements.txt file that assists us in installing any dependencies for your code to run
- Any additional instructions we will need to run your script and test the functionality

These files can be compressed into an archive file to make it easier to share.

## Detailed Requirements
### Python Code

You should create a Python class with multiple methods that can handle the functionality 
required.

Your Python class must be able to provide the following functionality:

- Creating a SQLite Database
- Creating a table to house the data, with correct data types per column
- Loading the CSV data into the SQLite database, conducting some minor data cleanup
- Querying the data for certain information

Your script behaviour should be able to be controlled by user command line arguments. 

#### Creating a SQLite Database and Table
Using the sqlite3 library your code will need to cater for creating a SQLite database if it doesn't
yet exist. The name of the database should be customisable by the user calling your script.

You should include a method that creates the table in your database, again should it not already
exist, and ensure the data types for each column are correct e.g. string, integer etc.

#### Loading data
It is recommended that you investigate the Pandas library to assist you in completing this 
task.

When loading the data into your SQLite database you must conduct some alterations to ensure
you can achieve the required query pattens outlined below.

For example, in the data set the Runtime is a string with a value like '120 min'. You will need
to strip the number from that string and store it as an integer value in your database, so that 
we can conduct basic arithmetic operations on this field. 

That one was a free hint, perhaps you will find some others!

You will also need to handle only loading the data once. Let's assume you code for an input
argument '--import-data=True' and I run your script twice with this argument, you must handle
this and not load duplicated data into your database. 

#### Querying Data
Once your data is loaded, you need to provide Python methods to conduct the following queries:

- Top 10 movies based on IMDB rating

```text
python challenge.py --database test --table movies --seed True --query top_10_movies

1: The Shawshank Redemption (9.3)
2: The Godfather (9.2)
3: The Dark Knight (9.0)
4: The Godfather: Part II (9.0)
5: 12 Angry Men (9.0)
6: The Lord of the Rings: The Return of the King (8.9)
7: Pulp Fiction (8.9)
8: Schindler's List (8.9)
9: Inception (8.8)
10: Fight Club (8.8)

```
- Top 10 lead actors (Star1 field) based on their movies average IMDB rating
```text
python challenge.py --database test --table movies --seed True --query top_10_actors

1: Tim Robbins (9.3)
2: John Travolta (8.9)
3: Elijah Wood (8.8)
4: Lilly Wachowski (8.7)
5: Marlon Brando (8.65)
6: Suriya (8.6)
7: Roberto Benigni (8.6)
8: Lin-Manuel Miranda (8.6)
9: Kátia Lund (8.6)
10: Jodie Foster (8.6)
```
- Given a user input value of a year (e.g. 1990) return all the movies from that year, sorted by IMDB rating
```text
python challenge.py --database test --table movies --seed True --year 1990 --query year

1: Goodfellas (8.7)
2: Dances with Wolves (8.0)
3: Edward Scissorhands (7.9)
4: Misery (7.8)
5: Awakenings (7.8)
6: Miller's Crossing (7.7)
7: Home Alone (7.6)
8: The Godfather: Part III (7.6)
```
- Given a user input value of a year (e.g. 2019) determine the longest running movie of the year and return it, along with its runtime in hours
```text
python challenge.py --database test --table movies --seed True --year 2019 --query longest_movie

The Irishman (3.48 hrs)
```
- Determine the year that had the highest grossing movies and return it, along with the average gross of movies that year
```text
python challenge.py --database test --table movies --seed True --query gross_year

2018 ($186,268,383)
```
- Given a user input of part of a movie name (e.g. lord of the rings) return all matching movies and their IMDB rating
```text
python challenge.py --database test --table movies --seed True --query find_movie --movie 'lord of the rings'

1: The Lord of the Rings: The Return of the King (8.9)
2: The Lord of the Rings: The Fellowship of the Ring (8.8)
3: The Lord of the Rings: The Two Towers (8.7)
```

#### Command Line Arguments
As seen in the examples above, your script should be executable from a terminal, and it's behaviour should be
controllable via command line arguments.

Look into the argparse library to help you write this logic into your code. 

#### Dependencies
Your solution should include a requirements.txt file that can be used to install all dependencies via
Python PIP.

Investigate virtual environments and the Python PIP freeze command to help with this! 

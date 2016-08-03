
# Active Record Ratings

## The Overview

You've started a new movie-rating website, and you've been collecting data on reviewers' ratings of various movies. There's not much data yet, but you can still try out some interesting queries. Here's the schema:

### We'll start with the movies

```
Movie ( id, title, year, director )
```
English: There is a movie with `id` number, a `title`, a release `year`, and a `director`.

_Below is an example of entries in this table:_

| id | title | year  | director |
|----|-------|-------|----------|
| 101 | Gone with the Wind | 1939  | Victor Fleming |
| 102 | Star Wars | 1977  | George Lucas |
| ... | ... | ...  | ... |


### Now, the reviewers


```
Reviewer ( id, name )
```
English: The reviewer with `id` number and has a certain `name`.

_Below is an example of entries in this table:_

| id  | name            |
|-----|-----------------|
| 101 | Sarah Martinez  |
| 102 | Daniel Lewis    |
| ... | ...             |


### And finally, the ratings


```
Rating ( rating_id, movie_id, stars, rating_date )
```
English: The `reviewer_id` gave the `movie_id` a number of `stars` rating (1-5) on a certain `rating_date`.

_Below is an example of entries in this table:_

| rating_id | movie_id | stars | rating_date |
|-----------|----------|-------|-------------|
|   201     | 101      |  2    |  2011-01-22 |
|   204     | 106      |  4    |  2011-03-17 |
|   ...     | ...      |  ...  |  ...        |



**Note:** The database script to load your postgres database is found in `data.sql`. To import this into postgres, use `psql MY_DB_NAME < data.sql`.


**Instructions:** Each problem asks you to write an active record query (and raw SQL query if you're into that).

To run this code, we will be using **pry**. However, we also have to load the `setup.rb` file in order to connect to the database and load the models.

Run the following in your terminal to start pry with the setup:
```
pry -r './setup'
```

----

## Questions


_Q1._ **Find the titles of all movies directed by Steven Spielberg.**


_Q2._ **Find all years that have a movie that received a rating of 4 or 5, and sort them in increasing order.**


_Q3._ **Find the titles of all movies that have no ratings.**


_Q4._ **Some reviewers didn't provide a date with their rating. Find the names of all reviewers who have ratings with a NULL value for the date.**


_Q5._ **Write a query to return the ratings data in a more readable format: reviewer name, movie title, stars, and ratingDate. Also, sort the data, first by reviewer name, then by movie title, and lastly by number of stars.**


_Q6._ **For all cases where the same reviewer rated the same movie twice and gave it a higher rating the second time, return the reviewer's name and the title of the movie.**


_Q7._ **For each movie that has at least one rating, find the highest number of stars that movie received. Return the movie title and number of stars. Sort by movie title.**


_Q8._ **For each movie, return the title and the 'rating spread', that is, the difference between highest and lowest ratings given to that movie. Sort by rating spread from highest to lowest, then by movie title.**


_Q9._ **Find the difference between the average rating of movies released before 1980 and the average rating of movies released after 1980. (Make sure to calculate the average rating for each movie, then the average of those averages for movies before 1980 and movies after. Don't just calculate the overall average rating before and after 1980.)**

----

## Extras


_Q1._ **Find the names of all reviewers who rated Gone with the Wind.**


_Q2._ **For any rating where the reviewer is the same as the director of the movie, return the reviewer name, movie title, and number of stars.**


_Q3._ **Return all reviewer names and movie names together in a single list, alphabetized. (Sorting by the first name of the reviewer and first word in the title is fine; no need for special processing on last names or removing "The".)**


_Q4._ **Find the titles of all movies not reviewed by Chris Jackson.**


_Q5._ **For all pairs of reviewers such that both reviewers gave a rating to the same movie, return the names of both reviewers. Eliminate duplicates, don't pair reviewers with themselves, and include each pair only once. For each pair, return the names in the pair in alphabetical order.**


_Q6._ **For each rating that is the lowest (fewest stars) currently in the database, return the reviewer name, movie title, and number of stars.**


_Q7._ **List movie titles and average ratings, from highest-rated to lowest-rated. If two or more movies have the same average rating, list them in alphabetical order.**


_Q8._ **Find the names of all reviewers who have contributed three or more ratings. (As an extra challenge, try writing the query without HAVING or without COUNT.)**


_Q9._ **Some directors directed more than one movie. For all such directors, return the titles of all movies directed by them, along with the director name. Sort by director name, then movie title. (As an extra challenge, try writing the query both with and without COUNT.)**


_Q10._ **Find the movie(s) with the highest average rating. Return the movie title(s) and average rating. (Hint: This query is more difficult to write in SQLite than other systems; you might think of it as finding the highest average rating and then choosing the movie(s) with that average rating.)**


_Q11._ **Find the movie(s) with the lowest average rating. Return the movie title(s) and average rating. (Hint: This query may be more difficult to write in SQLite than other systems; you might think of it as finding the lowest average rating and then choosing the movie(s) with that average rating.)**


_Q12._ **For each director, return the director's name together with the title(s) of the movie(s) they directed that received the highest rating among all of their movies, and the value of that rating. Ignore movies whose director is NULL.**

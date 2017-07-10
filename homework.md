# SQL Homework

The Dominion Cinema are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'

```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:

```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question.

## Questions

1. Return ALL the data in the 'movies' table.
SELECT * FROM  movies;
2. Return ONLY the name column from the 'people' table
SELECT name FROM people;
3. Oops! Someone at CodeClan spelled Del's name wrong! Change it to reflect the proper spelling.
UPDATE people SET name = 'Del Middlemiss' WHERE name = 'Del Boy Middlemiss';
SELECT name FROM people;
4. Return ONLY your name from the 'people' table.
SELECT 'Tracy Steinberg' FROM people LIMIT 1;
5. The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.
DELETE FROM movies WHERE title = 'Batman Begins';
6. Create a new entry in the 'people' table with the name of one of the instructors.
INSERT INTO people (name) VALUES ('Keith Douglas');
SELECT name FROM people;
7. John Travolta, has decided to hijack our movie evening, Remove him from the table of people.
DELETE FROM people WHERE name = 'John Travolta';
SELECT name FROM people;
8. Somehow the list of people includes two people named 'Christopher'. Change these entries to the proper names ('Christopher Whatshisface', 'Christopher Theotherone')
UPDATE people SET name = 'Christopher Whatshisface' WHERE name = 'Christopher Donnelly';
UPDATE people SET name = 'Christopher Theotherone' WHERE name = 'Christopher Hunter';
SELECT name FROM people;
9. The cinema has just heard that they will be holding an exclusive midnight showing of 'Guardians of the Galaxy 2'!! Create a new entry in the 'movies' table to reflect this.
<!-- Add an extra column to data base -->
ALTER TABLE movies      
   ADD show_time2 VARCHAR(255);
   UPDATE movies SET show_time2 ='24:00' WHERE title = 'Guardians of the Galaxy 2';
   SELECT show_time2 FROM movies;
10. The cinema would also like to make the Guardian movies a back to back feature. Update the 'Guardians of the Galaxy' show time from 12:10 to 21:30
<!-- Movie time is 19:35 (not 12:10)- not sure what to do - so used my second movie time field -->
UPDATE movies SET show_time2 ='23:30' WHERE title = 'Guardians of the Galaxy';
SELECT show_time2 FROM movies;

## Extension

1. Research how to delete multiple entries from your table in a single command.
<!-- From W3C Schools -->
ALTER TABLE movie
DROP COLUMN title, show_time, show_time2;

# MovieRecommender

In this kernel, I'll be building a baseline Movie Recommendation System using the TMDB 5000 Movie Dataset.
All credit to Kaggle and TMDB for providing such an awesome dataset.

## DataSet

1st dataset has the following features:-

movie_id - A unique identifier for each movie.

cast - The name of the lead and supporting actors.

crew - The name of the Director, Editor, Composer, Writer, etc.

The second dataset has the following features:-

budget - The budget in which the movie was made.

genre - The genre of the movie, Action, Comedy, Thriller, etc.

homepage - A link to the homepage of the movie.

id - This is in fact the movie_id as in the first dataset.

keywords - The keywords or tags related to the movie.

original_language - The language in which the movie was made.

original_title - The title of the movie before translation or adaptation.

overview - A brief description of the movie.

popularity - A numeric quantity specifying the movie's popularity.

production_companies - The production house of the movie.

production_countries - The country in which it was produced.

release_date - The date on which it was released.

revenue - The worldwide revenue generated by the movie.

runtime - The running time of the movie in minutes.

status - "Released" or "Rumored".

tagline - Movie's tagline.

title - Title of the movie.

vote_average - average ratings the movie received.

vote_count - the count of votes received.


## Step 1: Cleaning the data ( Data Preprocessing)

- Import the dataset
- Rename the column movie_id to id, dropped title in the credits dataset
- Merged the credits.csv to Movies.csv


## Demographic Filtering

WR = (v/(v+m)) * R + (m/(v+m)) * C

v is the number of votes for the movie; (Vote_count)
m is the minimum votes required to be listed in the chart;
R is the average rating of the movie; And ( Vote_average)
C is the mean vote across the whole report
- Used IMDB's weighted rating formula to create a column with avg_score

## Step 2:

- Calculated the C and M value
- Edited the dataset to contain only movies with vote_count >= m
- Column calc_score stores the WR for each movie
- Sorted the movies on the basis of calc_score
- Now we have the top 10 movies visually represented in the form of charts based on WR
- Also shown top 20 movies based on popularity in a stacked bar chart.

## Building the Recommender - Content-Based Filtering

- Dropped null values
- Filtered out targeted columns
- Generated corpus for every movie, combining overview, genre, cast, and crew.
- Renamed some columns, dropped old columns

*  We need to convert the word vector of each corpus. We'll compute Term Frequency-Inverse Document Frequency (TF-IDF) vectors for each overview.

* Term frequency, is the relative frequency of a word in a document and is given as (term instances/total instances). Inverse Document Frequency is the relative count of documents containing the term given as log(number of documents/documents with term) The overall importance of each word to the documents in which they appear is equal to TF * IDF

* This will give us a matrix where each column represents a word in the corpus vocabulary (all the words that appear in at least one document) and each row represents a movie, as before.

* COSINE SIMILARITY: I will be using the cosine similarity to calculate a numeric quantity that denotes the similarity between two movies. We use the cosine similarity score since it is independent of magnitude and is relatively easy and fast to calculate.

- Computed cosine similarity on the tfidf vector
- Now we ensure that all the diagonal elements are 1
- Now finally we build the recommender function which gets the index of the movie from the dataframe and sorts top N similar movies and displays them.


## Images: 


<img src="https://github.com/khchoudhary8/MovieRecommender/assets/76583677/8fdcbe39-967d-4414-9c1f-f66ad7c6ec49.jpg" width="850" height="450">



<img src="https://github.com/khchoudhary8/MovieRecommender/assets/76583677/7875f58b-0ae1-4d94-b035-b1be548f385b.jpg" width="800" height="450">  



<img src="https://github.com/khchoudhary8/MovieRecommender/assets/76583677/2c6d7fde-6400-4c1b-a911-dda271169272.jpg" width="600" height="550">




## Thank You
### By Kumar Harsh


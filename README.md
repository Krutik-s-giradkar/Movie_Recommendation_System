# Movie_Recommendation_System

## Overview

 It processes movie data, extracts key features like genre and actors, and represents them numerically. It then calculates similarities between movies based on these features.

To get recommendations, simply provide a movie title you like. The system will find movies with similar content and recommend the top 5 matches. It's like having a friend who knows your taste in movies and can suggest new ones you'll likely enjoy.

 **Example**

Let's say you provide the movie title "Avatar" as input:

The system will then output a list of 5 movie titles that are most similar to "Avatar" in terms of their genres, keywords, overview, cast, and crew. These might be movies like:

1. Titan A.E.
2. Independence Day
3. Aliens vs Predator: Requiem
4. Small Soldiers
5. Battle: Los Angeles



This code implements a movie recommendation system using data from two CSV files: 'movies.csv' and 'credits.csv'. It performs the following steps:

1. **Data Loading and Preprocessing:**
   - Loads the two CSV files into Pandas DataFrames.
   - Merges the DataFrames based on the 'title' column.
   - Cleans the data by handling missing values.
   - Selects relevant columns ('genres', 'keywords', 'overview', 'title', 'cast', 'crew').
   - Extracts and formats data within specific columns (e.g., 'genres', 'cast', 'crew').
   - Combines relevant features into a 'context' column for each movie.

2. **Feature Extraction using Bag of Words (BOW):**
   - Utilizes the `CountVectorizer` from scikit-learn to implement the Bag of Words approach.
   - Creates a vocabulary of the most frequent words in the 'context' column.
   - Represents each movie as a vector based on the frequency of words in its 'context'.

3. **Recommendation System based on Cosine Similarity:**
   - Calculates the cosine similarity between movie vectors using `cosine_similarity` from scikit-learn.
   - Creates a similarity matrix where each element (i, j) represents the similarity between movies i and j.
   - Defines a function `recommendationsystem` that takes a movie title as input.
   - Finds the index of the input movie in the DataFrame.
   - Sorts movies based on their similarity to the input movie.
   - Recommends the top 5 most similar movies.

## Bag of Words (BOW) 

BOW is a simple text representation method that creates a "bag" of words from a document, disregarding grammar and word order. It counts the frequency of each word in the document, creating a vector representation. In this code, BOW is used to extract features from the 'context' column, which combines information about genres, keywords, overview, cast, and crew for each movie.

## Cosine Similarity 

Cosine similarity measures the similarity between two vectors by calculating the cosine of the angle between them. A higher cosine similarity value indicates greater similarity. In this code, cosine similarity is used to compare movie vectors created using BOW. The more similar the vectors, the more similar the movies are considered to be.

## Recommendation System Logic 

The recommendation system uses the cosine similarity matrix to find movies similar to a given movie. It takes a movie title as input, identifies its corresponding vector, and then finds the vectors (and thus movies) with the highest cosine similarity to it. These similar movies are then recommended to the user.

##  Where This Can Be Helpful

This type of recommendation system can be helpful in various scenarios:

* Movie Streaming Platforms: Recommending similar movies to users based on their viewing history or preferences.
* E-commerce Websites: Suggesting related products to customers based on their browsing or purchase history.
* Content Curation: Automatically creating playlists or collections of similar content (music, articles, etc.).
* Personalized Recommendations: Providing tailored recommendations to users based on their individual interests.
* Information Retrieval: Finding documents or articles similar to a given query.  

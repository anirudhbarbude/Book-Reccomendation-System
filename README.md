# Book-Reccomendation-System
Recommendation system for books 



Remember : Versions may be upgraded for some of the dependencies used debugg the code in that case.
Dowload Data From Sorce Provided : https://drive.google.com/drive/folders/1xe1l1qjZa1B7Ep4gZ5uzk6mrZYJ_5Z9s?usp=sharing
Handle Data With Care |



This repository contains a simple book recommendation system implemented using Python. The system is designed to suggest books to users based on their reading preferences and history. This README file provides an overview of the project, instructions for setting it up, and details on how to use it.

Python script that appears to be part of a book recommendation system. It reads data from CSV files, performs data preprocessing, and implements two recommendation algorithms: a Popularity-Based Recommender System and a Collaborative Filtering-Based Recommender System. It then saves some data structures as pickled files for later use.

Let's break down the code step by step and explain each part:

Import Libraries:

python
Copy code
import pandas as pd
import numpy as np
import pickle
from sklearn.metrics.pairwise import cosine_similarity
These are the necessary libraries being imported for data manipulation (Pandas and NumPy), serialization (pickle), and cosine similarity calculation (from scikit-learn).

Read CSV Files:

python
Copy code
books = pd.read_csv('books.csv')
users = pd.read_csv('users.csv')
ratings = pd.read_csv('ratings.csv')
The code reads three CSV files ('books.csv', 'users.csv', 'ratings.csv') into Pandas DataFrames: books, users, and ratings.

Data Exploration:

The code inspects the data by printing the shape (number of rows and columns) of each DataFrame.
It checks for missing values (NaN) in each DataFrame using .isnull().sum().
It also checks for duplicated rows using .duplicated().sum().
Popularity-Based Recommender System:

The code computes two DataFrames, num_rating_df and avg_rating_df, by grouping the ratings_with_name DataFrame by 'Book-Title' and calculating the count and average of 'Book-Rating'.
Then, it merges these two DataFrames into popular_df, filtering books with at least 250 ratings and sorting them by average rating in descending order.
Finally, it merges the popular_df with the books DataFrame to obtain relevant information about the top-rated books.
Collaborative Filtering-Based Recommender System:

The code identifies "padhe_likhe_users" (knowledgeable readers) by checking if they have rated more than 200 books.
It filters ratings from these users and identifies "famous_books" by checking if they have received at least 50 ratings.
A pivot table pt is created where rows represent books, columns represent user IDs, and values represent book ratings.
The pivot table is filled with 0s where there are missing ratings.
Calculating Cosine Similarity:

The code calculates the cosine similarity between books using cosine_similarity from scikit-learn. The result is stored in similarity_scores.
Recommendation Function:

The recommend function takes a book title as input.
It finds the index of the input book title in pt.
Then, it calculates the similarity scores between the input book and all other books and returns the top 4 similar books.
For each similar book, it collects information like title, author, and image URL from the books DataFrame.
Saving Data:

The code saves the pt, books, and similarity_scores as pickled files for later use.
Recommending Books:

To recommend books, you can call the recommend function with a book title as an argument, and it will return a list of recommended books along with their details.
Overall, this code snippet combines data preprocessing, popularity-based recommendation, collaborative filtering, and cosine similarity to provide book recommendations based on user ratings and book similarities. The recommendations are generated using collaborative filtering by finding similar books to the input book.







# Movie Recommendation System

This project is a movie recommendation engine built in a Jupyter Notebook. It suggests movies from a dataset of 10,330 titles and 105,340 ratings using two different methods:

1.  **Popularity-Based Filtering:** Recommends the most popular movies from a user-selected genre, based on average rating and a minimum number of ratings.
2.  **Content-Based (Genre) Filtering:** Recommends movies that are most similar to a user-selected movie, based on their shared genres.

The project features an interactive UI built with `ipywidgets` directly within the notebook, allowing you to easily get recommendations from either model.

This project was completed by **Afthab Rahman** as part of the "Data Science with Python Techmaghi project."

---

## 🎬 Features

* **Popularity Recommendations:** Get a top-N list of movies for any genre (e.g., "Top 10 Comedies").
* **Content-Based Recommendations:** Find movies similar to one you already like (e.g., "Movies like 'Pulp Fiction (1994)'").
* **Interactive UI:** A simple tabbed widget in the notebook lets you choose your recommendation type, select genres or movies, and get results instantly.
* **Data-Driven:** Uses `pandas` for data manipulation and `scikit-learn` for feature extraction and similarity calculations.

---

## 🛠️ How It Works

The recommendation system employs two distinct models:

### 1. Popularity-Based Recommender

This model calculates the most popular movies in a given genre.

1.  The `ratings.csv` and `movies.csv` files are loaded and merged.
2.  The dataset is grouped by **Genre** and **Title**.
3.  The **average rating** and **total number of ratings** (size) are calculated for every movie.
4.  The user selects a **Genre** (e.g., "Comedy"), a **minimum rating threshold** (e.g., 50 ratings), and a **Top-N** count (e.g., 10).
5.  The system filters the dataset for that genre and threshold, then returns the Top-N movies sorted by their average rating.

### 2. Content-Based (Genre) Recommender

This model finds movies with the most similar genres to an input movie.

1.  A "bag of words" is created for each movie, where the "words" are its genres (e.g., "Action Drama Thriller").
2.  A **TF-IDF (Term Frequency-Inverse Document Frequency) Matrix** is built from these genre strings. This converts the genre text into a numerical vector representation for each movie.
3.  A **Cosine Similarity Matrix** is computed from the TF-IDF matrix. This matrix stores a similarity score (from 0 to 1) between every pair of movies.
4.  When a user selects a **Movie Title** (e.g., "Pulp Fiction (1994)"), the system looks up that movie in the similarity matrix.
5.  It then returns the Top-N movies that have the highest cosine similarity score, indicating the most similar genres.

---

## 📁 Project Structure

```

.
├── movie\_recommendation system.ipynb  \# The main Jupyter Notebook
├── movies.csv                         \# Dataset with movie IDs, titles, and genres
├── ratings.csv                        \# Dataset with user IDs, movie IDs, and ratings
├── requirements.txt                   \# Package Requirements to run the project
└── README.md                          \# You are here

````

---

## 🚀 How to Run

1.  **Clone the repository** (or download the files) to your local machine.
2.  **Ensure you have the required libraries.** You can install them using pip:

    ```bash
    pip install -r requirements.txt
    ```
3.  **Launch Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```
4.  Open the `movie_recommendation system.ipynb` file.
5.  **Run all cells** in the notebook (Cell > Run All).
6.  Scroll to the bottom of the notebook to find the **interactive recommendation UI**.
7.  **Use the tabs:**
    * **Popularity Based:** Select a genre, set the minimum number of reviews, and the number of recommendations you want. Click "RECOMMEND ME".
    * **Content Based:** Select a movie title you like and the number of recommendations you want. Click "RECOMMEND ME".
8.  The output will be displayed as a `pandas` DataFrame.

---

## 📊 Dataset

The project uses a subset of the [MovieLens dataset](https://grouplens.org/datasets/movielens/).

* `movies.csv`: Contains 10,330 movie titles.
    * `movieId`: Unique identifier for each movie.
    * `title`: Movie title (including release year).
    * `genres`: Pipe-separated list of genres (e.g., "Adventure|Animation|Children").

* `ratings.csv`: Contains 105,340 user ratings.
    * `userId`: Unique identifier for each user.
    * `movieId`: Identifier for the movie being rated.
    * `rating`: Rating given (on a 0.5 - 5.0 scale).
    * `timestamp`: Time the rating was given.
````

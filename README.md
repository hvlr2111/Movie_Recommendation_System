# 🎬 Movie Recommendation System

## 📊 Project Overview
This project implements a **content-based movie recommendation system** using machine learning. Recommendation systems are a cornerstone of modern digital services, used by platforms like Netflix, Amazon, and Spotify to personalize user experience. This system analyzes user rating patterns to find similarities between movies. When a user inputs a movie they enjoy, the system suggests other films they are likely to appreciate based on those shared patterns.

## 🎯 Objectives
- **Implement** a content-based filtering approach using collaborative data (user ratings).
- **Preprocess** and structure user-movie rating data into a format suitable for machine learning.
- **Build and Train** a k-Nearest Neighbors (k-NN) model using cosine similarity to identify the most similar movies.
- **Create a reusable function** that takes a movie title as input and returns a list of personalized recommendations.

## 🛠️ Tech Stack
- **Programming Language:** Python
- **Libraries:**
  - `pandas`, `numpy` (Data Manipulation & Analysis)
  - `scikit-learn` (Machine Learning: `NearestNeighbors` model, distance metrics)
  - `scipy` (Sparse Matrix handling with `csr_matrix` for efficient computation)
  - `matplotlib`, `seaborn` (Data Visualization - ready for extended analysis)

## 📁 Dataset
- **Source:** A custom `ratings.csv` file was used for this project.
- **Description:** The dataset contains user-movie interactions with the following features:
  - `userId`: Unique identifier for each user.
  - `movieId`: Unique identifier for each movie.
  - `title`: The title of the movie.
  - `rating`: The rating given by the user to the movie.

## 🔬 Methodology & Steps

### 1. Data Loading & Exploration
- Loaded the dataset using `pandas` and inspected its structure to understand the user-rating relationships.

### 2. Data Preprocessing & Matrix Creation
- **User-Item Matrix:** Transformed the raw data into a user-item matrix using a pivot table, where rows represent movies and columns represent users.
- **Sparse Matrix Conversion:** Converted the pivot table into a Compressed Sparse Row (CSR) matrix using `scipy`. This is a critical step for efficient memory usage and computation, especially with large-scale data.
- **Mapping:** Created dictionaries to map movie IDs to matrix indices and back, allowing for easy lookup between movie titles and their positions in the model.

### 3. Model Building & Training
- **Algorithm:** Implemented the **k-Nearest Neighbors (k-NN)** algorithm using `scikit-learn's` `NearestNeighbors`.
- **Similarity Metric:** Used **cosine similarity** as the distance metric. This metric is ideal for this context as it measures the cosine of the angle between rating vectors, effectively judging similarity based on rating patterns rather than magnitude.
- The model was fitted on the sparse user-item matrix to learn the "distance" between all movies.

### 4. Making Recommendations
- Developed a `recommend_similar(movie_title, k)` function that:
  1.  Takes a movie title and the number of recommendations (`k`) as input.
  2.  Finds the corresponding movie vector in the dataset.
  3.  Queries the k-NN model to find the `k+1` most similar movies (the closest neighbor is the movie itself).
  4.  Maps the indices of these similar movies back to their titles.
  5.  Returns and prints a clean list of recommendations for the user.

## 📈 Results & Example
The system successfully provides intuitive and relevant movie recommendations.

**Input:**
```python
recommend_similar("The Dark Knight", ratings, X, movie_mapper, movie_inv_mapper, k=5)
```
**Output:**
Because you liked 'The Dark Knight', you might also enjoy:
- Fight Club
- The Pianist
- Parasite
- 12 Angry Men
- The Lord of the Rings: The Return of the King

## 🚀 How to Run
  
1.  Clone this repository:
    ```bash
    git clone https://github.com/hvlr2111/movie-recommendation-system.git
    ```
2.  Navigate to the project directory:
    ```bash
    cd movie-recommendation-system
    ```
3.  Install the required libraries:
    ```bash
    pip install -r requirements.txt
    ```
4.  Ensure the `ratings.csv` file is in the same directory as the notebook.
5.  Run the Jupyter Notebook `Movie_Recommendation_System.ipynb` cell by cell.

## 📝 Future Work
- Integrate larger datasets (MovieLens 25M)
- Add hybrid filtering (content + collaborative)
- Web interface with Streamlit
- Real-time API deployment

## 👤 Author
H.V.L.Ranasinghe
- LinkedIn: https://www.linkedin.com/in/lakshika-ranasinghe-1404ab34a/

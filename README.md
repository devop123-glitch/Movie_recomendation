Movie_recommender_system_workflow:
This project implements a content-based movie recommendation system using metadata from the The Movie Database (TMDB) dataset. The system recommends movies by analyzing similarities in their content, such as genre, cast, keywords, and storyline.

The process begins with data collection, where two datasets are used: one containing movie details and another containing cast and crew information. These datasets are then merged on the movie title, creating a unified dataset that combines all relevant information for each movie.

Next, the data undergoes preprocessing to ensure it is clean and usable. Missing values are removed, and columns containing structured data (such as genres, keywords, cast, and crew) are converted from string format into proper lists. From these, only the most important elements are extracted—such as genre names, key keywords, the top cast members, and the director.

After preprocessing, the project moves to feature engineering, where a new column called tags is created. This column combines the movie’s overview, genres, keywords, cast, and director into a single textual representation. This step is crucial because it transforms multiple features into one unified format that can be analyzed effectively.

The combined text is then normalized through text processing. All characters are converted to lowercase, spaces between names are removed, and stemming is applied to reduce words to their base form. This ensures consistency and improves the quality of the analysis.

Once the text data is prepared, it is converted into numerical form using vectorization. A Bag-of-Words approach is applied through CountVectorizer, where each unique word becomes a feature and each movie is represented as a vector. This allows the system to perform mathematical comparisons between movies.

The next step is similarity computation, where cosine similarity is used to measure how similar two movies are based on their vector representations. Movies with similar content will have vectors that are closer to each other, resulting in higher similarity scores.

Finally, the system performs recommendation generation. When a user selects a movie, the system compares it with all other movies, ranks them based on similarity scores, and returns the top matches as recommendations.

In summary, the entire workflow transforms raw movie metadata into structured features, converts them into numerical vectors, and uses similarity measures to recommend movies with similar characteristics. This approach does not rely on user history but instead focuses entirely on the content of the movies.
Pipeline:
┌──────────────────────┐
│   Data Collection    │
│ (Movies + Credits)   │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│    Data Merging      │
│   (on movie title)   │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   Data Preprocessing │
│  - Remove nulls      │
│  - Parse JSON fields │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│  Feature Engineering │
│  - Genres            │
│  - Keywords          │
│  - Cast              │
│  - Director          │
│  → Create "tags"     │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   Text Processing    │
│  - Lowercase         │
│  - Stemming          │
│  - Remove spaces     │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   Vectorization      │
│  (CountVectorizer)   │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Similarity Computation│
│  (Cosine Similarity) │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│  Recommendation      │
│  Top N similar movies│
└──────────────────────┘

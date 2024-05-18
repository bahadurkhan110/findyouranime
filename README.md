# FindYourAnime - Anime Recommendation System

## Introduction

The objective of this project is to develop a recommendation system, `FindYourAnime`, which helps users discover new and exciting anime titles that align with their unique preferences, beyond mainstream suggestions. This system utilizes collaborative filtering and content-based filtering techniques to provide personalized recommendations. Additionally, a user-friendly web application is developed using Gradio to deliver these recommendations interactively.

## Dataset

### MyAnimeList Dataset

The dataset used in this project is sourced from MyAnimeList, a comprehensive database for anime titles, including user ratings, reviews, genres, themes, and other metadata.

**Anime Dataframe:**
- `anime_id` (int64): Unique identifier for each anime.
- `name` (object): Title of the anime.
- `genre` (object): Genre(s) associated with the anime.
- `type` (object): Type of anime (e.g., TV, Movie).
- `episodes` (object): Number of episodes.
- `rating` (float64): Average user rating.
- `members` (int64): Number of members who have added the anime to their list.

**Ratings Dataframe:**
- `user_id` (int64): Unique identifier for each user.
- `anime_id` (int64): Unique identifier for each anime.
- `rating` (int64): Rating given by the user to the anime.

## Data Preparation

### Merging Dataframes

The `anime_data` and `rating_data` dataframes are merged on the `anime_id` to create a comprehensive dataframe (`anime_fulldata`) containing all necessary information.

```python
anime_fulldata = pd.merge(anime_data, rating_data, on='anime_id', suffixes=['', '_user'])
anime_fulldata = anime_fulldata.rename(columns={'name': 'anime_title', 'rating_user': 'user_rating'})

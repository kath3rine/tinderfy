# Tinderfy 
A quasi-satirical, music-centric "dating app" that provides insight on a potential partner's taste in music, combining the intrigue of listening habits with the game-like addictiveness of dating apps (think Spotify Wrapped + Tinder). Two users put in songs they like and dislike, and are shown a "profile page" detailing their musical compatibility, including a compatibility score, artists/genres/audio traits they both like, and relevant recommendations. 

## How it works ##
For each of the four playlists, it creates a dataframe (table) of all the songs which includes audio features (energy, tempo, etc), title, artist, artist's genre for each song, and whether the user likes/dislikes it (songs in the "disliked" playlists are assigned 0, and songs in the "liked" playlists are 1)   
#### Compatibility Score (header section):
- Implements a [decision tree classifier](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html) (DTC) to determine the similarity of the users' music profiles based on their songs' audio traits by using DTC to predict/compare users' song data
- Trains DTC using the raw audio features (amount of energy, valence, etc) in user1's playlists for X variables, and the approval score (i.e. whether or not the user likes it) for y variable, and tests it using the same variables/data for user 2's playlists
- Users' "compatibility percentage" is the score value of the DTC - a higher score means that the DTC more accurately predicts whether or not user 2 likes a song based on user 1's preferences, indicating that the users 2's liked (or disliked) songs sound similar to those of user 1.

#### Favorite + Shared Artists/Genres ("bubbles" section):
- Creates lists of user 2's favorite artists/genres, and the artist/genres that both users like (like Tinder, artists/genres they have in common will appear red, not grey).

#### Recommendations for both people ("about me" section):
- Generates songs and artists (with links) both users would like by using the list of shared artists and/or genres as the seed for Spotify API's "get recommendations" and "related artists" endpoints, respectively

#### Similar Audio Features ("prompts" section)
- Takes the mean value of each audio feature for both users' "likes" playlists; iff the difference between their means for a given feature is below a threshold (e.g. they both like songs with high energy), that feature will appear here

#### Matching (messaging page):
- The users can choose whether or not to "match" (i.e. they like one another). If they do, their profile data will appear in a page mimicking to Tinder's "messages" tab

## Background ## 
#### Motivation
- I believe that someone's music taste says a lot about them, and I'm always looking for people who like the same music as me
- So, when my friend (avid dating app user) mentioned that a girl's taste in music would make or break it, I decided to create an app that evaluates a potential partner's compatibility based on their music taste

#### Tech Stack
- Frontend: HTML, CSS
- Backend: Flask (Python: scikit-learn, Pandas), Spotify API

#### Depenencies
- Flask (1.1.2)
- Python (3.9.13): Pandas, scikit-learn, requests, statistics



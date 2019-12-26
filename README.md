# Recommendations with IBM Watson

## Overview
In this project I will be using the dataset of articles that a user has seen on IBM and will build a recommender to suggest additional articles that the user would be interested in seeing. I will build recommendation systems based on rank. 

## Pre-requisites
This notebook will run on a base conda environment

## Running Instructions
`Recommendations_with_IBM.ipynb` - run this jupyter notebook in order to load up the datasets and do all the necessary analysis and build the recommendation systems. The following are the recommendations that are built in the notebook.
### Sections
1. Rank Based Recommendations
2. User Based Collaborative Filtering
3. Content Based Recommendations
4. Matrix Factorization

## Notebook Contents
### Data Structures
- `df` : {Dataframe} Contaning columns article_id, title, user_id
- `df_content` : {Dataframe} Containing columns doc_body, doc_description, doc_full_name, doc_status, article_id
- `user_item`: {Dataframe} User Ids as index and Article Ids as columns with a '1' where user has viewed an article and '0' otherwise
- `df_articles`: {Dataframe} Combined data of article titles that a user has viewed, and the entire corpus of live articles including doc name, description and content.
- `user_item_train`: {Dataframe} user-item matrix that is used to perform SVD for recommendation


### Available Functions
- `get_top_article_ids(n, df=df)`: returns ids of top `n` articles
- `get_top_articles(n, df=df)`: returns titles of top `n` articles
- `find_similar_users(user_id, user_item=user_item)`: returns a tuple of 1) an ordered list of users that similar to the current user, and 2) the similarity scores computed from the dot product of user_item matrix
- `get_user_articles(user_id, user_item=user_item)`: returns a tuple of articles ids, article titles that the user has seen
- `get_top_user_articles(user_id, user_item=user_item, df=df)`: returns a tuple of articles ids, article titles that the user has seen ordered by how popular the article was among all users
- `get_article_names(article_ids, df=df)`: given article ids, returns a list of associated article titles
- `user_user_recs(user_id, m=10)`: returns `m` articles ids for the given user based on the top similar users
- `get_top_sorted_users(user_id, df=df, user_item=user_item)`: returns a dataframe of top nearest neighbors for the given user with the columns neighbor_id, similarity, num_interactions
- `user_user_recs_part2(user_id, m=10)`: return a tuple of `m` article ids, article_titles recommended for the user based on 1) the nearest neighbors that have the most article read count, 2) ordered by the neighbor's articles that have the most readership count
- `tokenize`: Tokenizes and lemmatizes the document or text into a corpus of words
- `build_model`: Build a pipeline using Count Vectorizer, a custom tokenizer, and a TF-IDF Transformer
- `make_content_recs`: Uses a fitted model to transform a new document / text and make similar content recommendation based on the corpus that has already been fit
- `create_test_and_train_user_item`: Applies matrix factorization on training and test data and returns the user-item matrix for each of them

## Conclusion
>Having built the various recommendation systems as part of this project, I am making the following observations. It is important to give accurate recommendations to the users, however it is equally important to give novel (new content) as well as serendipitous (something unexpected, yet interesting) recommendations to the user. 

>It is important to note that the `user based collaborative filtering` and `content based recommendation` systems will only work when a user has already seen some articles. The SVD technique is very powerful, however it will additionally only work within articles that already have some viewership.

>The best recommendation system would be a weighted combination of user-based recommendation (based on what the current user has already seen that others are seeing too) and nearest-neighbor based recommendations (what similar users are seeing) for existing content, and additionally including some content-based recommendations (content similar to what the user has seen) for brand new articles.

>For new users however, the best way to bootstrap the recommendation system would be to start showing top viewed articles and wait to understand the new user's preferences better.


## References
- [Udacity Data Science NanoDegree Course Content](https://classroom.udacity.com/nanodegrees/nd025)
- [Numpy Reference](https://docs.scipy.org/doc/numpy/reference/index.html)
- [Pandas Reference](https://pandas.pydata.org/pandas-docs/stable/reference/index.html)
- [Stackoverflow](https://stackoverflow.com/)
- [Duck Duck Go Search Engine](https://duckduckgo.com/)

## License
This content may be used freely for educational and reference purposes. Do not copy this for your own projects, and please do attribute wherever appropriate.
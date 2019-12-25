# Recommendations with IBM Watson

## Overview
In this project I will be using the dataset of articles that a user has seen on IBM and will build a recommender to suggest additional articles that the user would be interested in seeing

## Running Instructions

## Project Structure
### Data Structures
- `df` : {Dataframe} Contaning columns article_id, title, user_id
- `df_content` : {Dataframe} Containing columns doc_body, doc_description, doc_full_name, doc_status, article_id
- `user_item`: {Dataframe} User Ids as index and Article Ids as columns with a '1' where user has viewed an article and '0' otherwise

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

### Folders
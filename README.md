# Netflix-Content-Analysis

> This project was taken up to explore my viewing preferences on Netflix. I am a big fan of the 90's bollywood movies but when it comes to TV shows, Hollywood, no doubt! What can i expect on Netflix in terms of my genre selection or choice of streaming? 

## About

We have all seen Netflix grow incredibly over the decade and become a popular streaming source for TV shows and movies. As of the end of 2019, the company was valued at more than $150 billion and has more than 167 million paid subscribers worldwide. It cannot be ruled out that the number of paid subscribers continue to grow despite a consistent increase in the price of subscription. 

It definitely raises a question - What kind of content do people enjoy so much that it allowed Netflix almost to double their revenue in just 3 years?

## Data

For the analysis I have considered a dataset that consists of tv shows and movies available on Netflix as of 2019. It has been obtained from Flixable which is a third-party Netflix search engine.

Variable | Description
---------|------------
show_id | Unique ID for every Movie / Tv Show
typeIdentifier | A Movie or TV Show
title | Title of the Movie / Tv Show
director | Director of the Movie
cast | Actors involved in the movie / show
country | Country where the movie / show was produced
date_added | Date it was added on Netflix
release_year | Actual Release year of the move / show
rating | TV Rating of the movie / show
duration | Total Duration - in minutes or number of seasons
listed_in | Genere
description | The summary description

## Solution highlights

I have tried to look the data from a crude perspective and answer the following question:
* Does Netflix have more TV shows or Movies? 
* Is there more mature or kids-friendly content? 
* How 'old' is the content on Netflix? 
* Are there more documentaries or comedies, thrillers or actions, stand-ups or dramas? 
* What actors do we see more often on Netflix? 
* Is the average length of a movie gradually increases as consumers have more and more opportunities to enjoy them in the comfort of their home?

I have also used the the description column of the data to create clusters and find similar content. 

```
text_content = df['description']
vector = TfidfVectorizer(max_df=0.4,                    
                             min_df=1,                 
                             stop_words='english',
                             lowercase=True, 
                             use_idf=True, 
                             norm=u'l2',
                             smooth_idf=True    
                            )
tfidf = vector.fit_transform(text_content)
```
```
k = 200
kmeans = MiniBatchKMeans(n_clusters = k)
kmeans.fit(tfidf)
centers = kmeans.cluster_centers_.argsort()[:,::-1]
terms = vector.get_feature_names()

for i in range(0,k):
    word_list=[]
    print("cluster%d:"% i)
    for j in centers[i,:10]:
        word_list.append(terms[j])
    print(word_list) 
```
```
def find_similar(tfidf_matrix, index, top_n = 5):
    cosine_similarities = linear_kernel(tfidf_matrix[index:index+1], tfidf_matrix).flatten()
    related_docs_indices = [i for i in cosine_similarities.argsort()[::-1] if i != index]
    return [index for index in related_docs_indices][0:top_n]  
```

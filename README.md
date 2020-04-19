# Netflix-Content-Analysis
Explore my viewing preferences on Netflix

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
* I am a big fan of the 90's bollywood movies.What can i expect?
* Is the average length of a movie gradually increases as consumers have more and more opportunities to enjoy them in the comfort of their home?

I have also used the the description column of the data to create clusters and find similar content. 

```
function test() {
  console.log("notice the blank line before this function?");
}
```

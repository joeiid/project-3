# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP

## Project 3: Web APIs & NLP

---


### Problem Statement:
---

Millions of people everyday are searching the web for information and anwers. One of the biggest website for forums and discussions is Reddit, holding over 2.8 million different subreddits. Reddit recently has a huge sytem upgrade and during the update millions of reddit post were swithched into incorrect subreddits. Reddit has hired my team to try and classify each reddit post to its correct subreddit. For our trial run we are trying to classify subreddit post between NASA and SpaceX. We purposly picked two subreddits with closely-related post to see how well our model can accurately re-classify the post to their respective subreddit.


### Data:
---

 - nasa.csv : r/NASA websraped data
 - spacex.csv : r/SpaceX webscraped data
 


### Data Dictionary:
---

|Feature|Type|Description|
|---|---|---|
|**subreddit**|*obj*|Identifies what subreddit the post came from, NASA or SpaceX.| 
|**id**|*obj*|Identifies the post that was submitted.|
|**author**|*obj*|Identifies the author who submitted the post to that specific subreddit.| 
|**title**|*obj*| The title of the subreddit post.
|**created_utc**|*int64*|Identifies the time and date the subreddit post was posted.| 
|**title_length**|*int64*|Lenght of title by characters in the title.| 
|**title_wordcount**|*int64*|Length of title by word count.| 



### Dictionary Description
---

The data dictionary has the categories of the subreddits that I webscraped and chose to keep. These are the categories of the NASA and SpaceX subreddits the modeling will be done on.



### Analysis:
---

#### EDA Analysis:

Creating two new columns that will give us the length and wordcount per titles in the subreddit post. With this information we can see if one post more commonly uses longer post or words. This could help differentiate between NASA subreddit and SpaceX subreddit. Going through the EDA process we learned that spacex title word and character count were longer than nasa. The obvious most common words were spacex and nasa but also has many similarities like moon, mars, launch, and space. Spacex reddit tends to talk about their founder Elon Musk often so that could be an obvious stand out word to classify for the spacex reddit.


#### WordCloud Analysis:

I decided to do a world cloud so i can get a better idea on which words were going to be the most commonly used in the NASA subreddit, SpaceX subreddit, and the combined dataframe with both subreddits. As expected, the nasa subreddits most common word was nasa, and the spacex subreddits most common word was spacex. The only thing I found a bit strange was how common spacex was used in the NASA subreddit.

#### CountVectorizer and TFIDFVectorizer Analysis:

When analysing the top 10 words in the combined NASA/SpaceX subreddit dataframe, I noticed that the top 10 words from the count vectorizer and the top 10 words from the TFIDF Vectorizer were slightly different. It removed nasa, spacex, space, and launch that were the top 4 on the list and instead made starship, elon, moon, and musk the top most common words. In my opinion, The TFIDF is doing a better job by removing the obvious words that could cause more confusion because of the high cross over and keeping words that could help identify the subreddit post. Nasa, spacex, space, are used over 1500 times in the post that were pulled, so they could cause a problem.

#### Count Vectorizer/ Logistic Regression Analysis:

The first model we decided to use Count Vectorizer and Logistic Regression. This gave .82 score on how the model will perform on unseen data. On the training data we scored a .94 and a .83 on the test data. The model is overfit by .11, meaning it does very well with the data we have given it but when introduced with new data it might not work as well.

The confusion matrix is a summary of prediction results on classification problems. This gives us the number of correct and incorrect prediction. We were able to predict 1304 words that were not from the correct subreddit correctly and 1213 that were from the correct subreddit. The model also predicted 304 post were not in the correct subreddit when it was, and 220 post were in the correct subreddit when it was not.

#### TFIDF Vectorizer/ Logistic Regression Analysis:

The second model we decided to use TFIDF and Logistic Regression. On the training data we scored a .91 and a .83 on the test data. The model is overfit by .8, it was a bit better than the first model because it was not as overfitting so it would perform better with new data but was slightly worse on the data trained on.

The confusion matrix showed us that the model was able to predict 1343 words that were not from the correct subreddit correctly and 1192 that were from the correct subreddit. The model also predicted 325 post were not in the correct subreddit when it was, and 181 post were in the correct subreddit when it was not.

#### Count Vectorizer/ Decision Tree:

The third model we decided to use count vectorizer and Decision Tree. This gave .78 score on how the model will perform on unseen data. On the training data we scored a .98 and a .79 on the test data. The model is overfit by .19, it does very well with the data we have given it but when introduced with new data it might not work as well.

We were able to predict 1258 words that were not from the correct subreddit correctly and 1155 that were from the correct subreddit. The model also predicted 362 post were not in the correct subreddit when it was, and 266 post were in the correct subreddit when it was not.

#### TFIDF with Decision Tree:

The fourth model we decided to use TFIDF and Decision Tree. On the training data we scored a .98 and a .79 on the test data. The model is overfit by .19, it performed almost perfect with the data that we trianed it with but a .19 overfit means we would definitly have trouble with any new data.

The confusion matrix showed us that the model was able to predict 1250 words that were not from the correct subreddit correctly and 1158 that were from the correct subreddit. The model also predicted 359 post were not in the correct subreddit when it was, and 274 post were in the correct subreddit when it was not.

### Conclusions & Next Steps:
---
Between the four separate models, the TFIDF and Logistic Regression model would be the best choise. It did not have the best score on the training data or the test data but it had the least amount of overfitting and the testing data was only a 2 points down from the highest one. This model till had an 8% overfitting but would be the best choice between the other three, with the TFIDF and Decision Tree model having at 19% overfitting. I did try tuning the models a bit but that was the parameters to pick.

How I would proceed if their was more time is i would try different iterations of models (KNNeighbors, MultinomialNB, ect.) and see if there are better models that could transform and evaluate the data. I would focus on finding a model that has a higher test score and a lower overfitting score because of the task. Once we introduce thousands of other reddit post we want the model to be more fluid and classify other post that were not seen.
---
layout: post
title:  "Who Wrote the 'Resistance' Op-Ed?"
date:   2018-09-09
author: "Sage Thomas"
categories: analysis
---

A few days ago the New York Times published an [op-ed][nyt_resistance] by a person 
identified only as a "senior official in the Trump administration." This person claims to be part of
a group of senior officials who are "working diligently from within to frustrate parts of 
[President Trump's] agenda". The [Washington Post][wp_who]
and others have attempted to uncover the anonomous writer, but suggestions remain speculative. Was
it Mike Pence? Nikki Haley? Mike Pompeo? Nobody knows, so we at Bookmatch decided to give it try. 

[Click here to skip to the results][bm_results]

Bookmatch normally analyzes the text of a fiction novel and compares it against bestsellers. With a
bit of tweaking we were able to setup a way to compare the anonymous article against op-eds written by
members of the White House Cabinet. Bookmatch can then use a machine learning method that implements
[stylometry][wi_stylometry] to attempt to match the article with one of the authors. Stylometry
is a way to "fingerprint" an author's writing style by tracking the frequency of common words, parts
of speech, and punctuation. 

We were only able gather 68 articles written by 8 cabinet members. To qualify for
our analysis each person had to have written at least 5 articles. Any less and the accuracy of the
algorithm would be severely affected. Bookmatch is optimized for ~100,000 word novels, so <1,000 word
articles stretch the capabilities of stylometry. The results are interesting nonetheless.

### Our Candidates

The top 8 most prolific writers in the White House cabinet staff are:

* Alex Azar, United States Secretary of Health and Human Services
* Linda McMahon, Administrator of the Small Business Administration
* Mick Mulvaney, Office of Management and Budget
* Mike Pence, Vice President of the United States
* Mike Pompeo, United States Secretary of State
* Nikki Haley, United States Ambassador to the United Nations
* Robert Lighthizer, United States Trade Representative
* Sonny Perdue, United States Secretary of Agriculture

We will assume the anonymous writer is one of these eight people for our analysis.

### Pre-Analysis

Before we start the analysis a few things have to happen. First, each article has to be
cleaned of non-standard characters. Bookmatch then chunks the articles into 500 word sizes. This 
helps to standardize the data and increase the data points that we can harvest. Next, Bookmatch 
identifies the parts of speech of each word and generates a list of data points we can look at.

### Parts of Speech Analysis

Parts of speech frequency is the best to visualize. The staff member with the most similar 
fingerprint to the anonymous op-ed is Alex Azar. The least similar is Linda McMahon. Here are the
bar graphs, the vertical line on the authors' bars displays the standard deviation (68% of the 
tracked values fall between the line): 

#### Alex Azar vs Anonymous
![Alex Azar](/assets/img/alex_azar.png)
#### Linda McMahon vs Anonymous
![Linda McMahon](/assets/img/linda_mcmahon.png)

### Full Analysis

On top of looking at the frequency of parts of speech, we can also track 50 of the most commonly
used words. Hyphens and question marks are also used frequently by certain authors. We then use a
machine learning algorithm called a gaussian process classifier to predict who wrote the letter. 

### Results

Our algorithm successfully predicts an author of an article with 50% accuracy, 4x better than 
randomly guessing. 86% of the time the author is in one of the top three choices.

#### Most Likely

* Alex Azar
* Mick Mulvaney
* Robert Lighthizer

#### Least Likely

* Mike Pence
* Nikki Haley
* Linda McMahon

Of the top three, Robert Lighthizer seems to write the most about topics mentioned in the anonymous
op-ed. He wrote highly about [Senator McCain][robert_article_1] and warns about 
[Republicans' changing views on free trade][robert_article_2]. However, we did not want to include 
words that covered these topics to remain as unbiased as possible considering how little 
data there is.

I hope you enjoyed reading this blog post! We hopefully got closer to the truth, and this was a fun
exercise to test Bookmatch in the real world. If you have any questions or comments feel free to 
email me at [sage@bookmatch.com][sage_email] or tweet [@_bookmatch][bm_twitter].


[bm_homepage]: https://bookmatch.com
[nyt_resistance]: https://www.nytimes.com/2018/09/05/opinion/trump-white-house-anonymous-resistance.html
[wp_who]: https://www.washingtonpost.com/graphics/2018/politics/who-wrote-the-resistance-op-ed/?utm_term=.df7ada49a043
[wi_stylometry]: https://en.wikipedia.org/wiki/Stylometry
[robert_article_1]: https://www.nytimes.com/2008/03/06/opinion/06lighthizer.html
[robert_article_2]: https://www.nytimes.com/2010/11/13/opinion/13lighthizer.html
[bm_results]: #results
[sage_email]: mailto:sage@bookmatch.com
[bm_twitter]: https://twitter.com/_bookmatch

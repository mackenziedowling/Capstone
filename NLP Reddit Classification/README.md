
![Project 3](https://git.generalassemb.ly/mkdowling/dsir-125/blob/master/Assignments/Projects/Project-Three/Images/CULTS%20vs.%20RELGION.png)



# Classifying R/Cults post vs. R/religion post



--- 


For this project the task is two-fold:
1. Using [Pushshift's](https://github.com/pushshift/api) API, collect posts from two subreddits.
2. Then use NLP to train a classifier on which subreddit a given post came from. This is a binary classification problem.

## Link to subreddits:
- **[r/cults](https://www.reddit.com/r/cults/)** 
- **[r/religion](https://www.reddit.com/r/religion/)**

---


## Background

The term cult has a long and controversial history. Originating as term used in the sociological study of religion the term has since developed in usage and meaning. Today in the english-speaking world the term cult has become a widely used and popular term. In popular culture it is typically used in a derogatory tone and seen in most scenarios as an ad hominem attack on groups with different practices and doctrines[source](https://www.jstor.org/stable/3511972?seq=1). 

With the rise of secular anti-cult movements in the 1970s scholars (though not the general public) began to abandon the use of the term *cult.* According to The Oxford Handbook of Religious Movements, "by the end of the decade, the term 'new religions' or ‘new religious movement’ would replace the term 'cult' to describe all of those leftover groups that did not fit easily under the label of church or sect with in the sociological study of religion. [source](https://en.wikipedia.org/wiki/Cult).

Today the term *new religion* replaces cult in sociology studies but many sociologist argue for the need to differentiate those groups that may be dangerous from those that are more benign. [source](#https://en.wikipedia.org/wiki/Cult) But this is not only an issue within the study of sociology. Today the issue is critical to human rights laws because limiting the definition of religion may interfere with freedom of religion, while too broad a definition may give some dangerous or abusive groups "a limitless excuse for avoiding all unwanted legal obligations.”[source](https://en.wikipedia.org/wiki/Cult).


## Problem Statment
As better deifintions for a dangerous cult and a new religious movement struggle to come to an official understanding, Our client, who perfers to be kept r/anonymous, has requested to know if a dangerous group can be differentiated from a more benign group through social media posts so they can identify the rise of a dangerous group prior to the health and wellbeing of indivudals is at risk. In order to accomplish this we will use reddit to collect posts under the two conflicting umbrella terms r/religion and r/cults and identify commonalities and differnces within vocabular and sentiment of each post. Through Natural Language processing and classification modeling our goal is determine how distinct these groups are and what type of language style and vocabulary helps to predict a post subreddit. 


## EDA Analysis Summary

The most frequently used words within each othese subreddit share many common words. Although we start too see more distinction in religion with terms related to religious practices and more colloquial terms used in the cults posts it is unclear if there is enough defining features in vocabulary to differentiate and predict accuratly the right post when modeling. 

![Common words](https://git.generalassemb.ly/mkdowling/dsir-125/blob/master/Assignments/Projects/Project-Three/Images/Common%20words.png)

![venndiagram](https://git.generalassemb.ly/mkdowling/dsir-125/blob/master/Assignments/Projects/Project-Three/Images/venndiagram.png)

When analyzing the sentiment of the two subreddits there is very little differece as majoirty were put into neutral. Religion has more positive and negative sentiment post than cults, this inconsistency leads me hypoithesis that sentiment might not be the best predictor for modeling.

![sentiment Analysis](https://git.generalassemb.ly/mkdowling/dsir-125/blob/master/Assignments/Projects/Project-Three/Images/sentimentAnalysis.png)

---

## Modeling
Below are is the performance on three different classifcation models used with two different text transformers. In terms of Accuracy Naïve Bayes Multinominal performed the best.

![cvec modelsg](https://git.generalassemb.ly/mkdowling/dsir-125/blob/master/Assignments/Projects/Project-Three/Images/cvecmodels.png)

![tvec models](https://git.generalassemb.ly/mkdowling/dsir-125/blob/master/Assignments/Projects/Project-Three/Images/tvecmodels.png)

## Best Performing Model Evaluation
A ROC Curve summarizes the trade-off between the true positive rate (tpr) and false positive rate (fpr) for a predictive model using different probability thresholds. Given that c is a constant known as decision threshold, Looking at the below ROC curve our blue curve is closer to the upper left corner than the 45 degree line that suggests that this model performed quite well in being able to differentiate the two groups of religion and cults. The ROC AUC score is 0.92 telling us the model has a 92% acurracy at predicting the positive class (religion).

![Roc Curve](https://git.generalassemb.ly/mkdowling/dsir-125/blob/master/Assignments/Projects/Project-Three/Images/RocCurve.png)



The ROC curce helps to view the relationship between specificty and sensitivey. For exmaple if we decrease the threshold, we will get more positive values thus it increases the sensitivity and decreasing the specificity. Similarly, when we increase the threshold, we get more negative values (cults) thus we get higher specificity and lower sensitivity.

In the below bar charts the top 10 features and their coeficients are plotted for each subreddit. The most important feature for religion is the term *god* and the most important term for cults is *join*. This is really interesting to me because as I found in my exploratory analysis there was this trend of language used within the r/cults thread that had this structure of *otherness* in terms of socail groups. We also see a lot of the top terms in r/cults are common words one would use to describe a social group from a club, organization etc. 

Another intersting aspect is the commonality these two groups have. Both of them have *people* as the 2nd top feature predictor and they also both include the words *think*. What is even more interesting is that the word *church* which commonly one would associate with religion is used as a top feature to predict cult. This could obviously could prove to be an issue if this model were to be expanded to furhter platforms or data. 

![Most Important Features_Coef](https://git.generalassemb.ly/mkdowling/dsir-125/blob/master/Assignments/Projects/Project-Three/Images/MostImportantFeatures_Coef.png)


## Conclusion Statement:
In order to develop better definintion's for what defines a religion vs a cult we looked to reddit threads to understand how the language and commmunications styles differ within popular culture. Identifying the difference in vocabulary, sentiment, and parts-of-speach within each of these subbreddit threads could lead to better understanding on the differences and commonalities of the two groups. With a better understanding of what terms are used in the discussion of these topics we can attempt to identify dangerous or destructive cults more quickly through natural language processing of comments, post, and discussion on social media and prevent outcomes that risk the health and wellbeing of people. 

Our modeling showed that while there are mamy similarities between the language/vocabulary used across the two groups that there are some defining words that make these two groups standout that can allow us to make a prediction with 0.84% accuracy. To develop this project further it would be worth analyzing post on specfic social media pages dedicated to a specific cult and religion and compare the sentiment, vocabulary, and part-of-speach. 


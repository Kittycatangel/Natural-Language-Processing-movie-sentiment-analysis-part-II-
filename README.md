# Natural-Language-Processing-movie-sentiment-analysis-part-II

# Data
The data used for training can be found in  Natural-Language-Processing-movie-sentiment-analysis-part-I repositority. The python cod efor this project can be found in this repository Natural-Language-Processing-movie-sentiment-analysis-part-II.

Let's see other options of optimizations for our movie sentiment analysis:

# Stop words
Another way that we can get rid of uninformative words is by discarding words that are too frequent to be informative. There are two main approaches: using a language-specific list of stopwords, or discarding words that appear too frequently. scikitlearn has a built-in list of English stopwords in the feature_extraction.text module.

# Rescaling the Data with tf–idf
Instead of dropping features that are deemed unimportant, another approach is to rescale features by how informative we expect them to be. One of the most common ways to do this is using the term frequency–inverse document frequency (tf–idf) method. The intuition of this method is to give high weight to any term that appears often in a particular document, but not in many documents in the corpus. If a word appears often in a particular document, but not in very many documents, it is likely to appear often in a particular document, but not in very many documents, it is likely to be very descriptive of the content of that document. scikit-learn implements the tf–idf method in two classes: TfidfTransformer, which takes in the sparse matrix output produced by CountVectorizer and transforms it, and TfidfVectorizer, which takes in the text data and does both the bag-of-words feature extraction and the tf–idf transformation.

# Investigating Model Coefficients

inally, let’s look in a bit more detail into what our logistic regression model actually learned from the data. Because there are so many features — 27,271 after removing the infrequent ones — we clearly cannot look at all of the coefficients at the same time. However, we can look at the largest coefficients, and see which words these correspond to. We will use the last model that we trained, based on the tf–idf features.

![image](https://user-images.githubusercontent.com/53411455/146652195-00632de3-46e3-4798-b504-14bb0386f422.png)

# Bag-of-Words with More Than One Word (n-Grams)
One of the main disadvantages of using a bag-of-words representation is that word order is completely discarded. Therefore, the two strings “it’s bad, not good at all” and “it’s good, not bad at all” have exactly the same representation, even though the meanings are inverted. Putting “not” in front of a word is only one example (if an extreme one) of how context matters. Fortunately, there is a way of capturing context when using a bag-of-words representation, by not only considering the counts of single tokens, but also the counts of pairs or triplets of tokens that appear next to each other. Pairs of tokens are known as bigrams, triplets of tokens are known as trigrams, and more generally sequences of tokens are known as n-grams. We can change the range of tokens that are considered as features by changing the ngram_range parameter of CountVectorizer or TfidfVectorizer. The ngram_range parameter is a tuple, consisting of the minimum length and the maximum length of the sequences of tokens that are considered.

 The TfidfVectorizer on the IMDb movie review data and find the best setting of n-gram range using a grid search: Best cross-validation score: 0.91
 
 To understand better how the model improved, we can visualize the important coefficient for the best model, which includes unigrams, bigrams, and trigrams.
 
 ![image](https://user-images.githubusercontent.com/53411455/146652345-4cd02eb2-fcb1-42be-afc6-6b4eed5887f1.png)

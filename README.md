# Natural-Language-Processing-movie-sentiment-analysis-part-II

Let's see other options of optimizations:

# Stop words
Another way that we can get rid of uninformative words is by discarding words that are too frequent to be informative. There are two main approaches: using a language-specific list of stopwords, or discarding words that appear too frequently. scikitlearn has a built-in list of English stopwords in the feature_extraction.text module.

# Rescaling the Data with tf–idf
Instead of dropping features that are deemed unimportant, another approach is to rescale features by how informative we expect them to be. One of the most common ways to do this is using the term frequency–inverse document frequency (tf–idf) method. The intuition of this method is to give high weight to any term that appears often in a particular document, but not in many documents in the corpus. If a word appears often in a particular document, but not in very many documents, it is likely to appear often in a particular document, but not in very many documents, it is likely to be very descriptive of the content of that document. scikit-learn implements the tf–idf method in two classes: TfidfTransformer, which takes in the sparse matrix output produced by CountVectorizer and transforms it, and TfidfVectorizer, which takes in the text data and does both the bag-of-words feature extraction and the tf–idf transformation.

# Investigating Model Coefficients

inally, let’s look in a bit more detail into what our logistic regression model actually learned from the data. Because there are so many features — 27,271 after removing the infrequent ones — we clearly cannot look at all of the coefficients at the same time. However, we can look at the largest coefficients, and see which words these correspond to. We will use the last model that we trained, based on the tf–idf features.

![image](https://user-images.githubusercontent.com/53411455/146652195-00632de3-46e3-4798-b504-14bb0386f422.png)


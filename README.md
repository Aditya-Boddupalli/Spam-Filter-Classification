# Spam Filter Classification

Here we are given huge dataset which contains Quora questions amd their repsonses whether they are span or not. The model we build must classify the quora questions as spam or not. The dataset shared is in below format.

![image](https://user-images.githubusercontent.com/31129705/57281267-467edc80-70c8-11e9-8669-2b062d99ef8a.png)


The shape of the dataset is (1306122, 3), so we have 1306122 rows. To bring down the dimensions, we can make us eof pre-trained embeddings such as glove or any other open source embeddings to make it easier. 

I build models with and without using glove. So, what exactly are word embeddings? What is Glove?

# Word embeddings

"Word embeddings" are a family of natural language processing techniques aiming at mapping semantic meaning into a geometric space. This is done by associating a numeric vector to every word in a dictionary, such that the distance (e.g. L2 distance or more commonly cosine distance) between any two vectors would capture part of the semantic relationship between the two associated words. The geometric space formed by these vectors is called an embedding space.

For instance, "coconut" and "polar bear" are words that are semantically quite different, so a reasonable embedding space would represent them as vectors that would be very far apart. But "kitchen" and "dinner" are related words, so they should be embedded close to each other.

Word embeddings are computed by applying dimensionality reduction techniques to datasets of co-occurence statistics between words in a corpus of text. This can be done via neural networks (the "word2vec" technique), or via matrix factorization.

# GloVe word embeddings

GloVe stands for "Global Vectors for Word Representation". It's a somewhat popular embedding technique based on factorizing a matrix of word co-occurence statistics. GloVe is an unsupervised learning algorithm for obtaining vector representations for words. Training is performed on aggregated global word-word co-occurrence statistics from a corpus, and the resulting representations showcase interesting linear substructures of the word vector space.

You can learn more about glove here https://nlp.stanford.edu/projects/glove/

I have used Common Crawl (840B tokens, 2.2M vocab, cased, 300d vectors, 2.03 GB download): glove.840B.300d.zip embedding. In NLP tokens refers to the total number of "words" in your corpus. The vocab is the number of unique "words".

# Pre processing data

I have build models with and without removing stopwords, special chatacters. If you want to bring down the dimesions you can cut down the stopwords, special characters as they do not have significant impact on model's performance.


# Types of Models

I have build various models for the project. They are as follows:

A. With removing stopwords and special characters:

1. Sequential model which has embedding layer with embedding matrix built using pre-trained glove.I have set trainable=false in the embedding layer, as we have already have weight matrix, so no need to update the weights during training.

Architecture : 

![image](https://user-images.githubusercontent.com/31129705/57294707-24945280-70e6-11e9-9afc-df801b13ef0f.png)

Performance :

![image](https://user-images.githubusercontent.com/31129705/57294758-4988c580-70e6-11e9-8a87-a4e26817eb71.png)

2. Sequential model which has embedding layer without using glove and without any weight matrix. The weights get updated during the training process.

Architecture: 

![image](https://user-images.githubusercontent.com/31129705/57294946-d92e7400-70e6-11e9-8f39-7d65ba2e4906.png)

Performance :

![image](https://user-images.githubusercontent.com/31129705/57294988-fbc08d00-70e6-11e9-8361-83312493bce9.png)



B. Without removing stopwords and special characters:

1. Without using pre-trained glove embeddings, this has huge corpus, hence it'll take a lot of time in training.

Architecture :

![image](https://user-images.githubusercontent.com/31129705/57295061-34f8fd00-70e7-11e9-9751-dfaf49917c21.png)

Performance :

![image](https://user-images.githubusercontent.com/31129705/57295109-5d80f700-70e7-11e9-8493-ee575f297057.png)

2. With using pre-trained embeddings.

Architecture :

![image](https://user-images.githubusercontent.com/31129705/57295175-928d4980-70e7-11e9-922d-3766420c71cb.png)

Performance :

![image](https://user-images.githubusercontent.com/31129705/57317018-bf0b8a80-7114-11e9-8af7-86dd69d94404.png)



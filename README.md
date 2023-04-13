# Text similarity measures

## Jaccard similarity
Jaccard similarity takes into account only the set of unique words for each text document if a term like “UHD” or “efficiency” is used multiple times in one product description and just once in another product description, the Euclidean distance and cosine similarity would drop. On the other hand, if the total number of unique words stays the same, the Jaccard similarity will remain unchanged.

## Euclidean distance
We use spaCy’s in-built Word2Vec model to create text embeddings. Euclidean distance doesn’t work well with the sparse vectors of text embeddings. So cosine similarity is generally preferred over Euclidean distance when working with text data

## Levenshtein distance
To measure this, we build a 2D matrix and track the cost or changes required by comparing both strings character by character. The distance reflects the total number of single-character edits required to transform one word into another. One use case is autocompletion

## Cosine similarity
Similarity of two vectors as the cosine of the angle between two vectors. It determines whether two vectors are pointing in roughly the same direction.
So if the angle between the vectors is 0 degrees, then the cosine similarity is 1. Cosine similarity is not affected by the magnitude/length of the feature vectors. 


# Word embeddings

## Bag of words (BOW)
In bag of words representation (also called count vectorizing), each word is represented by its count instead of 1. Regardless of that, both these approaches create huge, sparse vectors that capture absolutely no relational information

##TF-IDF 
TF-IDF vectors are an extension of the one-hot encoding model. Instead of considering the frequency of words in one document, the frequency of words across the whole corpus is taken into account. The big idea is that words that occur a lot everywhere carry very little meaning or significance. Although TF-IDF vectors offer a slight improvement over simple count vectorizing, they still have very high dimensionality and don’t capture semantic relationships.

##CBOW vs Skip-gram
CBOW is better at learning syntactic relationships between words while skip-gram is better at understanding the semantic relationships. In practical terms, this means that for a word like ‘dog’, CBOW would return morphologically similar words like plurals like 'dogs'. On the other hand, Skip-gram would consider morphologically different but semantically similar words like 'cat' or 'hamster'. As Skip-gram relies on single-word input it is less sensitive to overfitting frequent words. Because even if some words appear more times during the training they considered one at a time. CBOW is prone to overfit frequent words because they can appear several times in the same set of context words. This characteristic also allows Skip-gram to be more efficient in terms of amount of documents required to achieve good performance. Skip-gram works better when working with a small amount ofdata, focuses on semantic similarity of words, and represents rare words well. On the other hand, CBOW is faster, focuses more on the morphological similarity of words, and needs more data to achieve similar performance

##ELMO
ELMo computes the embeddings from the internal states of a two-layer bidirectional Language Model (LM), thus the name “ELMo”: Embeddings from Language Models. It assigns each word a representation that is a function of the entire corpus of sentences. ELMo embeddings are a function of all of the internal layers of the biLM. Different layers encode different kinds of information for the same word. For example, the lower levels work well for Part-Of-Speech tagging, while the higher levels are better at dealing with polysemous words. Concatenating the activations of all layers allows ELMo to combine a wide range of word representations that perform better on downstream tasks.ELMo works on the character level instead of words. This enables it to take advantage of sub-word units to derive meaningful embeddings for even out-of-vocabulary words


##SentenceBERT
Sentence-BERT (SBERT) is a modified BERT network that uses siamese and triplet network structures to derive semantically meaningful sentence embeddings. This reduces the effort for finding the most similar pair from 65 hours with BERT / RoBERTa to about 5 seconds with SBERT, while maintaining the accuracy from BERT

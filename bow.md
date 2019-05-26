# Bag Of Words
A bag-of-words model, or BoW for short, is a way of extracting features from text for use in modeling, such as with machine learning algorithms.

A bag-of-words is a representation of text that describes the occurrence of words within a document. It involves two things:

    1. A vocabulary of known words.
    2. A measure of the presence of known words.
    
# Example
The following models a text document using bag-of-words. Here are two simple text documents:

      (1) John likes to watch movies. Mary likes movies too.

      (2) John also likes to watch football games.
      
Based on these two text documents, a list constructed as follows for each document:

       "John","likes","to","watch","movies","Mary","likes","movies","too"

        "John","also","likes","to","watch","football","games"
       
       
Representing each bag-of-words as a JSON object, and attributing to the respective Javascript variable:


        BoW1 = {"John":1,"likes":2,"to":1,"watch":1,"movies":2,"Mary":1,"too":1};
        BoW2 = {"John":1,"also":1,"likes":1,"to":1,"watch":1,"football":1,"games":1};


Each key is the word, and each value is the number of occurrences of that word in the given text document. 

# Bag of Word for word embedding
In traditional way creating bag of word is so simple. 

We have a fixed vocabulary set V which contains

```
V = ['Good', 'Bad','Ugli','Beautiful']
```
So for creating word embedding using BOW we initialize a one hot vector(contains all zero except positional one) 
and it's `length = len(V)`

So

vector for good = [1 0 0 0] 

Vector for Bad = [0 1 0 0]

---------------- and so on.

Here vector size = length of vocabulary set

and 1 for position. 

# Create Bag of Word corpus using gensim

```python
import gensim
from gensim import corpora
from gensim.models import simple_preprocess
from pprint imoprt pprint
# List with 2 sentences
my_docs = ["Who let the dogs out?",
           "Who? Who? Who? Who?"]

# Tokenize the docs
tokenized_list = [simple_preprocess(doc) for doc in my_docs]

# Create the Corpus
mydict = corpora.Dictionary()
mycorpus = [mydict.doc2bow(doc, allow_update=True) for doc in tokenized_list]
pprint(mycorpus)
#> [[(0, 1), (1, 1), (2, 1), (3, 1), (4, 1)], [(4, 4)]]
```

## References
1. [https://en.wikipedia.org/wiki/Bag-of-words_model](https://en.wikipedia.org/wiki/Bag-of-words_model)
2. [https://machinelearningmastery.com/gentle-introduction-bag-words-model/](https://machinelearningmastery.com/gentle-introduction-bag-words-model/)
3. [https://towardsdatascience.com/word-embedding-with-word2vec-and-fasttext-a209c1d3e12c](https://towardsdatascience.com/word-embedding-with-word2vec-and-fasttext-a209c1d3e12c)

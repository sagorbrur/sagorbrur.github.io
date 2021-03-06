# N-Gram
An n-gram is a contiguous sequence of n items from a given sample of text or speech. The items can be phonemes, syllables, letters, words or base pairs according to the application.
The n-grams typically are collected from a text or speech corpus. When the items are words, n-grams may also be called shingles.

- An n-gram of size 1 is referred to as a "unigram"; 
- An n-gram of size 2 is a "bigram" (or, less commonly, a "digram"); 
- An n-gram of size 3 is a "trigram". 

## N-Gram as feature
A combination of N words together are called N-Grams. N grams (N > 1) are generally more informative as compared to words (Unigrams) as features. Also, bigrams (N = 2) are considered as the most important features of all the others. The following code generates bigram of a text.

```python
def generate_ngrams(text, n):
    words = text.split()
    output = []  
    for i in range(len(words)-n+1):
        output.append(words[i:i+n])
    return output

>>> generate_ngrams('this is a sample text', 2)
# [['this', 'is'], ['is', 'a'], ['a', 'sample'], , ['sample', 'text']]

```

# Generating N-Gram in NLTK
```python
import re
from nltk.util import ngrams
s='Hi, My Name is Sagor.'
s = s.lower()
s = re.sub(r'[^a-zA-Z0-9\s]', ' ', s)
tokens = [token for token in s.split(" ") if token != ""]
output = list(ngrams(tokens, 5))
print(output)

#>[('Hi,', 'My', 'Name', 'is', 'Sagor.')]

#change 5 into 1, 2 or 3 and watch the output


```



## References
1. [https://en.wikipedia.org/wiki/N-gram](https://en.wikipedia.org/wiki/N-gram)
2. [https://www.analyticsvidhya.com/blog/2017/01/ultimate-guide-to-understand-implement-natural-language-processing-codes-in-python/](https://www.analyticsvidhya.com/blog/2017/01/ultimate-guide-to-understand-implement-natural-language-processing-codes-in-python/)
3. [http://www.albertauyeung.com/post/generating-ngrams-python/](http://www.albertauyeung.com/post/generating-ngrams-python/)

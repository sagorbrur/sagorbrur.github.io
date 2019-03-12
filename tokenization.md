# Tokenization
**Tokenization** is the process of breaking up the given text into units called tokens. The tokens may be words or number or punctuation mark. Tokenization does this task by locating word boundaries. Ending point of a word and beginning of the next word is called word boundaries. Tokenization is also known as word segmentation. 


**More Specificly:**
Given a character sequence and a defined document unit, tokenization is the task of chopping it up into pieces, called tokens , perhaps at the same time throwing away certain characters, such as punctuation.

For example:

```
The quick brown fox jumps over the lazy dog
```

After Tokenization we will get the output:

```
Output: [The] [quick] [brown] [fox] [jumps] [over] [the] [lazy] [dog]

```

# Word Tokenization in NLTK

```python
from nltk.tokenize import sent_tokenize, word_tokenize
 
data = "All work and no play makes jack a dull boy, all work and no play"
print(word_tokenize(data))
#output: ['All', 'work', 'and', 'no', 'play', 'makes', 'jack', 'dull', 'boy', ',', 'all', 'work', 'and', 'no', 'play']
```


## References
- [http://language.worldofcomputing.net/category/tokenization](http://language.worldofcomputing.net/category/tokenization)
- [https://en.wikipedia.org/wiki/Lexical_analysis#Tokenization](https://en.wikipedia.org/wiki/Lexical_analysis#Tokenization)
- [https://nlp.stanford.edu/IR-book/html/htmledition/tokenization-1.html](https://nlp.stanford.edu/IR-book/html/htmledition/tokenization-1.html)
- [https://pythonspot.com/tokenizing-words-and-sentences-with-nltk/](https://pythonspot.com/tokenizing-words-and-sentences-with-nltk/)

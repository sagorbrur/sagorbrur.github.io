---
title: "Process Large Corpora Using Python Generator"
date: 2021-05-01
categories:
  - python
classes: wide
excerpt: This blog describe how to process large corpora using python generator
---

Suppose you have a large text corpora and you can't process that large file in your small RAM computer.

Here is a solution for processing large corpora using `python generator`

```py
class CorpusProcessing:
    def __init__(self, data_path):
        self.data_path = data_path

    def __iter__(self):
        for line in open(self.data_path):
            # do your process here
            # here I am doing white space tokenization
            tokens = line.split()
            yield tokens

process = CorpusProcessing('large_copora.txt')
for tokens in process:
    print(tokens)
```

## References
- [python generator wiki](https://wiki.python.org/moin/Generators)
- [python generator by realpython](https://realpython.com/introduction-to-python-generators/)
- [gensim example](https://radimrehurek.com/gensim/auto_examples/tutorials/run_word2vec.html#training-your-own-model)

## Thanks TO
- [Faruk Ahmad](https://github.com/faruk-ahmad) vai for forcefully helping me learning python generator 

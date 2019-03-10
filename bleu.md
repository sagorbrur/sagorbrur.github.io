# BLEU(Bilingual Evaluation Understudy)

The Bilingual Evaluation Understudy Score, or BLEU for short, is a metric for evaluating a generated sentence to a reference sentence.

# Calculate BLEU Scores

The Python Natural Language Toolkit library, or NLTK, provides an implementation of the BLEU score that you can use to evaluate your generated text against a reference.

```python
from nltk.translate.bleu_score import sentence_bleu
reference = [['this', 'is', 'a', 'test'], ['this', 'is' 'test']]
candidate = ['this', 'is', 'a', 'test']
score = sentence_bleu(reference, candidate)
print(score)
```


## References
1. [https://en.wikipedia.org/wiki/BLEU](https://en.wikipedia.org/wiki/BLEU)
2. [https://machinelearningmastery.com/calculate-bleu-score-for-text-python/](https://machinelearningmastery.com/calculate-bleu-score-for-text-python/)
3. [http://www.aclweb.org/anthology/P02-1040.pdf](http://www.aclweb.org/anthology/P02-1040.pdf)

# ROUGE (Recall-Oriented Understudy for Gisting Evaluation)

ROUGE, or Recall-Oriented Understudy for Gisting Evaluation, is a set of metrics and a software package used for evaluating automatic summarization and machine translation software in natural language processing. The metrics compare an automatically produced summary or translation against a reference or a set of references (human-produced) summary or translation.

# Mertices
The following five evaluation metrics are available. 

* ROUGE-N: Overlap of N-grams between the system and reference summaries. 
  * ROUGE-1 refers to the overlap of 1-gram (each word) between the system and reference summaries.
  * ROUGE-2 refers to the overlap of bigrams between the system and reference summaries.
* ROUGE-L: Longest Common Subsequence (LCS) based statistics. Longest common subsequence problem takes into account sentence level structure similarity naturally and identifies longest co-occurring in sequence n-grams automatically.
* ROUGE-W: Weighted LCS-based statistics that favors consecutive LCSes .
* ROUGE-S: Skip-bigram[5] based co-occurrence statistics. Skip-bigram is any pair of words in their sentence order.
* ROUGE-SU: Skip-bigram plus unigram-based co-occurrence statistics.


## References
1. https://en.wikipedia.org/wiki/ROUGE_(metric)
2. http://www.aclweb.org/anthology/W04-1013

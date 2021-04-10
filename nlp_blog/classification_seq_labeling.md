# Text Classification and Sequence Labeling in NLP
In this blog I am describing a short note about what is text classificaiton and sequence labeling in NLP.

## Text Classification
Text classification measns classify a sentence with it's corresponding label.

In short:
```
Given a sentence X and predict an output Y
```
### Type of Text Classification
- __Topic Classification__

  Topic classification predict a topic from an input sentence or text
  
  For example:
  
  Topic classifcation predict a topic(like food, sports, music) from an input sentence or text
  
  For Example:
  ```
  I like pizza -> food
  I like Ariana Grande -> music
  ------------------------
  ```
  
- __Sentiment Analysis__If we provide a topic list `[food, music, sports]` then classification work like this

  Sentiment analysis predict a sentiment (like positive, negative or neutral) from an input sentence or text
  
  For example:
  ```
  I like this picture -> positive
  I hate this picture -> negative
  
  ```
- __Language Identification__

  Language identification predict a language type(like English, Bangla.....) from an input sentence or text
  
  For Example:
  ```
  She live in Dhaka -> English
  সে ঢাকায় বাস করে -> Bangla
  ```
- __Hate Speech Detection__

  Hate speech detection detect hateness (like political, religious, personal, race....) from an input sentence or text
  
  For example:
  ```
  He is ugly -> personal
  ```
and there are so many classification problem arround here

## Sequence Labeling 
Sequnce labeling means generate a sequence of label from an input sentence

In short:
```
Given an input sentence X and generate sequence of label Y of equal length
```
### Type of Sequence Labling
- __Part of Speech Tagging__
  
  Part of speech tagging problem generate different `part of speech tag` from an input sentence
  
  For example:
  ```
  I eat rice -> PRON VERB NOUN 
  ```
- __Lemmatization__

  Lemmatization predict different `lemma` from an input sentence
  
  For example:
  ```
  He ate rice -> He eat rice
  ```
- __Language Identification__

  Language identification predict different language type from an input sentence
  
  For example:
  ```
  ami tomake love kori -> BN BN EN BN
  ```
and there are more sequence tagging problem around here

### Span Labeling as Sequence Labeling
Span labeling kind of sequence labeling but instead of labeling sequence it's label span by speical kind of sequence label

- __Name Entity Recognition__

  Name entity recogtion predict different name entity(like PERSON, LOCATION) from an input sentence
  
  For Example:
  ```
  Sagor Sarker love to visit Rangpur -> B-PER I-PER O O O S-LOC -> (Sagor Sarker)-> PERSON, Rangpur->LOCATION
  
  ```
  you can find different type of name entity tagging format [here](https://en.wikipedia.org/wiki/Inside%E2%80%93outside%E2%80%93beginning_(tagging))
  
  More example for other type sequence labeling:
  
  __semantic role labeling__
  ```
  Sagor Sarker is living in Dhaka, Bangladesh -> (Sagor Sarker)-> Actor, living->Predicate, (Dhaka, Bangladesh)->Location
  ```
  __syntactic chunking__
  ```
  Sagor Sarker is living in Dhaka -> (Sagor Sarker)->NP, (is living)-> VP, (in Dhaka)->NP
  ```
  
## References
- [http://demo.clab.cs.cmu.edu/11737fa20/slides/multiling-04-seqlabeling.pdf](http://demo.clab.cs.cmu.edu/11737fa20/slides/multiling-04-seqlabeling.pdf)
- [http://speech.ee.ntu.edu.tw/~tlkagk/courses/MLDS_2015_2/Lecture/Sequence%20(v4).pdf](http://speech.ee.ntu.edu.tw/~tlkagk/courses/MLDS_2015_2/Lecture/Sequence%20(v4).pdf)
- [https://cs230.stanford.edu/blog/namedentity/](https://cs230.stanford.edu/blog/namedentity/)
- [https://guillaumegenthial.github.io/sequence-tagging-with-tensorflow.html](https://guillaumegenthial.github.io/sequence-tagging-with-tensorflow.html)

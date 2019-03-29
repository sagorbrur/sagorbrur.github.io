# METEOR (Metric for Evaluation of Translation with Explicit ORdering)
METEOR  is a metric for the evaluation of machine translation output. The metric is based on the harmonic mean of unigram precision and recall, with recall weighted higher than precision. 

Meteor consists of two major components:
`a flexible monolingual word aligner` and `a scorer`


## Example 

![a](METEOR-alignment-a.png)

![b](METEOR-alignment-b.png)


From the two alignments shown, alignment (a) would be selected at this point. Stages are run consecutively and each stage only adds to the alignment those unigrams which have not been matched in previous stages.


 ## Code Example 
 [This](https://github.com/tylin/coco-caption/tree/master/pycocoevalcap/meteor) is the link for calculating meteor value. 
 Clone this and run ```meteor.py```
 
 









## References
1. [https://en.wikipedia.org/wiki/METEOR](https://en.wikipedia.org/wiki/METEOR)
2. [https://medium.com/explorations-in-language-and-learning/metrics-for-nlg-evaluation-c89b6a781054](https://medium.com/explorations-in-language-and-learning/metrics-for-nlg-evaluation-c89b6a781054)
3. [https://www.cs.cmu.edu/~alavie/METEOR/README.html](https://www.cs.cmu.edu/~alavie/METEOR/README.html)

---
title: "Different F1 score for sequence tagging"
date: 2022-05-18
categories:
  - nlp
  - metrics
  - sequence-labelling
classes: wide
excerpt: This blog post explains different F1 score used in sequence tagging.
---

![](/images/sequence_tag_f1.png)

F1 score is the most common evaluation metric for sequence tagging. It is the harmonic mean of precision and recall. But more often we see that there different variant of F1 score use in sequence tagging or sequence labeling task. Like

- Micro F1 score
- Macro F1 score
- Weighted F1 score

In this blog post, I will what these F1 score is and how to calculate them.

## Micro F1 score

In micro F1 score, we need to sum up all class true positive(TP), false positive(FP), false negative(FN) and calculate the global F1 score.

Suppose we have three classes A, B, C. 

| Class | TP | FP | FN |
|------:|:---:|:---:|:---:|
| A     | 10  | 5  | 0  |
| B     | 5   | 10 | 0  |
| C     | 0   | 0  | 10 |
| Total | 15  | 10 | 10 |

So, the micro F1 calculation equation is:

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(micro)=\frac{2TP}{2TP+FP+FN})

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(micro)=\frac{30}{30+10+10}=0.6)

## Macro F1 score
Suppose we have three classes, A, B, C. To calculate the macro F1 score, we need to calculate the F1 score for each class and then average them.

| Class | Per-class F1 score |
|------:|:------------------:|
| A     | 0.8                |
| B     | 0.5                |
| C     | 0.7                |

So macro calculation equation is: ,

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(macro)=\frac{A+B+C}{3})

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(macro)=\frac{0.8+0.5+0.7}{3}=0.66)


## Weighted F1 score
Weighted F1 score depends on two parameters

- Each class F1 score
- __Support__ of each class

__Support__: Support is the number of actual occurrences of the class in the datasets. The support value for A is 10 means that there are only 10 A label in the dataset.


| Class | Per-class F1 score | Support | Support Percentage |
|------:|:------------------:|:-------:|:-----------------:|
| A     | 0.8                | 3      | 0.3 (3/total support)                |
| B     | 0.5                | 1       | 0.1                |
| C     | 0.7                | 6      | 0.6                |
|Total | -                | 10      | -                |

So, weighted F1 calculation equation is:

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(weighted)={A}\times{0.3}+{B}\times{0.1}+{C}\times{0.6}=0.66)

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(weighted)={0.8}\times{0.3}+{0.5}\times{0.1}+{0.7}\times{0.6}=0.71)



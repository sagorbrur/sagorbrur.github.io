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

F1 score is the most common evaluation metric for sequence tagging. It is the harmonic mean of precision and recall. But more often we see that there are different variants of the F1 score used in sequence tagging or sequence labeling tasks. Like

- Micro F1 score
- Macro F1 score
- Weighted F1 score

In this blog post, I will explain what these F1 score is and how to calculate them.

## Micro F1 score

In micro F1 score, we need to sum up all class true positive(TP), false positive(FP), and false negative(FN) and calculate the global F1 score.

Suppose we have three classes A, B, and C. 

| Class | TP | FP | FN |
|------:|:---:|:---:|:---:|
| A     | 10  | 0  | 0  |
| B     | 5   | 10 | 0  |
| C     | 0   | 0  | 10 |
| Total | 15  | 10 | 10 |

So, the micro F1 calculation equation is:

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(micro)=\frac{2TP}{2TP+FP+FN})


![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(micro)=\frac{30}{30+10+10}=0.6)

## Macro F1 score
Suppose we have three classes, A, B, and C. To calculate the macro F1 score, we need to calculate the F1 score for each class and then average them.

| Class | Per-class F1 score |
|------:|:------------------:|
| A     | 0.8                |
| B     | 0.5                |
| C     | 0.7                |

So macro calculation equation is: ,

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(macro)=\frac{A+B+C}{3})

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(macro)=\frac{0.8+0.5+0.7}{3}=0.66)


## Weighted F1 score
The weighted F1 score depends on two parameters

- Each class F1 score
- __Support__ of each class

__Support__: Support is the number of actual occurrences of the class in the datasets. The support value for A is 10 means that there are only 10 A labels in the dataset.


| Class | Per-class F1 score | Support | Support Percentage |
|------:|:------------------:|:-------:|:-----------------:|
| A     | 0.8                | 3      | 0.3 (3/total support)                |
| B     | 0.5                | 1       | 0.1                |
| C     | 0.7                | 6      | 0.6                |
|Total | -                | 10      | -                |

So, the weighted F1 calculation equation is:

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(weighted)={A}\times{0.3}+{B}\times{0.1}+{C}\times{0.6})

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;F1(weighted)={0.8}\times{0.3}+{0.5}\times{0.1}+{0.7}\times{0.6}=0.71)


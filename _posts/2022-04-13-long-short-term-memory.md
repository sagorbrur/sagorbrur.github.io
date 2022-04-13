---
title: "Understanding LSTM(Long Short Term Memory)"
date: 2022-04-13
categories:
  - nlp
  - dl
classes: wide
excerpt: This blog describes about the concept of LSTM
---
Due to the vanishing gradient problem in RNN for long sequence, where some information is lost in each time step increasing the sequence length, we need to use a technique called Long Short Term Memory(LSTM). 

LSTM contains three gate:
- Forget gate
- Input gate
- Output gate

__Forget gate__ controls(by f(t)) which parts of the long-term state should be erased.
__Input gate__ controls(by i(t)) which parts of the long-term state should be added
__Output gate__ controls(by o(t)) which parts of the long-term state should be read and output at this time step.

LSTM is exact as RNN but it's state is split in two vectors: h(t) and c(t) where h(t) is short-term state and c(t) is long-term state.

As long-term state `c(t-1)` traverses the netwrok from left to right. It first goes through forget gate, dropping some memories, and then it goes through input gate, adding new memories. The result `c(t)` goest straight out.

The long-term state c(t) copied and pass through `tanh` function and result filtered by output gate.

![](/images/lstm.png)
<!-- <center> Fig: LSTM(source: HOML book)</cneter> -->


The input vector x(t) and prevous short-term state h(t-1) are fed to four different fully connected layers.

Here's all the equations for every gates:

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;i_{t}=sigmoid(W_{xi}x_{t}+W_{hi}h_{t-1}+b_{i})))

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;f_{t}=sigmoid(W_{xf}x_{t}+W_{hf}h_{t-1}+b_{f})))

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;o_{t}=sigmoid(W_{xo}x_{t}+W_{ho}h_{t-1}+b_{o})))

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;g_{t}=tanh(W_{xg}x_{t}+W_{hg}h_{t-1}+b_{g})))

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;c_{t}=f_{t}c_{t-1}+i_{t}g_{t})

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;h_{t}=o_{t}tanh(c_{t}))


## References
- [Hands on machine learning by scikit-learn and keras by geron]()
- [https://colah.github.io/posts/2015-08-Understanding-LSTMs/](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)

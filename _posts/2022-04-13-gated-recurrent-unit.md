---
title: "Understanding GRU(Gated Recurrent Unit)"
date: 2022-04-13
categories:
  - nlp
  - dl
classes: wide
excerpt: This blog describes about the concept of GRU
---

GRU is the simplified version of [LSTM](https://sagorbrur.github.io/2022/04/long-short-term-memory/) and performs as well as LSTM. GRU has less parameters than LSTM and is faster than LSTM.
Both state vectors are merged into one sinlge vector h(t) in GRU.

A single gate controller z(t) controls both forget and input gate.
If the gate controller outputs 1, the forget gate is open(=1) and the input gate is closed(1-1=0). If it's output is 0, the opposite happens. In other word whenever a memory must be stored, the location where it will be stored is erased first. 
![](/images/gru.png)
<!-- <center> Fig: LSTM(source: HOML book)</cneter> -->

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;z_{t}=sigmoid(W_{xz}^Tx_{t}+W_{hz}^Th_{t-1}+b_{z}))

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;r_{t}=sigmoid(W_{xr}^Tx_{t}+W_{hr}^Th_{t-1}+b_{r}))

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;h_{t}=r_{t}h_{t-1}+z_{t}g_{t})

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;g_{t}=tanh(W_{xg}^Tx_{t}+W_{hg}^Th_{t-1}+b_{g}))


## References
- [Hands on machine learning by scikit-learn and keras by geron]()


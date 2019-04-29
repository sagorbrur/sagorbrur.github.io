# A Gentle Intro of Recurrent Neural Network(RNN)

Input: A sequence of vector

Output: A fixed size probability vector


A Simple RNN: 

```
y = RNN()
y = rnn.step(x)
```

A Two layer RNN:

```
y1 = rnn(x)
y2 = rnn(y1)


```

# Most popular activation functions

Non-linearity is one of the most important part for deep neural network. without activation function resulting network is equivalent to single-layer-network. Below there are four most popular activation functions are described.

## Sigmoid
Sigmoid activation function maps the output into range [0, 1]

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;y=sigmoid(z)=\frac{1}{1+e^{-z}})

```py
import math

z = [0.6, 1.1, -1.5, 1.2, 3.2, -1.1]
sigmoid_act = [1/(1+math.exp(-i)) for i in z]
print(sigmoid_act)
```

## Tanh
Tanh activation function maps the output ranges from -1 to 1

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;y=\frac{e^{z}-e^{-z}}{e^{z}+e^{-z}})

```py
import math

z = [0.6, 1.1, -1.5, 1.2, 3.2, -1.1]
tanh_act = [(math.exp(i)-math.exp(-i))/(math.exp(i)+math.exp(-i)) for i in z]
print(tanh_act)
```

## ReLU
Rectified Linear Unit(ReLU) maps the output into 0 to z

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;y=max(z,0))

```py
z = [0.6, 1.1, -1.5, 1.2, 3.2, -1.1]

relu_act = [i if i>0 else 0 for i in z]
print(relu_act)
```

## Softmax
Softmax maps output into a probability distribution.

![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;y=\frac{e^{z_{i}}}{\sum_{j}e^{z_{j}})

```py
import math

z = [0.6, 1.1, -1.5, 1.2, 3.2, -1.1]
sum_of_exp_z = sum([math.exp(i) for i in z])
softmax = [(math.exp(i)/sum_of_exp_z) for i in z]
print(softmax)
```

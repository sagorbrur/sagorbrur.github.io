
# Creating a Bi-LSTM model in Tensorflow

We will create a simple Bi-LSTM model in tensorflow to demonestrate
how bi-lstm model work

## Steps:

* Text Preprocessing
* Building Model
* Training 
* Prediction



```python
# import tensorflow 
import tensorflow as tf
import numpy as np

tf.reset_default_graph()
```

    C:\Users\Sagor Sarker\Anaconda3\lib\site-packages\h5py\__init__.py:36: FutureWarning: Conversion of the second argument of issubdtype from `float` to `np.floating` is deprecated. In future, it will be treated as `np.float64 == np.dtype(float).type`.
      from ._conv import register_converters as _register_converters
    

# Text Preprocessing(Normalization)


```python
# example data

sentences = ("He is going to Dhaka", "She lives in Rangpur", "We love our country")
```


```python
# tokenize sentences
word_seq = " ".join(sentences).split()
print(word_seq)
# remove duplicate words
word_list = list(set(word_list))
print(word_list)
```

    ['He', 'is', 'going', 'to', 'Dhaka', 'She', 'lives', 'in', 'Rangpur', 'We', 'love', 'our', 'country']
    ['Rangpur', 'our', 'country', 'She', 'We', 'to', 'going', 'is', 'lives', 'love', 'Dhaka', 'He', 'in']
    


```python
# create word2id
word_dict = {w: i for i, w in enumerate(word_list)}
print(word_dict)
# create id2word
number_dict = {i: w for i, w in enumerate(word_list)}
print(number_dict)
```

    {'Rangpur': 0, 'our': 1, 'country': 2, 'She': 3, 'We': 4, 'to': 5, 'going': 6, 'is': 7, 'lives': 8, 'love': 9, 'Dhaka': 10, 'He': 11, 'in': 12}
    {0: 'Rangpur', 1: 'our', 2: 'country', 3: 'She', 4: 'We', 5: 'to', 6: 'going', 7: 'is', 8: 'lives', 9: 'love', 10: 'Dhaka', 11: 'He', 12: 'in'}
    


```python
n_class = len(word_dict)
print(n_class)
n_step = len(word_list)
print(n_step)
```

    13
    13
    


```python
# make batch input for lstm from sentence data
def make_batch_debug(sentence):
    input_batch = []
    target_batch = []
    
    words = word_seq
    for i, word in enumerate(words[:-1]):
        print('input words: ')
        print(words[:(i+1)])
        input = [word_dict[n] for n in words[:(i+1)]]
        print(input)
        input = input+[0]*(n_step-len(input))
        print(input)
        print('target word: ', words[i+1])
        target = word_dict[words[i+1]]
        print(target)
        
        # to check input_batch and target_batch 
        # uncomment print
        input_batch.append(np.eye(n_class)[input])
#         print(input_batch)
        target_batch.append(np.eye(n_class)[target])
#         print('target array is: ')
#         print(target_batch)
#         return input_batch, target_batch
make_batch_debug(sentences)        
```

    input words: 
    ['He']
    [11]
    [11, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    target word:  is
    7
    input words: 
    ['He', 'is']
    [11, 7]
    [11, 7, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    target word:  going
    6
    input words: 
    ['He', 'is', 'going']
    [11, 7, 6]
    [11, 7, 6, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    target word:  to
    5
    input words: 
    ['He', 'is', 'going', 'to']
    [11, 7, 6, 5]
    [11, 7, 6, 5, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    target word:  Dhaka
    10
    input words: 
    ['He', 'is', 'going', 'to', 'Dhaka']
    [11, 7, 6, 5, 10]
    [11, 7, 6, 5, 10, 0, 0, 0, 0, 0, 0, 0, 0]
    target word:  She
    3
    input words: 
    ['He', 'is', 'going', 'to', 'Dhaka', 'She']
    [11, 7, 6, 5, 10, 3]
    [11, 7, 6, 5, 10, 3, 0, 0, 0, 0, 0, 0, 0]
    target word:  lives
    8
    input words: 
    ['He', 'is', 'going', 'to', 'Dhaka', 'She', 'lives']
    [11, 7, 6, 5, 10, 3, 8]
    [11, 7, 6, 5, 10, 3, 8, 0, 0, 0, 0, 0, 0]
    target word:  in
    12
    input words: 
    ['He', 'is', 'going', 'to', 'Dhaka', 'She', 'lives', 'in']
    [11, 7, 6, 5, 10, 3, 8, 12]
    [11, 7, 6, 5, 10, 3, 8, 12, 0, 0, 0, 0, 0]
    target word:  Rangpur
    0
    input words: 
    ['He', 'is', 'going', 'to', 'Dhaka', 'She', 'lives', 'in', 'Rangpur']
    [11, 7, 6, 5, 10, 3, 8, 12, 0]
    [11, 7, 6, 5, 10, 3, 8, 12, 0, 0, 0, 0, 0]
    target word:  We
    4
    input words: 
    ['He', 'is', 'going', 'to', 'Dhaka', 'She', 'lives', 'in', 'Rangpur', 'We']
    [11, 7, 6, 5, 10, 3, 8, 12, 0, 4]
    [11, 7, 6, 5, 10, 3, 8, 12, 0, 4, 0, 0, 0]
    target word:  love
    9
    input words: 
    ['He', 'is', 'going', 'to', 'Dhaka', 'She', 'lives', 'in', 'Rangpur', 'We', 'love']
    [11, 7, 6, 5, 10, 3, 8, 12, 0, 4, 9]
    [11, 7, 6, 5, 10, 3, 8, 12, 0, 4, 9, 0, 0]
    target word:  our
    1
    input words: 
    ['He', 'is', 'going', 'to', 'Dhaka', 'She', 'lives', 'in', 'Rangpur', 'We', 'love', 'our']
    [11, 7, 6, 5, 10, 3, 8, 12, 0, 4, 9, 1]
    [11, 7, 6, 5, 10, 3, 8, 12, 0, 4, 9, 1, 0]
    target word:  country
    2
    


```python
# make batch input for lstm from sentence data
def make_batch(sentence):
    input_batch = []
    target_batch = []
    
    words = word_seq
    for i, word in enumerate(words[:-1]):
        input = [word_dict[n] for n in words[:(i+1)]]
        input = input+[0]*(n_step-len(input))
        target = word_dict[words[i+1]]
        input_batch.append(np.eye(n_class)[input])
        target_batch.append(np.eye(n_class)[target])
        return input_batch, target_batch        
```

# Building Bi-LSTM Model


```python
# creating Bi-LSTM model

X = tf.placeholder(tf.float32, [None, n_step, n_class])
Y = tf.placeholder(tf.float32, [None, n_class])
print(X.shape)
print(Y.shape)

```

    (?, 13, 13)
    (?, 13)
    


```python
# random weight and bias
n_hidden = 5
W = tf.Variable(tf.random_normal([n_hidden*2, n_class]))
print(W)
b = tf.Variable(tf.random_normal([n_class]))
print(b)
```

    <tf.Variable 'Variable_4:0' shape=(10, 13) dtype=float32_ref>
    <tf.Variable 'Variable_5:0' shape=(13,) dtype=float32_ref>
    


```python
# creating lstm cell
lstm_fw_cell = tf.nn.rnn_cell.LSTMCell(n_hidden) # forward lstm
lstm_bw_cell = tf.nn.rnn_cell.LSTMCell(n_hidden) # backward lstm

# outputs
outputs, _ = tf.nn.bidirectional_dynamic_rnn(lstm_fw_cell, lstm_bw_cell, X, dtype=tf.float32)

```


```python
outputs = tf.concat([outputs[0], outputs[1]], 2) # outputs[0]=lstm_fw, outputs[1]=lstm_bw
outputs = tf.transpose(outputs, [1, 0, 2]) # [n_step, batch_size, n_hidden]
outputs = outputs[-1] # [batch_size, n_hidden]

```


```python
model = tf.matmul(outputs, W) + b
```


```python
cost = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits_v2(logits=model, labels=Y))
optimizer = tf.train.AdamOptimizer(0.001).minimize(cost)

```


```python
prediction = tf.cast(tf.argmax(model, 1), tf.int32)
```

# Training


```python
# training
init = tf.global_variables_initializer()
sess = tf.Session()
sess.run(init)

input_batch, target_batch = make_batch(sentence)

for epoch in range(10000):
    _, loss = sess.run([optimizer, cost], feed_dict={X: input_batch, Y: target_batch})
    if (epoch + 1)%1000 == 0:
        print('Epoch:', '%04d' % (epoch + 1), 'cost =', '{:.6f}'.format(loss))

```

    Epoch: 1000 cost = 0.006196
    Epoch: 2000 cost = 0.001835
    Epoch: 3000 cost = 0.000830
    Epoch: 4000 cost = 0.000432
    Epoch: 5000 cost = 0.000240
    Epoch: 6000 cost = 0.000137
    Epoch: 7000 cost = 0.000080
    Epoch: 8000 cost = 0.000047
    Epoch: 9000 cost = 0.000028
    Epoch: 10000 cost = 0.000016
    

# Prediction


```python
# prediction
predict = sess.run([prediction], feed_dict={X: input_batch})
print(sentences)
print([number_dict[n] for n in [pre for pre in predict[0]]])
```

    ('He is going to Dhaka', 'She lives in Rangpur', 'We love our country')
    ['is']
    

# References
* [nlp-tutorial](https://github.com/graykode/nlp-tutorial)

# Sequence to Sequence Model
Sequence to Sequence model is a neural model which takes a sequence of input and produce a sequence of output. 
## Sequence to Sequence model has two part.
* Encoder
* Decoder


![seq2seq](http://i64.tinypic.com/30136te.png)



The task of an encoder network is to understand the input sequence, and create a smaller dimensional representation of it. This representation is then forwarded to a decoder network which generates a sequence of its own that represents the output. Let’s take an example of a conversational agent to understand the concept.

In the image given above, the input sequence is “How are you”. So when such an input sequence is passed though the encoder-decoder network consisting of LSTM blocks (a type of RNN architecture), the decoder generates words one by one in each time step of the decoder’s iteration. After one whole iteration, the output sequence generated is “I am fine”.

[Seq2seq Keras Implementation](https://github.com/keras-team/keras/blob/master/examples/lstm_seq2seq.py)

## References
1. [https://www.analyticsvidhya.com/blog/2018/03/essentials-of-deep-learning-sequence-to-sequence-modelling-with-attention-part-i/](https://www.analyticsvidhya.com/blog/2018/03/essentials-of-deep-learning-sequence-to-sequence-modelling-with-attention-part-i/)

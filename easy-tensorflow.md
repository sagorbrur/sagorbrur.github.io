# Easy Tensorflow

We will implement a simple equation ```h = ReLu(Wx+b)```

## Import Tensorflow and other necessaries
```python
import os
import tensorflow as tf
import numpy as np
tf.reset_default_graph()

```


## create the input placeholder
```python
x = tf.placeholder(tf.float32, shape=[None, 784], name='X')
```

## Create weight matrix initialized randomely from N(0, 0.01)
```python
weight_initer = tf.truncated_normal_initializer(mean=0.0, stddev=0.01)
W = tf.get_variable(name="Weight", dtype=tf.float32, shape=[784, 200], initializer=weight_initer)
```
## Create bias vector of size 200, all initialized as zero
```python
bias_initer =tf.constant(0., shape=[200], dtype=tf.float32)
b = tf.get_variable(name="Bias", dtype=tf.float32, initializer=bias_initer)

```
## Creating model, Saving model and visualize using tensorboard
```python
# create matmul node
x_w = tf.matmul(x, W, name='MatMul')
#create add node
x_w_b = tf.add(x_w, b, name='Adding')
#create ReLu node
h = tf.nn.relu(x_w_b, name='ReLu')

# Add an Op to initialize variables
init_op = tf.global_variables_initializer()

## tensorboard coding start

# A scalar summary for the scalar tensor
scalar_summary = tf.summary.scalar('My_scalar_summary', x)
# A histogram summary for the non-scalar (i.e. 2D or matrix) tensor
histogram_summary = tf.summary.histogram('My_histogram_summary', x_w_b)

# ____step 2:____ merge all summaries
merged = tf.summary.merge_all()
## tensorboard coding end here
# launch the graph in a session
with tf.Session() as sess:
    # initialize variables
    sess.run(init_op)
    # create the dictionary:
    d = {x: np.random.rand(100, 784)}
    # feed it to placeholder a via the dict 
    print(sess.run(h, feed_dict=d))
    
    #saving for tensorboard
    # to visualize run : tensorboard --logdir=graphs --port=6006
    writer = tf.summary.FileWriter('./graphs', sess.graph)
    
    #for saving the model
    saver = tf.train.Saver()
    saved_path = saver.save(sess, 'train/'+'./saved_variable')
    print('model saved in {}'.format(saved_path))
    
    ## Restore the model
    # restore the saved vairable
    saver.restore(sess, 'train/'+'./saved_variable')
    # print the loaded variable
    W_out, b_out = sess.run([W, b])
    print('W = ', W_out)
    print('b = ', b_out)
    
    # import the graph from the file
    imported_graph = tf.train.import_meta_graph('train/saved_variable.meta')

    # list all the tensors in the graph
    for tensor in tf.get_default_graph().get_operations():
        print (tensor.name)
```
Now Run the code as
```test.py```
and also run the following code to visualize
```tensorboard --logdir=graph_path```

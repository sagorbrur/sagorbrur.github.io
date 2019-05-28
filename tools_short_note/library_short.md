# This page provides short note about different library functions

## Using GPU memory Fraction in Tensorflow

```py
config = tf.ConfigProto()
config.gpu_options.per_process_gpu_memory_fraction = 0.4
session = tf.Session(config=config, ...)
```

This will set 40% gpu memory for your model. Such as, if you have 6GB GPU memory and you set `per_process_gpu_memory_fraction=0.5`, It
will set 3GB GPU memory for your model.

## Keras Callback

Keras Callback is a set of function provides you for training model.

### ModelCheckpoint

Using this callback you can save your trained checkpoints

```py
from keras.callbacks import ModelCheckpoint
checkpoints = ModelCheckpoint(filepath, monitor='val_loss', verbose=0, save_best_only=False, 
save_weights_only=False, mode='auto', period=1)

```

Now you call it from  `model.fit` as:

```py
model.fit(x_train, y_train,
          batch_size=batch_size,
          epochs=epochs,
          validation_data=(x_test, y_test), callbacks=[checkpoints])
```

### Tensorboard

Using this callback you can visualize your model graph through tensorboard

```py
from keras.callbacks import TensorBoard
tensorboard = TensorBoard(log_dir='./logs', histogram_freq=0, 
                 batch_size=32, write_graph=True, write_grads=False, write_images=True, 
                     embeddings_freq=0, embeddings_layer_names=None,
                      embeddings_metadata=None, embeddings_data=None, update_freq='epoch')
```

Now you call it from  `model.fit` as:

```py
model.fit(x_train, y_train,
          batch_size=batch_size,
          epochs=epochs,
          validation_data=(x_test, y_test), callbacks=[tensorboard])
```

### EarlyStopping

Using this callback your training will stopped while the accuracy is stucked. 

```py
from keras.callbacks import EarlyStopping
early_stopped = EarlyStopping(monitor='val_loss', min_delta=0, patience=0, 
                 verbose=0, mode='auto', baseline=None, restore_best_weights=False)
```
Now you call it from  `model.fit` as:

```py
model.fit(x_train, y_train,
          batch_size=batch_size,
          epochs=epochs,
          validation_data=(x_test, y_test), callbacks=[early_stopped])
```

You can call multiple callbacks just like

```py
model.fit(x_train, y_train,
          batch_size=batch_size,
          epochs=epochs,
          validation_data=(x_test, y_test), callbacks=[checkpoints, tensorboard, early_stopped])
```

## References
1. [https://keras.io/callbacks/](https://keras.io/callbacks/)
2. [https://medium.com/singlestone/keras-callbacks-monitor-and-improve-your-deep-learning-205a8a27e91c](https://medium.com/singlestone/keras-callbacks-monitor-and-improve-your-deep-learning-205a8a27e91c)

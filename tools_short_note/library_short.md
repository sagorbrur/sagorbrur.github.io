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

### ModelCheckpoint

```py
from keras.callbacks import ModelCheckpoint
checkpoints = ModelCheckpoint(filepath, monitor='val_loss', verbose=0, save_best_only=False, save_weights_only=False, mode='auto', period=1)

```

Now you call it from  `model.fit` as:

```py
model.fit(x_train, y_train,
          batch_size=batch_size,
          epochs=epochs,
          validation_data=(x_test, y_test), callbacks=[checkpoints])
```


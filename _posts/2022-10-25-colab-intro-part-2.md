---
title: "Colab Introduciton part-2"
date: 2022-10-25
categories:
  - colab
  - msc
classes: wide
excerpt: Colab basic use cases and helpers
---

## Starting Colab
1.   Create a google account (Gmail account)
2.   Go to https://colab.research.google.com
3.   Sign in with your google account
4.   Start using colaboratory

## Colaborary Machine Details
1. It's a linux-baesd operating system machine
2. It's CPU is Intel(R) Xeon(R) CPU @ 2.20GHz
    
    To check CPU info run the below command in colab
    ```python
    !cat /proc/cpuinfo
    ```
3. Total RAM 13GB

    To check RAM info run the below command in Colab

    ```python
    !cat /proc/meminfo
    ```
4. Total disk space 108GB
5. It has Tesla T4 16GB GPU memory
    
    To check GPU fist switch the colab machine to GPU by __Edit>Notebook Settings__ and select GPU from Hardware accelerator dropdown
    ```python
    !nvidia-smi -L
    ```
    ```python
    !nvidia-smi
    ```
6. It has google TPU v2 with 8GB memory per core


## Colab is a Linux Machine
Colab is a linux-based machine. You can run any linux-based command here.


```python
# check files and directories in current directory
!ls
```

    sample_data



```python
!ls -a
```

    .  ..  .config	sample_data



```python
%cd sample_data/
```

    /content/sample_data



```python
!ls
```

    anscombe.json		      mnist_test.csv
    california_housing_test.csv   mnist_train_small.csv
    california_housing_train.csv  README.md



```python
%cd ..
```

    /content



```python
!mkdir hello
```


```python
%cd hello
!touch test.py

```

    /content/hello



```python
# edit the script
# then run
!python test.py
```

    hello world!



```python
%cd ..
```

    /content



```python
## install any third party linux software
!apt install docker.io
```

```python
!docker --version
```

    Docker version 20.10.7, build 20.10.7-0ubuntu5~18.04.3



```python
# download a file from online
!wget https://huggingface.co/sagorsarker/bangla-glove-vectors/resolve/main/bn_glove.100d.zip
```

```python
# unzip the file
!unzip bn_glove.100d.zip
```

    Archive:  bn_glove.100d.zip
      inflating: bn_glove.100d.txt       



```python
# remove the file
!rm -rf bn_glove.100d.zip
!rm -rf bn_glove.100d.txt
```


```python
!cat hello/test.py
```

    print("hello world!")


```python
!cp hello/test.py ./
```


```python
!mv test.py sample_data
```


```python
!df -h
```

    Filesystem      Size  Used Avail Use% Mounted on
    overlay         108G   38G   71G  35% /
    tmpfs            64M     0   64M   0% /dev
    shm             5.8G     0  5.8G   0% /dev/shm
    /dev/root       2.0G  1.1G  910M  54% /sbin/docker-init
    tmpfs           6.4G   28K  6.4G   1% /var/colab
    /dev/sda1        55G   39G   17G  71% /etc/hosts
    tmpfs           6.4G     0  6.4G   0% /proc/acpi
    tmpfs           6.4G     0  6.4G   0% /proc/scsi
    tmpfs           6.4G     0  6.4G   0% /sys/firmware



```python
!du -sh
```

    55M	.



```python
!pwd
```

    /content

## Colab contains build in virtual environment


```python
# install any python package using pip
!pip install tqdm
```

    Looking in indexes: https://pypi.org/simple, https://us-python.pkg.dev/colab-wheels/public/simple/
    Requirement already satisfied: tqdm in /usr/local/lib/python3.7/dist-packages (4.64.1)



```python
from tqdm import tqdm

for i in tqdm(range(100)):
  pass
```

    100%|██████████| 100/100 [00:00<00:00, 57621.98it/s]



```python
# download google drive file using gdown
!pip install gdown
```

```python
import gdown
url = "https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ"
output = "fcn8s_from_caffe.npz"
gdown.download(url, output, quiet=False)
```

    Downloading...
    From: https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ
    To: /content/fcn8s_from_caffe.npz
    100%|██████████| 499M/499M [00:02<00:00, 227MB/s]





    'fcn8s_from_caffe.npz'



## Special Options


```python
# install or run any module without showing the log
%%capture
!pip install scikit-learn
```


```python
# write any file using the magic command
%%writefile hello.py
print("hello world!")
```

    Writing hello.py



```python
# check time while running any command or code
%%time
print('hello')
```

    hello
    CPU times: user 1.84 ms, sys: 0 ns, total: 1.84 ms
    Wall time: 1.78 ms


## Pre-installed well known libraries


```python
import tensorflow as tf
tf.__version__
```




    '2.8.2'




```python
import torch
torch.__version__
```




    '1.12.1+cu113'




```python
import sklearn
sklearn.__version__
```




    '1.0.2'


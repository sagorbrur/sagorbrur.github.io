---
title: "Multiprocessing using concurrent in python"
date: 2024-01-10
categories:
  - python
  - large file processing
classes: wide
excerpt: In this blog I will share how to do multiprocessing using concurrent in python
---

Multiprocessing is an essential need to process long list or lage chunks of data. In this post I will share a simple python program to do the multiprocessing for tokenizing chunks of list of data.

## Steps
1. Import necessaries

```py
import os
import glob
import concurrent
from tqdm import tqdm
from concurrent.futures import ThreadPoolExecutor

```

2. Create your specific function to do your task. In my case I have created a file tokenizer to read the file and return tokens

```py
def file_tokenization(file):
    with open(file) as f:
      text = f.read()
      return text.split()
```

3. Inside `main` function get the `cpu count` using os library

```py
cpu_count = os.cpu_count()
```

4. Create a threadpool using concurrent library and pass your function as iterator with input argument. Also add `tqdm` to show the progress.

```py
# Using ThreadPoolExecutor for parallel downloads
with ThreadPoolExecutor(max_workers=cpu_count) as executor:
    futures = [executor.submit(file_tokenization, file) for file in files]

    # Using tqdm to display progress
    for future in tqdm(concurrent.futures.as_completed(futures), total=len(futures)):
        print(future.result())
```


## Full Source Code

```py

import os
import glob
import concurrent
from tqdm import tqdm
from concurrent.futures import ThreadPoolExecutor


def file_tokenization(file):
    with open(file) as f:
      text = f.read()
      return text.split()

def main():
    files = glob.glob('sample_data/*')

    # Get CPU count for parallelism
    cpu_count = os.cpu_count()

    # Using ThreadPoolExecutor for parallel downloads
    with ThreadPoolExecutor(max_workers=cpu_count) as executor:
        futures = [executor.submit(file_tokenization, file) for file in files]

        # Using tqdm to display progress
        for future in tqdm(concurrent.futures.as_completed(futures), total=len(futures)):
            print(future.result())

if __name__ == "__main__":
    main()

```
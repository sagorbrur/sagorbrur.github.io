---
title: "Multiprocessing example in python over pandas dataframe"
date: 2024-01-11
categories:
  - python
classes: wide
excerpt: In this blog I will share how to do simple multiprocessing in python over pandas dataframe
---

Multiprocessing is an essential need to process long list or lage chunks of data. In this post I will share a simple python program to do the multiprocessing for a pandas dataframe rows processing.

```py
import multiprocessing
import pandas as pd
from tqdm import tqdm

def process(row):
    # do your process over the row
    return process_data


def main():
    df = pd.read_csv('mydata.csv')
    data_to_process = df.to_dict('records')
    pool = multiprocessing.Pool(processes=multiprocessing.cpu_count())
    for result in tqdm(pool.imap_unordered(process, data_to_process), total=len(data_to_process)):
        print(result)

if __name__ == "__main__":
    main()

```
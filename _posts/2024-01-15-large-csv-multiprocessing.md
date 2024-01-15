---
title: "Large CSV file multiprocessing"
date: 2024-01-15
categories:
  - python
  - large file processing
classes: wide
excerpt: In this blog I will share how to do multiprocessing on large CSV file with iterator
---

Processing large CSV/TSV file pandas is kind of heavy task. Instead of pandas we can simply use python builtin `csv` reader to iterate over the row. Let's assure we have a csv file with header and 10 rows. Let's dig down the code.


```py
import csv
import itertools
import multiprocessing
from tqdm import tqdm
from functools import partial

def process_row(row, header):
    # your processing here.
    return processed_data

def main():
    csv_path = "mypath/mycsv.csv"

    pool = multiprocessing.Pool(processes=multiprocessing.cpu_count())

     with open(csv_path, 'r') as file:
        csvreader = csv.reader(file)
        # separate the header first
        header = next(csvreader)

        # to get the total row numbers copy the iterator and check len on copy
        # it will keep your original iterator in intial index
        csvreader_copy, csvreader_original = itertools.tee(csvreader, 2)
        total_rows = len(list(csvreader_copy))

        partial_process_row = partial(process_row, header=header)

        # map your multiprocessing pool over the iterator and see progress bar by tqdm
        for result in tqdm(pool.imap_unordered(partial_process_row, csvreader_original), total=total_rows):
            print(result)

```

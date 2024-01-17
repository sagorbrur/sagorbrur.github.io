---
title: "Process large CSV file using pandas"
date: 2024-01-17
categories:
  - python
  - pandas
  - large file processing
classes: wide
excerpt: In this blog I will share how to process large CSV file using pandas
---

Working with large datasets in Python can be a challenging task, especially when dealing with CSV files that don't fit into memory. Thankfully, the Pandas library provides an efficient way to handle large CSV files by reading them in chunks. In this blog post, we'll explore how to load large CSV files using Pandas, along with a practical example code.

## Why Chunking Matters?
Loading an entire large CSV file into memory can be memory-intensive and slow. Pandas' chunking mechanism allows you to read and process the data in manageable pieces, making it more memory-efficient and responsive. This is particularly useful when working with datasets that are too large to fit into RAM.

## Example Code: Loading Large CSV Files in Chunks
Here is an example of chunking a large CSV file.


```py
import os
import pandas as pd
from tqdm import tqdm

def chunk_csv(input_file, chunk_size, output_path="output"):
    file_number = 1

    # Read the large CSV file in chunks
    for chunk in tqdm(pd.read_csv(input_file, chunksize=chunk_size)):
        # Define the chunk file name
        chunk_file_name = os.path.join(output_path, f'chunk_{file_number}.csv')
        
        # Process the chunk as needed (in this example, we save each chunk to a separate CSV file)
        chunk.to_csv(chunk_file_name, index=False)
        
        file_number += 1

# example to run the function
chunk_csv('my_large_csv', 20000, output_path="mypath")
```


## References
- Help taken from [chatGPT](https://chat.openai.com/)
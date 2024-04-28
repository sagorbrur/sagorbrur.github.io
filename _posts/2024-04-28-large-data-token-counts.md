---
title: "Large text data token counting fast"
date: 2024-04-28
categories:
  - python
  - datasets
  - large file processing
classes: wide
excerpt: In this blog I will share codes to count tokens from large dataset fast.
---


## Codes
```py
import glob
import json
import multiprocessing
from tqdm import tqdm
from transformers import AutoTokenizer

model_id = "tokenzer_model"

tokenizer = AutoTokenizer.from_pretrained(model_id, trust_remote_code=True)

def token_num(file):
    file_tokens = 0
    for line in open(file):
        data = json.loads(line)
        text = data['text']
        tokens = tokenizer.tokenize(text)
        file_tokens += len(tokens)
    print(f"file tokens: {file_tokens}")
    return file_tokens

files = glob.glob('/data2/mybndatasets/splited_data/train/*.jsonl')
print(len(files))

total_tokens = 0

with multiprocessing.Pool(processes=multiprocessing.cpu_count()) as pool:
        for tokens in tqdm(pool.imap(token_num, files), total=len(files)):
              total_tokens += tokens

print(f"total tokens: {total_tokens}")

```



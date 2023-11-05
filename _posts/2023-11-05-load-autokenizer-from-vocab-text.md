---
title: "How to load vocab.txt file using huggingface transformers AutoTokenizer"
date: 2023-11-05
categories:
  - tokenizer
  - huggingface
  - transformers
classes: wide
excerpt: In this blog I will provide a simple tips to load vocab.txt file using hugginface AutoTokenizer
---

## Steps
- Download a save already exist pretrained tokenizer which contains `vocab.txt`. In our case we will download `sagorsarker/bangla-bert-base` 

    ```py
    from transformers import AutoTokenizer

    bnbert_tokenizer = AutoTokenizer.from_pretrained("sagorsarker/bangla-bert-base")
    text = "আমি বাংলায় গান গাই।"
    bnbert_tokenizer.tokenize(text)
    # ['আমি', 'বাংলা', '##য', 'গান', 'গাই', '।']
    # save the tokenizer by the following line
    tokenizer.save_pretrained('bangla-bert-base')
    # remember the folder bangla-bert-base must created before saving
    ```

- Create your own folder and copy `special_tokens_map.json` and `tokenizer_config.json` there. Also keep your `vocab.txt` file there.
- Open `tokenizer_config.json` file and check if special token index match with `vocab.txt` special token index. If not note the token index and update index in `tokenizer_config.json`
- Now load your tokenizer folder using AutoTokenizer.from_pretrained()

    ```py
    from transformers import AutoTokenizer

    bnbert_tokenizer = AutoTokenizer.from_pretrained("mytokenizer")
    text = "আমি বাংলায় গান গাই।"
    bnbert_tokenizer.tokenize(text)
    ```
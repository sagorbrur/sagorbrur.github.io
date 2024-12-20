---
title: "bntranslit package for Bengali transliteration"
date: 2021-05-31
categories:
  - nlp
  - transliteration
  - tools
classes: wide
excerpt: This blog post explains how to use bntranslit package for Bengali transliteration.
---

[BNTRANSLIT](https://github.com/sagorbrur/bntranslit) is a deep learning based transliteration app for Bangla word.

## Installation
```
pip install bntranslit
```

## Dependency
- pytorch 1.7.0 or 1.7.0+

NB: No GPU Needed. Totally CPU based

## Pre-trained Model
- Download bntranslit_model from [here](https://github.com/sagorbrur/bntranslit/raw/master/model/bntranslit_model.pth)

## Usage
```py
from bntranslit import BNTransliteration

model_path = "bntranslit_model.pth"
bntrans = BNTransliteration(model_path)

word = "aami"
output = bntrans.predict(word, topk=10)
# output: ['আমি', 'আমী', 'অ্যামি', 'আমিই', 'এমি', 'আমির', 'আমিদ', 'আমই', 'আমে', 'আমিতে']
```

## Datasets and Training Details
- We used [Google Dakshina Dataset](https://github.com/google-research-datasets/dakshina)
- Thanks to [AI4Bharat](https://github.com/AI4Bharat/IndianNLP-Transliteration) for providing training notebook with details explanation
- We trained Google Bangla Dakshina lexicons train datasets for 10 epochs with batch size 128, 1e-3, embedding dim = 300, hidden dim = 512, lstm, used attention
- We evaluated our trained model with Google Bangla Dakshina lexicon test data using [AI4Bharat evaluation script](https://raw.githubusercontent.com/AI4Bharat/IndianNLP-Transliteration/jgeob-dev/tools/accuracy_reporter/accuracy_news.py) and our evaluation results insides docs/evaluation_summary.txt

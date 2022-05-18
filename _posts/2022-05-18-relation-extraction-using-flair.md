---
title: "Relation Extraction Training with Flair"
date: 2022-05-18
categories:
  - nlp
  - relation-extraction
  - tools
classes: wide
excerpt: This blog post explains how to train relation extraction model with Flair.
---

Training a Relation Extraction model in [Flair](https://github.com/flairNLP/flair) is kind of a very easy task. A few days back I was doing relation extraction with flair. But unfortunately there no exact code to train the model. So, I prepare the relation extraction training code by myself by observing flair [NER training](https://github.com/flairNLP/flair/blob/master/resources/docs/TUTORIAL_7_TRAINING_A_MODEL.md#training-a-named-entity-recognition-ner-model-with-flair-embeddings) training code.

## Data Preparation
We will train a relation extraction model for [CONLL04](https://github.com/bekou/multihead_joint_entity_relation_extraction/tree/master/data/CoNLL04) datasets. So, first we need to prepare our data in CONLL04 format.

Here is an example of __CONLL04__ format:

```
# global.columns = id form ner
    # text = Shaka khan loves to read book.
    # sentence_id = 1
    # relations = 6;6;1;2;HOBBY
    1	Shaka	B-PER
    2	Khan	I-PER
    3	loves	O
    4	to	O
    5	read	O
    6   book	B-OBJ

    # text = Rita loves to swim.
    # sentence_id = 2
    # relations = 4;4;1;1;HOBBY
    1	Rita	B-PER
    2	loves	O
    3	to	O
    4   swim	B-SPORT

    ................................
```

- Prepare three file in same name as below

    - conll04-train.conllu
    - conll04-dev.conllu
    - conll04-test.conllu

- Keep these files in below directory format

    ```bash
    - data
        - re_english_conll04
            - conll04-train.conllu
            - conll04-valid.conllu
            - conll04-test.conllu
    ```

## Training
Training code is straight forward.

```py
from flair.datasets import RE_ENGLISH_CONLL04
from flair.embeddings import WordEmbeddings, StackedEmbeddings, FlairEmbeddings
from flair.models import RelationExtractor
from flair.trainers import ModelTrainer

data_path = "data"
# load corpus
corpus = RE_ENGLISH_CONLL04(data_path)
print(corpus)
# prepare label dictionary
label_dict = corpus.make_label_dictionary("relation")
print(label_dict)

# initialize embeddings
# if you have other embeddings, you can add below list also or replce
embedding_types = [
    # comment in these lines to use flair embeddings
    WordEmbeddings("glove"),
    FlairEmbeddings('news-forward'),
    FlairEmbeddings('news-backward'),
]

embeddings = StackedEmbeddings(embeddings=embedding_types)

extractor = RelationExtractor(embeddings=embeddings, 
                                entity_label_type="ner", 
                                label_dictionary=label_dict, 
                                label_type="relation")

trainer = ModelTrainer(extractor, corpus)

# start training
trainer.train("log_path",
            learning_rate=0.1,
            mini_batch_size=32,
            max_epochs=150)

```

For predicting relation you need an NER model too. 

Let's discuss it in another blog post.


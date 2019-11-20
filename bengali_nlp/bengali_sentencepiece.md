# Bengali Sentencepiece

[git with model](https://github.com/sagorbrur/bengali_sentencepiece)

## What is [SentencePiece](https://github.com/google/sentencepiece)?
SentencePiece is an unsupervised text tokenizer and detokenizer mainly for Neural Network-based text generation systems where the vocabulary size is predetermined prior to the neural model training. SentencePiece implements subword units (e.g., byte-pair-encoding (BPE) [Sennrich et al.]) and unigram language model [Kudo.]) with the extension of direct training from raw sentences. SentencePiece allows us to make a purely end-to-end system that does not depend on language-specific pre/postprocessing.

## What we did?
We trained **sentencepiece** model with bengali wiki data and saved our bengali sentencepiece model. 

## Steps

* sentencepiece installation

```pip install sentencepiece```

* preprocess wiki data

We download bengali wiki dump data and extract using [bengali_wikiextractor](https://github.com/sagorbrur/bn_wikiextractor).

We preprocess bengali wiki data into a text file with **single sentence** per line. 

 - data format

```
sentence 1
sentence 2
..........
sentence n
```

* Sentencepiece Training

```py
import sentencepiece as spm

spm.SentencePieceTrainer.train('--model_prefix=bn_spm --input=data/bn_wiki.txt --vocab_size=50000')

```

it will save `bn_spm.model` and `bn_spm.vocab` in your train directory.

* Testing bengali sentencepiece model

```py
import sentencepiece as spm
sp = spm.SentencePieceProcessor()
sp.Load("bn_spm.model")

# output: True
```

```py
sp.EncodeAsPieces("আমি বাংলায় গান গাই।")

# output: ['▁আমি', '▁বাংলায়', '▁গান', '▁গাই', '।']
```

```py
sp.EncodeAsIds("আমি বাংলায় গান গাই।")
# output: [914, 1852, 349, 6229, 3]
```

```py
sp.DecodePieces(['▁আমি', '▁বাংলায়', '▁গান', '▁গাই', '।'])
# output: 'আমি বাংলায় গান গাই।'

```

```py
sp.NBestEncodeAsPieces("আমি বাংলায় গান গাই।", 5)
"""
output:
[['▁আমি', '▁বাংলায়', '▁গান', '▁গাই', '।'],
 ['▁আমি', '▁বাংলা', 'য়', '▁গান', '▁গাই', '।'],
 ['▁আমি', '▁বাংলায়', '▁গান', '▁গা', 'ই', '।'],
 ['▁আমি', '▁বাংলায়', '▁গান', '▁', 'গাই', '।'],
 ['▁', 'আমি', '▁বাংলায়', '▁গান', '▁গাই', '।']]

"""

```

```py
sp.DecodeIds([914, 1852, 349, 6229, 3])

# output: 'আমি বাংলায় গান গাই।'

```

```py
sp.GetPieceSize()
# output: 50000 as our vocab size is 50000
# same as len(sp)

```





